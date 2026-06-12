---
title: "An unorthodox OSX reinstallation question"
date: 2008-01-14
forum: Apple Intel Users
---

### Post by Rog-Mahal on 2008-01-14
I decided to completely wipe my macbook and singleboot ubuntu. So far, I am pretty content, however, in the interests of firmware updates and such, I think that I want to create a small OSX partition. Can I do that? Would I be able to then boot into OSX and install rEFIt? Any opinions/help would be greatly appreciated.

---

### Post by benanzo on 2008-01-14
I have done exactly what you're describing.

```

ben@adola:/media/MacOSX$ df -h .
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             9.8G  5.0G  4.9G  51% /media/MacOSX
ben@adola:/media/MacOSX$

```

As you can see I've created a 10GB partition with OS X installed on it.  I haven't installed any of the superfluous OS X stuff like iLife or anything.  I opted for the bare minimum, which you can see takes up 5GB.  I have rEFIt installed to the OS X partition and GRUB installed to /dev/sda3 (Ubuntu Gutsy).  I have /dev/sda4 as my /home directory in Ubuntu.

So yes, you can do it.

---

### Post by tchorix on 2008-01-15
Hi benanzo,

There is an important issue to consider here. Did you have a bigger partition with OS X on it, and then resize it to 5GB in order to install Ubuntu? or did you first create the 10GB partition to install OS X in that particular one?

I tried once to install OS X in a 20GB and it didn't allowed me. It just failed with a ridiculous message saying something like: "The installation failed, please try again", I tried to see the details and I got an error number... I searched for it on the internet but I didn't find anything... probably, people trying to get a customized OS X is not at all a big community. Mac users usually use their software as they get it...

cheers

---

### Post by benanzo on 2008-01-15
Either way will work fine.  You can create a 10GB parition with diskutil before/during installation or you can install to the whole disk then shrink it later.  I've done both.

---

### Post by Rog-Mahal on 2008-01-15
Great! Thanks for the info.

---

### Post by tchorix on 2008-01-17
Ok, thanks for the clarification... good to know that is possible in case I need that once.

cheers

---

