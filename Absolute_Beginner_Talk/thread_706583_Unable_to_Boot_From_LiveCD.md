---
title: "Unable to Boot From LiveCD"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by DanMonkey3 on 2008-02-24
I am a first time user, and I read the READ THIS FIRST post, but I can't figure out what's going wrong here. I burned the Ubuntu 7.10 image to a CD, and when I turn on my computer with it in, I get the Ubuntu menu, so it's not a problem with the burning. However, when I try to boot up the live CD, the loading screen comes on, I see the text commands being run, and then nothing. The screen turns black and nothing happens unless I hard restart. I suspect it may be a graphical problem with my laptop: an Aurora M9700 with an Nvidia GeForce GS 7900 GS 512mb SLI graphics card.

Can anyone help me?

---

### Post by overdrank on 2008-02-24
> **DanMonkey3 said:**
> I am a first time user, and I read the READ THIS FIRST post, but I can't figure out what's going wrong here. I burned the Ubuntu 7.10 image to a CD, and when I turn on my computer with it in, I get the Ubuntu menu, so it's not a problem with the burning. However, when I try to boot up the live CD, the loading screen comes on, I see the text commands being run, and then nothing. The screen turns black and nothing happens unless I hard restart. I suspect it may be a graphical problem with my laptop: an Aurora M9700 with an Nvidia GeForce GS 7900 GS 512mb SLI graphics card.

Can anyone help me?

Hi and welcome, have you tried the safe graphics mode and if you would like you can try the alternate cd to INSTALL. The alternate is not a live cd but a text installer. Found here
[http://releases.ubuntu.com/releases/7.10/](http://releases.ubuntu.com/releases/7.10/)

---

### Post by DanMonkey3 on 2008-02-24
I have tried safe graphics mode, but that doesn't work either. I don't want the text installer because I want to try it out first before I start messing with my partitions.

---

### Post by overdrank on 2008-02-24
> **DanMonkey3 said:**
> I have tried safe graphics mode, but that doesn't work either. I don't want the text installer because I want to try it out first before I start messing with my partitions.

Hi and you can try, when you reach the screen to start/install ubuntu press F6 and edit the kernel line and remove quiet splash and add vga=771 or 775 and then hit enter. Hope this helps and good luck!

---

### Post by radiocognition on 2008-02-24
Are you sure that you have a good CD.  Run a checksum on it and compare it to the MD5 checksum for Ubuntu

---

### Post by overdrank on 2008-02-24
> **radiocognition said:**
> Are you sure that you have a good CD.  Run a checksum on it and compare it to the MD5 checksum for Ubuntu

Good point radiocognition
Then you may want to do a checksum on the cd 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by bayouoldguy on 2008-02-24
> **DanMonkey3 said:**
> I am a first time user, and I read the READ THIS FIRST post, but I can't figure out what's going wrong here. I burned the Ubuntu 7.10 image to a CD, and when I turn on my computer with it in, I get the Ubuntu menu, so it's not a problem with the burning. However, when I try to boot up the live CD, the loading screen comes on, I see the text commands being run, and then nothing. The screen turns black and nothing happens unless I hard restart. I suspect it may be a graphical problem with my laptop: an Aurora M9700 with an Nvidia GeForce GS 7900 GS 512mb SLI graphics card.

Can anyone help me?

Hi DanMonkey3; Before messing with any settings.....do the " MD5 Sums" check, you may have bad download....I too am NEW ubuntu & followed the directions EXACTLY !.
1. Download & install on the desktop " MD5 SUMS" from  the sources.
2. Download & install  the open source "INFRA RECORDER" from the sources.
   ( i had burn problem with an installed burner on my XP machine ).
3. Run MD5 SUMS on the downloaded file. ( check against the source file , copy from &   
    paste to the check box )..
4. Burn the C-D using the "INFRA RECORDER".( as slow of a speed it will allow ).
5. Then try Ubuntu Live 7.10 in your system...allow a few minutes cause it loads into
    ram, then runs....
6. See if this works...good luck, ubuntu looks like the last system that Microsoft made     
    me ( BUY ) !     "G" :)

---

### Post by DanMonkey3 on 2008-02-24
Sorry, I forgot to mention that I have already run the checksum and run the boot menu option of checking the disk. I tried to remove quiet splash and  input VGA=771 into both the normal and safe graphics starts, to no avail. I'll get back to you all tomorrow when I have time to try it with VGA=775.

By the way, what am I doing when I do that?

---

