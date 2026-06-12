---
title: "Filesystems under Ubuntu, using NTFS?"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by crystallinity on 2007-04-16
hello all,

i've been considering dual-booting with ubuntu, in hopes of completely switching over from windows at some point, but have been wondering how this would affect my files. i have a few questions about that - phrased from a windows user's perspective - so please try to be relatively accomodating to my ignorance! 

specifically, if i've got a windows xp storage drive (ntfs) that contains music (.mp3), movies (.avi), documents (.doc, pdf, txt), and such, can i expect these to be accessible under ubuntu?

i seem to remember reading that a package called ntfs-3g or something needed to be installed in order to write ntfs files in ubuntu. would i need to do anything out of the ordinary to access these files, which were all created under windows?

for example, can openoffice, under ubuntu, read openoffice (.odt) files that were created in windows? what about ms word (.doc) files created in windows?

what about firefox bookmarks - is there any way to import these?

finally, since i've got a pair of identical drives i use for backing up storage, is it possible (and would it make sense) to format one drive in ext3 (or whichever file system currently being used for ubuntu) and transfer everything from the NTFS formatted drive, having it re-written into the ext3 format on the other? or should i just continue using NTFS?

thanks for any help you can provide, and for having patience with my admittedly tedious questions :)

---

### Post by jdong on 2007-04-16
> **crystallinity said:**
> hello all,

i've been considering dual-booting with ubuntu, in hopes of completely switching over from windows at some point, but have been wondering how this would affect my files. i have a few questions about that - phrased from a windows user's perspective - so please try to be relatively accomodating to my ignorance! 

specifically, if i've got a windows xp storage drive (ntfs) that contains music (.mp3), movies (.avi), documents (.doc, pdf, txt), and such, can i expect these to be accessible under ubuntu?

i seem to remember reading that a package called ntfs-3g or something needed to be installed in order to write ntfs files in ubuntu. would i need to do anything out of the ordinary to access these files, which were all created under windows?

By default, your NTFS drives will be made available for **read-only** access in Ubuntu, requiring no additional effort on your part. However, if you would like to be about to write to, or delete files from, NTFS drives from Ubuntu, then you do need to install the ntfs-3g driver package, which is not difficult, but requires some work. (In Feisty, there is a program called ntfs-config that you can install which does this for you)

> 
for example, can openoffice, under ubuntu, read openoffice (.odt) files that were created in windows? what about ms word (.doc) files created in windows?

Ubuntu will be able to read Openoffice documents, and also work with Microsoft Office formats (doc, xls, ppt, etc). In most cases its compatibility is excellent , but in my experience there are still some interoperability problems if you have very complex .doc file layouts.

> 
what about firefox bookmarks - is there any way to import these?

Feisty Fawn's Migration Assistant in the installer will be able to import these. Feisty is set to release at the end of the week -- this may be a good reason to wait for Feisty's release!
> 
finally, since i've got a pair of identical drives i use for backing up storage, is it possible (and would it make sense) to format one drive in ext3 (or whichever file system currently being used for ubuntu) and transfer everything from the NTFS formatted drive, having it re-written into the ext3 format on the other? or should i just continue using NTFS?

thanks for any help you can provide, and for having patience with my admittedly tedious questions :)

You can either use ext3, NTFS, or FAT32 to share files with a Windows computer. 

If you just need to access Windows files in Linux or even change files, ntfs-3g will work perfectly fine -- no need to copy around gigabytes of data or do any extra work!


If you have any further questions, please let me know.

---

### Post by SOULRiDER on 2007-04-16
You can read NTFS out of the box, but not write. Allt he files will work in ubuntu, from MP3s, to OOo and M$ Office files created in windows. You can import FF bookmarks.

As for the last question, i dont really know, but i would do this. If you are gonna back up stuff rom widnows keep it NTFS, if youre gonna backup ubuntu (which isnt really needed IMHO) then you should make one of them EXT3 and keep the other one NTFS.

Good luck!

---

