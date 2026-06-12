---
title: "Broken grub installation"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by cwa107 on 2006-06-19
Hello all -

I've searched through the forums and read a number of threads, but haven't found one that provided the solution I was looking for.  

Here's my situation - I have a Dell Latitude C400 setup to dual-boot Ubuntu 6.06 & XP.  GRUB was installed as the bootloader on the MBR.  I backed up my drive using Ghost Enterprise 7 and then installed a newer (larger) hard drive and brought that image back down on the drive.

Now, when I attempt to boot my system, the word GRUB appears on every inch of the screen and the machine does not boot.  I searched and found this thread:

[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=ghost+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=ghost+grub)

But neither methods repaired my issue (I believe the first method assumes Ubuntu 5.10 and method 2 assumes you are using different boot loader and DON'T want it on the MBR - which I do).

Anyway, I just want to put things back the way they were, meaning, I want to use grub (installed on the MBR) and have the option to boot into Ubuntu or XP.  

I'm a major noob as it relates to Linux, but an old hand with Windows, so any help would be appreciated.

---

### Post by catlett on 2006-06-19
I think something happened when you transfered the image. If you are good with windows and new to linux this is the easiest way to do it. Believe it or not. This way you will be back in an hour as opposed to taking an hour to try a bunch of different things.

Get a windows install disk. Boot to recovery mode. Get to a command line and enter ```
fixmbr
``` That will get you booting again into windows.

In my signature is a link "access your ubuntu partition from windows" . If you have valuable data on Ubuntu use that link to install the drivers to read and write to ext3 from windows. Copy over any important information from Ubuntu into windows.

Reinstall ubuntu. The ubuntu install is very fast It never takes more than an hour. You already have the partitions made for it. 

Belive it or not this is probably the easiest way for you to have a dual boot windows/ubuntu system up and running in a hour. 

I'm sure others will post with other ideas. You can try them but this is mine.

Good luck.

---

### Post by jrd on 2006-06-19
If fix mbr don't work you may have to copy ntdetect and ntldr as well. I'm not sure what fix mbr does but one time it didn't work for me, so I copied those files over and then it worked fine.

---

### Post by cwa107 on 2006-06-20
Crap - I was hoping this would be easier.  I'm really not concerned about the XP installation - that's there for emergencies only.  I'm a Windows network admin and have been cutting my teeth on Linux using this laptop.  So far, I've gotten Ubuntu working properly with my wireless card, WPA support and Citrix client and I was hoping not to have to undo everything I've already done.  I did try to reinstall Ubuntu over top of itself and it failed.  Sounds like I may just have to go back to the old drive.  

Any advice or threads on the CORRECT way to upgrade HDDs without breaking either OS?

---

