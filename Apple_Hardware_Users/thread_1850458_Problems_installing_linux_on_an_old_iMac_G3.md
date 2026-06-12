---
title: "Problems installing linux on an old iMac G3"
date: 2011-09-26
forum: Apple Hardware Users
---

### Post by el_badbit on 2011-09-26
I have an old iMac G3 (333 mhz, 256 mb RAM, 160 GB HD). I used it to listen to music and online radio, but it's so limited now that I wanted to install a lightweight linux distro to bring it back to life.

I've tried a number of distributions and none of them work. At first they booted from CD and then said that they couldn't mount the filesystem. So I erased the MacOS X partition and reformated the drive with the UNIX filesystem. Still, every distribution I've tried crashes when trying to boot the kernel (Yellowdog, Slackintosh, Xubuntu, FreeBSD).

The last one I tried was Finnix, and when I tried to boot the kernel the following message appeared::(:(:(

```
cd:2,/boot/linux: Unknown or corrupt filesystem.
```

I can't even use fdisk as no distribution will boot. I don't want to do anything fancy with my iMac, I just want a bash prompt and some basic tools like vim and ssh. Any ideas?

---

### Post by snafu006 on 2011-09-26
is it a slot loading cd drive or tray loading drive

---

### Post by oswaldkelso on 2011-09-27
I see you have a larger HD than standard so this may help?
> 
"The second big tray-loading iMac problem is shared with the WallStreet PowerBooks and beige G3 Power Macs - any drive over 8 GB must be partitioned, the first partition must be smaller than 8 GB, and these models will only boot from OS X if it's installed on the first partition."

This also applies to linux, if you have fitted a larger HD put boot and root on the first 8gb and a separate home partition on the rest. If your going to dual boot. Osx must be on the first partition. Linux on the second, both within the first 8gb. This is a hardware constraint not software.

---

### Post by el_badbit on 2011-09-27
It is slot loading and I replaced the original HD. There's no problem with the bigger HD, it runs mac os x 10.3.9 just fine.

The problem was the CD-RW I was using to boot the machine. I burned the images on CD-Rs and worked just fine. I installed Debian minimal, now I have another problem.

After the system boots, and right before the login screen appears, the monitor goes black and nothing happens. I tried passing arguments like vga=ask at bootup but with to no avail. Any ideas?

---

### Post by oswaldkelso on 2011-09-28
Then I suspect it's not a 333MHz. Maybe a 350MHz? 
[http://www.applefritter.com/node/23764](http://www.applefritter.com/node/23764)

---

