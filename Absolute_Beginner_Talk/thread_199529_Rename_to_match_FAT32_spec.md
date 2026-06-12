---
title: "Rename to match FAT32 spec?"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by Burke on 2006-06-18
Hey, is there a program or command I can use to rename (recursively) the contents of a directory to comply with the FAT32 spec?

Thanks

---

### Post by aysiu on 2006-06-18
How are they not complying? What's "the FAT32 spec"?

---

### Post by Burke on 2006-06-19
I guess what I mean is filenames that Windows can recognize (ie. none of those crazy characters like exclamation marks). 

I was copying a bunch of files to a FAT32 drive (from a reiser drive) and quite a few errored out because of odd punctuation in the filenames.

I fixed it myself, it just took longer than it should have (I renamed them manually). I'm wondering if anyone knows offhand of a program that can automatically rename files to be a little more platform-agnostic.

---

### Post by aysiu on 2006-06-19
It sounds like a character-encoding issue, not a file naming issue.

I've always mounted FAT32 with the parameter *iocharset=utf8* and had no problems between Windows and Ubuntu for those files.

---

### Post by Burke on 2006-06-19
Fair enough, I'll try that next time. Thanks.

---

### Post by aysiu on 2006-06-19
It may not work retroactively (on old files), but give it a try.

For the old files, you may need some kind of script or terminal command to recursively rename them.

KRename (see screenshot) can do bulk renaming, but I don't think it works recursively.

---

