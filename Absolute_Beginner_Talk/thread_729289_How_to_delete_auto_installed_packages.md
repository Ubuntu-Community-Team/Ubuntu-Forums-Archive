---
title: "How to delete auto installed packages?"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by garyed on 2008-03-19
I'm runnunimg Feisty & I tried to play a midi file that it didn't recognize so it ask me to allow it to get new packages & I said yes. Half way through the download I changed my mind & aborted.
Is there any way to know what if anything got downloaded or installed? Do the files actually  get downloaded to a directory or do they just get installed & the installation files never stay on the Hard Drive?  
I also have the Ubuntu studio repos installed so I wanted to go through them first before I installed anything else.

---

### Post by PeterJS on 2008-03-19
None of the packages start installing untill all of the packages in a set finish downloading, so you don't have to worry about uninstalling anything. Packages are downloaded to:
```

/var/cache/apt/archives/

```
pending install and are stored there for future reinstall. Having a few extra packages in the local cache shouldn't cause any harm, on the other hand you could clear the whole cache out if you wanted that extra couple hundred MB back.

---

### Post by garyed on 2008-03-20
Thanks that did the trick.

---

