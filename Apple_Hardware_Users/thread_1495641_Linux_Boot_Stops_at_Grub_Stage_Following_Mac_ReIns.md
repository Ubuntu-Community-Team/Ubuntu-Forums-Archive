---
title: "Linux Boot Stops at Grub Stage Following Mac ReInstall"
date: 2010-05-28
forum: Apple Hardware Users
---

### Post by BFeaver on 2010-05-28
I reinstalled Mac OSX and my Mac files on my 24" intel core 2 duo iMac from a Time Machine backup.   The Linux and Swap partitions appear to be unaffected.   However, rebooting into Linux 8.04 stops at the Grub stage.  Suggestions please.  

Blue side up,
Bob

---

### Post by linuxopjemac on 2010-05-28
My wild guess is to reupdate Grub in your system

```
sudo update-grub
```

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by BFeaver on 2010-05-28
Booting into Linux stops at Grub Stage 2.   Typing anything other than reboot results in "Error 27: Unrecognized Command"  

Thanks for your reply.  

Blue side up,
Bob

---

### Post by BFeaver on 2010-05-28
Oopps,  I missed your link.   Checking this out now.  

Blue side up,
Bob

---

### Post by linuxopjemac on 2010-05-28
chroot into the system from a liveCD and then do that command

[http://mac.linux.be/content/chroot-system-livecd](http://mac.linux.be/content/chroot-system-livecd)

---

### Post by BFeaver on 2010-05-28
Oh boy...  once again I am over my head.  haha

I started up from my Linux install disk and choose demo mode.   I opened Terminal and entered the chroot into system from liveCD commands.  

The second line sudo mount -t ext4...  returned "unknown file system command type 'ext4' "


Blue side up,
Bob

---

### Post by linuxopjemac on 2010-05-29
I don't see why you want to mount a filesystem. When you chrooted into the system you are working in your Linux computer as if you booted into it. It's a hack to fix things when you can't boot into it. Just do an sudo update-grub. It should do the job.

---

### Post by BFeaver on 2010-05-29
I was denied permission to sudo update-grab from the liveCD.  

But you have given me an idea. it is very possible I can achieve my few Linux needs directly from the liveCD.  I only use Linux to do short test drives of my plugins for the X-Plane flight sim.  

Yesterday I downloaded a copy of Ubuntu 10.04 for use as a live CD.  I will test this out. 

Also, seeing as I have previously created Linux partitions on my Mac I may do a fresh install of my Linux platform to 10.04.   I may not get to this until later next week.  

I truly thank you for your time and patience;  manning this forum with such diligence is a major responsibility. 

Blue side up,
Bob

---

