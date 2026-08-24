# Cribl Pack Generator — shared goldens

Verified pipeline definitions ("goldens") used by the Cribl Pack Generator app. Each
file holds the Cribl functions, the recipe that produced them, and the quality score
the pipeline achieved when it was verified against a real sample.

This repository is **public so that every installation of the app can read it without
credentials**, in both run modes (inside the Cribl UI and standalone). Reads go over
`raw.githubusercontent.com`; nothing here requires authentication.

## Layout

```
shared-goldens/
  index.json                     manifest: one entry per golden (key, score, author, path)
  <sourcetype>__<format>.json    one golden per file
```

A key is `<sourcetype>::<dest_format>`; on disk `::` becomes `__`.

## Writing

Publishing is done by the app running outside the Cribl UI, with a GitHub token that has
`Contents: Read and write` on this repository. Publishing is first-writer-wins: an
existing key is only overwritten by a strictly higher score.

## Contents

These files describe log formats — regular expressions, field mappings, timestamp
handling and scores. They contain no customer data and no sample events.
