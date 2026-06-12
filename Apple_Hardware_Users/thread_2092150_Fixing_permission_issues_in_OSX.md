---
title: "Fixing permission issues in OSX"
date: 2012-12-06
forum: Apple Hardware Users
---

### Post by skullmunky on 2012-12-06
I'm jotting down some notes for future reference as I work through fixing a bunch of file permission problems on my HFS+ partition.  These are files that I've created while in Ubuntu - I store a lot of my data on the HFS+ partition on my Macbook, and edit files from either OS depending on particular needs.  Most of the time this works flawlessly.  But once in a while I get a bunch of files that are fine in Ubuntu but in OSX are locked, unchangeable, undelete-able, and which I can't do anything with even after unlocking them in the Finder, using sudo, etc.


Aside from the basic UID/GID matchup tricks, OSX apparently has a whole bagful of secret ways to make files inaccessible.  These include ACL's, extended attributes, and "flags", all of which need different command line tools.

Flags:

to see flags:
```

ls -lO

```

Handy ref:
[http://mac101.net/content/tips-tricks/pc-to-mac-using-terminal-to-fix-multiple-locked-files-and-folders-at-once/#1]("http://mac101.net/content/tips-tricks/pc-to-mac-using-terminal-to-fix-multiple-locked-files-and-folders-at-once/#1")

examples:
```

chflags noopaque *file*
chflags nouappnd *file*

```

basically, if you see one listed, call chflags and add "no" before the flag name to remove it.

or just 

```

chflags -R 0 *

```
recursively set flags to 0 on all files and subdirectories. 

Extended Attributes:

this is garbage like com.apple.FinderInfo and the [URL="http://reviews.cnet.com/8301-13727_7-57374676-263/workarounds-for-quarantine-bug-in-os-x-lion/"]"quarantine" thing
[/URL]

list them:

```

ls -l@

```

kill it with fire:
```

xattr -d com.apple.FinderInfo *

```

supposedly -c will just clear them all, but on Snow Leopard I get invalid flag so have to do 'em all manually.

---

