---
title: "sound locked up by ------ deluge???"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by bitterbug on 2008-01-18
For a while I've been having intermittent loss of sound, and for the life of me couldn't figure out why, until someone posted this handy command:

```
lsof | grep pcm
```

What it revealed to me was that Deluge, of all things, was keeping the audio device open.
I haven't even seen an option in Deluge for sound notifications, so this strikes me as quite strange.

Anyone else had the same problem?

---

