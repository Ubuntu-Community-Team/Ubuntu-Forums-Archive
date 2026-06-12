---
title: "Directory / reads as 100% full; cannot login"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by DMUSER on 2007-05-02
I'm currently dual-booting with Windows XP and Feisty Fawn.

I just installed Ubuntu a couple of days ago, and have been spending the last couple of days getting everything working to my satisfaction.

I was in the process of improving performance on the desktop, and I did two things(that I can remember)

1. Disabled AGPGART(blacklisted) and enabled the NVIDIA binary AGP drivers

2. Stopped klogd service (it was continuously using 20-60% of my CPU for some reason)

I have absolutely no idea if either of those things caused the problem I'm having now, but when I rebooted to see if AGP was working properly I got this error message(approximately) when I tried to log in:

GDM cannot write to your authorization file.  You cannot log in.  Please contact your System Administrator.

It's longer than that but I can't remember it all.  I can post it word-for-word if required.

When I log on as root, it comes up with a message telling me that my / drive is 100% full.  I have 10Gb in the Ubuntu partitions, and all I've installed is some drivers, VLC, Cedega, and Wine.  So I have no idea how that could possibly be.

My system specs are:

Athlon XP 2400+ (running at 2000Mhz)
1024 Mb DDR333 RAM
GeForce 6800 GS 256Mb
80Gb Maxtor Diamondmax (dual-booting Windows XP and Ubuntu Feisty Fawn)

I can provide logs and such if required if someone can point me in the direction of what I need and how I get them/post them.

Any help is much appreciated.  Thanks.

---

### Post by taurus on 2007-05-02
Boot into recovery mode from GRUB menu and do a little house cleaning.

```
aptitude clean
df -h
```
That should clean out the archives, giving you some free space to write to disk.  Then, reboot and see if you can log in now.

```
shutdown -r now
```

---

### Post by macogw on 2007-05-02
Ubuntu takes about 5GB with programs.  If you have language packs, that's more.  If you have a lot of stuff in your apt archives, that's more.  Do what taurus said.  Is your home drive part of that 10GB?  If so, that's a rather small partition to try to fit everything on.  You might want to store all of your own files in a different partition (say, on your Windows partition).  I wouldn't be surprised if Cedega and Wine take up quite a bit of space.   To keep the apt archives from making it fill again, open up Synaptic, go to Settings > Preferences > Files and choose "delete downloaded packages after installation"

---

### Post by DMUSER on 2007-05-02
That fixed it.  My drive actually was full, I just didn't know it.

On the upside I have everything working as well, or better than I do in XP.  Giving weight to me just turfing Microsoft right out the front door.

As a stopgap for now I think I'll use an external drive for multimedia storage until I get a second internal drive.

Thanks for the help.

---

