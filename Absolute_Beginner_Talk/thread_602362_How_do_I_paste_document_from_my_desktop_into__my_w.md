---
title: "How do I paste document from my desktop into  my windows drives?"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by Cool Surfer on 2007-11-04
How do I paste document from my desktop into  my windows drives?
the paste option is not highlighted . Thanks

---

### Post by forestpixie on 2007-11-04
do you have read/write enabled for your ntfs drives - or are they fat
which version of ubuntu are you running - feisty needed [ntfs3g]("http://www.ntfs-3g.org/") - which you can get from the repos, but gutsy doesn't apparently

---

### Post by Cool Surfer on 2007-11-04
I have 
-
Ubuntu 7.04
                - the Feisty Fawn - released in April 2007.
-----------------------------------

Have installed NTFS configuration tool, enabled write permission, but still its not working.

---

### Post by forestpixie on 2007-11-04
you recently installed it - or you had it before and it's stopped working? 
If you recently installed have you rebooted?
can you drag it in nautilus?

---

### Post by Cool Surfer on 2007-11-04
I just installed this ubunty - Ubuntio Studio yesterday. Even ntfs tool i installed yesterday.

---

### Post by forestpixie on 2007-11-04
try adding ntfs-config in terminal

```
sudo apt-get install ntfs-config
```

is the drive mounted when you start - can you see it in nautilus - and can you drga the files in nautilus

---

### Post by taisao on 2007-11-04
here is a howto: 
[https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite](https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite)

---

