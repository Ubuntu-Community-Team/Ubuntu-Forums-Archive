---
title: "[SOLVED] mounting ext3 partitions in OSX"
date: 2007-10-19
forum: Apple Intel Users
---

### Post by Monsoonx27 on 2007-10-19
I have a new Macbook Pro the 15inch dual booted with Gutsy which works well, a couple of kinks which I am ironing out.

Although Gutsy will be my main OS I want to be able to mount my external in OS X, it is formated at ext3 and has 500gb of data on it so formating to another file system is out of the question.

I have read and tried some of the tutorials around for doing this but the ext2 program they use only work with PPC macs and this is an intel.


Any ideas would be very helpful.

---

### Post by cyberdork33 on 2007-10-19
> **Monsoonx27 said:**
> I have a new Macbook Pro the 15inch dual booted with Gutsy which works well, a couple of kinks which I am ironing out.

Although Gutsy will be my main OS I want to be able to mount my external in OS X, it is formated at ext3 and has 500gb of data on it so formating to another file system is out of the question.

I have read and tried some of the tutorials around for doing this but the ext2 program they use only work with PPC macs and this is an intel.


Any ideas would be very helpful.
There is an ext2/3 app for intel macs. You must have a different version.

---

### Post by ajtudor on 2007-10-19
> **Monsoonx27 said:**
> I have a new Macbook Pro the 15inch dual booted with Gutsy which works well, a couple of kinks which I am ironing out.

Although Gutsy will be my main OS I want to be able to mount my external in OS X, it is formated at ext3 and has 500gb of data on it so formating to another file system is out of the question.

I have read and tried some of the tutorials around for doing this but the ext2 program they use only work with PPC macs and this is an intel.


Any ideas would be very helpful.

You can try here: [http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/)

I use this one with the same setup you described.  It may be read only though... or at least that's how I use it.  The only difference between ext2 and ext3 is the journaling information... ie you can mount an ext3 as an ext2, but the journaling will be ignored.  Also, watch you permissions in the filesystem since the uid will most likely be different under OSX.

Hope that helps.

---

### Post by Monsoonx27 on 2007-10-20
> **ajtudor said:**
> You can try here: [http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/)

I use this one with the same setup you described.  It may be read only though... or at least that's how I use it.  The only difference between ext2 and ext3 is the journaling information... ie you can mount an ext3 as an ext2, but the journaling will be ignored.  Also, watch you permissions in the filesystem since the uid will most likely be different under OSX.

Hope that helps.

The sourceforge was the driver I had the problems with.

If their are so many how about another suggestion.

---

