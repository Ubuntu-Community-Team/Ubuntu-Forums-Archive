---
title: "Make image of new install"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by mevets on 2007-05-08
I recently had to reinstall ubuntu. I am wondering if I would be able make a restore cd of how my system is right now with all the programs installed. I heard of programs like Ghost but I am not sure I it needs to be use as a boot cd or it can be run when the os is running? Anyway, how is this traditionally done?

edit:can this be done in a virtual machine so I can set it up in there in my spare time and then have whats there be made into an image that will later go a cd?

---

### Post by cypherzero on 2007-05-08
If you recently had to reinstall Ubuntu then your system will be a brand new one anyway - i.e.
all you have to do to restore it is boot up your Live CD and reinstall.

If you're looking for a XP-style 'System restore' there isn't one, short of the rather long winded method of copying all your files / the whole partition to somewhere else.

---

### Post by mills on 2007-05-08
> You could make an image using SystemRescueCd. It's a bootable CD, and it will make a bit-for-bit copy of whatever partition you want, giving you 3 options for compression (none, medium, or high). It took about 10 minutes for me to backup my entire Ubuntu install this way, so if anything goes wrong, all I have to do is use the CD to restore the image I created.

Also, unlike other methods, this method doesn't copy empty bits. Some backup programs copy the entire harddrive, but SRC only copies information. In other words, if you have an 80 gig hdd with only 6 gigs of data on it, SRC will only image the 6 gigs of data, rather than making an entire 80 gig image.

credit goes to cocoAUS from [this thread]("http://ubuntuforums.org/showthread.php?t=346946&highlight=burn+system+iso+disc")

hope its what your after

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

---

