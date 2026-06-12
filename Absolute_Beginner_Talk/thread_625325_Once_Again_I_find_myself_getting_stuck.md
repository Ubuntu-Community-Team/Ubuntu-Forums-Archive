---
title: "Once Again I find myself getting stuck"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by 449 on 2007-11-27
Hello again, I have another problem that I am having trouble sorting out. My dad brought home a computer from work and said the harddrive was fried. So I thought I could install Kubuntu on my external harddrive because this computer has decent specs: pentium 4, 512 MB RAM. So anyways I put in the live cd it boots up I install and it tell me to restart. When I restart it it says something like "loading grub 1.5" and beneath that is says "error 17." Now it is possible that something else is messed up on this computer ,but I don't know how to check. If anyone could shed some light on this issue that be great. Thanks!

Also, right now I'm running the Ubuntu live cd to see if it will work ,but it's been stuck at 15% "detecting file systems" for quite some time now.

---

### Post by OldTimeTech on 2007-11-27
Check out this link:
[http://www.justlinux.com/forum/showthread.php?threadid=149484](http://www.justlinux.com/forum/showthread.php?threadid=149484)

---

### Post by 449 on 2007-11-27
Thanks for the link and quick response! After reading the Gnome vs KDE thread I've decided to install Ubuntu instead since this machine should be able to handle the effects.

---

### Post by 449 on 2007-11-27
Hm, is skimmed through most of it and I only have three partitions so why do I get that error?

---

### Post by OldTimeTech on 2007-11-27
something didn't like something....best answer I have at the moment.

---

### Post by 449 on 2007-11-27
Well right now I'm trying to install Ubuntu and it get's stuck at 15%. Do I need to wipe the files with Gparted from the Kubuntu install?

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       25302   203238283+   c  W95 FAT32 (LBA)
/dev/sda2   *       25303       30274    39937590   83  Linux
/dev/sda3           30275       30401     1020127+  82  Linux swap / Solaris

---

### Post by OldTimeTech on 2007-11-27
my suggestion would be to use an alternate disk, it doesn't use a GUI and is a text based install.....shouldn't have to wipe your drive, it should ask you if you want to format your drive when getting ready to install.

---

### Post by 449 on 2007-11-27
> **OldTimeTech said:**
> my suggestion would be to use an alternate disk, it doesn't use a GUI and is a text based install.....shouldn't have to wipe your drive, it should ask you if you want to format your drive when getting ready to install.

Ok, I'll try this. Am I still going to get the error 17?

---

### Post by OldTimeTech on 2007-11-27
Okay....I re-read your initial question....what hard drive are you installing this on....the old one in the computer or the backup drive?

---

### Post by 449 on 2007-11-27
> **OldTimeTech said:**
> Okay....I re-read your initial question....what hard drive are you installing this on....the old one in the computer or the backup drive?

The external hdd is the *only* hdd. It's 250 GB with a 39 GB and 1 GB (for swap) partion.

---

### Post by OldTimeTech on 2007-11-27
I don't think ubuntu is trying to install to the external, I think it's trying to install to the original drive and that's why your getting the error 17.

Sometimes hard drives aren't fried.....so with that thought, try formatting the hard drive with gparted, download from here: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) and then try to install ubuntu or kubuntu again....see what happens, if still doesn't work then definitely the old hard drive is fried....may just be it's tired of windows.

I need to see what I can find on external drives....but try above first.

---

### Post by OldTimeTech on 2007-11-27
okay...check this out and see if it helps with doing the external drive thing....
[http://ubuntuforums.org/showthread.php?t=624841&highlight=external+drive+with+ubuntu](http://ubuntuforums.org/showthread.php?t=624841&highlight=external+drive+with+ubuntu)

---

