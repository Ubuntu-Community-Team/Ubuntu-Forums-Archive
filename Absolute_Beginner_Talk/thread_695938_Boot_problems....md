---
title: "Boot problems..."
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by LostMagix on 2008-02-13
I let my brother use my computer and when i got back nothing worked. My system would power up but the system bell was going off and it wouldn't boot. I disconnected my power supply and removed my battery to reset my system and it worked. I could boot into grub and into the ubuntu load screen. Once at the load screen i got the black screen of death.


My brother said my computer was freezing while he was using it so he manually had to restart it. I am think that's what messed up my bios. 

After I tried a restore on it, I installed ubuntu on a 4gb drive I had laying around.

I dont want to wipe that hard drive, im hoping for a way to get into it and restore the corrupted data. I am still very new to Ubuntu and i dont even know how to get to the files on the drive.

Any help or advise would be greatly appreciated.


C.F.

---

### Post by dstew on 2008-02-13
> After I tried a restore on it, I installed ubuntu on a 4gb drive I had laying around.I don't understand what you did. Are you referring to the original installation in your computer that now won't boot properly, or did you install Ubuntu onto an external hard disk?> im hoping for a way to get into it and restore the corrupted dataAre you referring now to the hard disk in the computer that won't boot?

There are many ways to get at data on a hard disk that is not booting. You can boot a Live CD system, and try to mount the disk, and see if you can fix it, or copy files to another uncorrupted partition or external drive. But maybe the booting problem has to do with the video display, and the disk is not corrupt. At the black screen, press ctrl-alt-F1 and see if you get a command line.

---

### Post by LostMagix on 2008-02-13
I have a 40gb hard drive that i ran Ubuntu on, It some how was currupted and now im running on a 4gb hard drive i had from a old dell, running it as the master.

I was to restore the 40gb.

The data should still be there, it just wont boot.

---

### Post by LostMagix on 2008-02-13
With the 40gb drive connected I cant load grub on ether drive with out going using the "boot from first hard drive" option on the live CD

---

### Post by glennric on 2008-02-13
The first thing you should do is what dstew suggested.  Boot a livecd and try to mount the filesystem on the disk that won't boot.

---

### Post by OffAxis on 2008-02-13
Have you checked the boot sequence in the CMOS?
On startup press the Del key to access the CMOS configuration utility.
The boot sequence is probably in Advanced BIOS Setup, if not it's somewhere. Make sure that your hard drive is in there.

If it's the software that's messed up then try super grub
[http://supergrub.forjamari.linex.org/]("http://supergrub.forjamari.linex.org/")

or boot to command line  (from a live CD) - Rescue System or Safe Mode (I don't remember what it's called)
and

```
sudo grub
-->root (hd0,1)
-->setup(hd0)
-->quit
```

where hd0 is your hard drive mount point and 1 = the partition where grub is. If you've only got the one drive attached and it's only got one partition then that's probably it.

---

### Post by LostMagix on 2008-02-13
Im in the live CD but I am not sure how to get into the hard drive, or what to replace.


(like i said, im very new to Ubuntu)

---

### Post by LostMagix on 2008-02-13
This is to much to deal with right now, ill just restore the damn thing.

---

