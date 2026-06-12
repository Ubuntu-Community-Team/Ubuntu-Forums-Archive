---
title: "Grub Hard Disk Error"
date: 2007-10-18
forum: Apple Intel Users
---

### Post by Skook on 2007-10-18
Hey all. After seeing much hype about the new Gutsy release, I decided that I'd want to try and get it running just to see what all the fuss is about. I have some Linux hours under my belt, mostly with Fedora, but I'm not exactly experienced by any means. 

With that said, I have a new Aluminum 20" iMac with the ATI HD 2600 graphics chip. I have OS X and Windows XP on the main hard drive, and I wanted to install Gutsy on my 160gb External drive. I did the installation, told Gutsy to install on the external drive (with the basic selection after the keyboard screen, didn't do a custom partition). Installation went smooth and completed. When the computer rebooted, the first thing I did was check to make sure OS X still worked, which it did. After that, I tried to boot Gutsy and I got an error message: GRUB Hard Disk Error. I then restarted and tried booting to XP and got the same message. 

I did some searching and saw that some people got around the error by choosing to boot from the hard drive with the Ubuntu CD, but that didn't work. I also saw some sudo grub instructions [here](http://ubuntuforums.org/showthread.php?t=224351), which it said it was successful, but I still get the GRUB error. 

So now here I am at the gas station asking for directions. What is it that I'm doing wrong? Any help is greatly appreciated :)

---

### Post by garethrv on 2007-10-19
Hey,

Unfortunately from what I can tell from another thread here about booting from an external, you cannot do it if you have an internal windows partition.

Not sure what the reason for this is, but it is certainly an issue identified in this thread

[http://ubuntuforums.org/showthread.php?t=510030](http://ubuntuforums.org/showthread.php?t=510030)

I have a little external drive with Feisty on it and I can happily plug it into my macbook and boot from it, however when I plug into my brothers macbook pro which has XP on it, I cannot get it to boot.

However, I never got an error, just windows. So maybe there is hope for you yet.

Good luck, hope I was able to shed some light.

Gareth.

---

### Post by Skook on 2007-10-19
> **garethrv said:**
> Hey,

Unfortunately from what I can tell from another thread here about booting from an external, you cannot do it if you have an internal windows partition.

Not sure what the reason for this is, but it is certainly an issue identified in this thread

[http://ubuntuforums.org/showthread.php?t=510030](http://ubuntuforums.org/showthread.php?t=510030)

I have a little external drive with Feisty on it and I can happily plug it into my macbook and boot from it, however when I plug into my brothers macbook pro which has XP on it, I cannot get it to boot.

However, I never got an error, just windows. So maybe there is hope for you yet.

Good luck, hope I was able to shed some light.

Gareth.

Ahh, thank you for pointing that out :)

---

### Post by cyberdork33 on 2007-10-19
Booting Ubuntu from an external drive just doesn't work well. Some people can get it to work, others can't. There is no definite solution to the problem (we can't figure out what the underlying problem is).

---

