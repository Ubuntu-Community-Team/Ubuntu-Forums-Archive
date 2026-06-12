---
title: "DEBIAN EDITION. Mount the Windows partition."
date: 2012-05-15
forum: Any Other OS
---

### Post by Ryupower on 2012-05-15
SOO...
I've got Linux Mint Debian Edition (LMDE) installed, and so far, I'm loving it! Though having some technical bumps here and there regarding installing and dependencies for the newest stuff...it has been way more stable and reliable than the Ubuntu version.

Anywho, my beef though is that in Ubuntu, my windows partition is automounted from start. If I want to mount it on Mint Debian, however, I need to click the partition first and then mount it (or them) and enter password every time. It would be nice if the partition would be automounted upon login. How do I do this?

I figured it might have something to do with the mount flags, but I'm not sure. Whatever the case, here they are (from partition manager):

defaults,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077,fmask=0177

This is my Fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sdb2 :
UUID=18e99ac7-01da-4cb8-946a-b7dd06073881	/	ext4	rw,errors=remount-ro	0	1



The only partition here is the main partition with LMDE on it. My USB HDD mount automatically eventhough they're not on there. My windows partition needs to be mounted manually.
It might be obvious for some, call me stupid, but it's not me!

What do I do?

---

### Post by jefsview on 2012-05-15
I'm only seeing one drive in the fstab, and it's an ext4 one, not NTFS.

Here's a nice [tutorial]("http://fitzcarraldoblog.wordpress.com/2011/02/12/automounting-a-ntfs-partition-or-drive-when-linux-boots/") about getting a drive to automount.

Also, you could use one to set it up for you, like NTFS-config in the repos. I've used it several times instead of manually editing the fstab, because I would get errors when booting when I manually did it. 

good luck.

-- Jeff

---

### Post by coffeecat on 2012-05-16
> **jefsview said:**
> Also, you could use one to set it up for you, like NTFS-config in the repos. I've used it several times instead of manually editing the fstab, because I would get errors when booting when I manually did it. 

I have to say that you were lucky. ntfs-config has been unmaintained for years and often causes severe problems. I cannot recommend it after having had to help people out of the mess it can cause, several times in this forum. A pity, because we do need a good GUI method of adding lines to /etc/fstab.

@Ryupower, post the output of these terminal commands and I can help you with editing /etc/fstab manually so that your NTFS partition is mounted automatically on bootup.

```
sudo fdisk -lu
sudo blkid
ls -l /media
id
```

The last will give us your account UID. That may seem a strange request, but I'll explain if you post back with the details. In order to copy the terminal output into your post, you can highlight it, and then right-click to copy.

**EDIT**: I'm not sure whether Mint Debian edition uses the sudo model of Ubuntu and Mint based on Ubuntu. If it doesn't, su to root in the terminal and issue the first two commands without the sudo.

---

### Post by jefsview on 2012-05-16
realy, coffeecat? I've had nothing but good luck with ntfs-config.

Now, psydym was a horror story.

I've installed and reinstalled various OS's since switching to Linux so many times, I just like the process automated. Only time my external NTFS automounted itself was when I ran PinguyOS, but that was using gnome. I like Xfce better, since I run 3d software and like a lower resource OS, and I have found an Xfce distro that has auto-mounting of an always plugged in external.

editing fstab isn't too bad, especially once you run find your UUID, but doing so repeatedly just becomes tiring.

I'm hoping to be able to stick to one distro for a while now, though.

ps: most Debian distros do use Sudo these days, except for SID-based ones, which prefer sux or su. 

-- Jeff

---

