---
title: "Booting from USB2 external?"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by Name141 on 2008-03-23
Hello, I was thinking about using an external HD to install and boot Ubuntu from , would this run good ENOUGH for me to test it out , to see if I want to install it internally and get rid of windows? Or would it run much too slow for even testings?  Second off, lets see if I got it down how to perform this..

1. set BIOS to boot from DVD, USB, then internal.
2.  Install Ubuntu to USB, and leave the internal and other external alone.
3.  I should then be getting GRUB from the external, asking me if I want linux (on external #1) , or windows on the internal?
4. Either OS should work fine this way with no data loss?

The reason for this is there is 2 dell partitions internal, and the main NTFS partition where everything else is, that I don't want to resize and guess at, plus I don't want data loss.

---

### Post by smartboyathome on 2008-03-23
I installed Ubuntu just fine on my external hard drive by using [this guide]("http://ubuntuforums.org/showthread.php?t=678146").

---

### Post by lucasl on 2008-03-23
Why not use a LiveCD to test? Or you could use [Wubi]("http://wubi.sourceforge.net/").

---

### Post by Name141 on 2008-03-23
Cause the live CD is slow as @)(#$32, and I can't save data to return back to it.

Second, I don't want to.

---

### Post by Name141 on 2008-03-23
> **smartboyathome said:**
> I installed Ubuntu just fine on my external hard drive by using [this guide]("http://ubuntuforums.org/showthread.php?t=678146").

I see, so the simple form I was hoping for wont work?

---

### Post by smartboyathome on 2008-03-23
Not unless you are able to remove the internal hard drive temporarily, install it on the external, and then put the internal back in. That is the only other way to do it.

---

### Post by Name141 on 2008-03-23
> **smartboyathome said:**
> Not unless you are able to remove the internal hard drive temporarily, install it on the external, and then put the internal back in. That is the only other way to do it.

That would probably mess up my dell hardware warranty no doubt.  So my best bet seems to be following the guide so far.  It appears all I have to do if I get in a jam, is run the XP disk , and run fixboot and/or fixmbr ?

---

### Post by smartboyathome on 2008-03-23
fixmbr is part of the repos, install it on the ubuntu disk and run it, and then it will fix your XP boot.

---

### Post by Name141 on 2008-03-24
> **smartboyathome said:**
> fixmbr is part of the repos, install it on the ubuntu disk and run it, and then it will fix your XP boot.

Repos?

---

