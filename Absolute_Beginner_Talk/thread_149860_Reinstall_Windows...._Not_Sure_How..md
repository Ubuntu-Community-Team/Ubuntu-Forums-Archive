---
title: "Reinstall Windows.... Not Sure How."
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by ephman on 2006-03-24
hi,

i'm being forced to reinstall my windows (keep it around for some games i like) anyways any tips on how to reinstall XP so that after i reboot life will be good and i won't need any live cd's or anything like that to deal with losing grub.  is this possible?

thanks,
ephman

---

### Post by trent dillman on 2006-03-24
Windows XP will kill grub by default. You will have to reinstall grub no matter what.

Cursed M$.

---

### Post by WoodyMahan on 2006-03-24
Just went through this yesterday and today.  Your systems Master Boot Record gets set to default to Grub in a working Dual Boot system.  When you re-install Windows, the Windows Install reconfigures the MBR to default to Windows.  Grub is thus broken.  I would recommend backing up your Ubuntu System to and outside source.  Then Reinstall Windows, then reinstall Ubuntu, then restore you Ubuntu Backup.

---

### Post by Sef on 2006-03-24
> i'm being forced to reinstall my windows (keep it around for some games i like) anyways any tips on how to reinstall XP so that after i reboot life will be good and i won't need any live cd's or anything like that to deal with losing grub. is this possible?

Below is a link on how to reinstall grub.


[> https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28grub%29%7C%28reinstall%29]("https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28grub%29%7C%28reinstall%29")

---

### Post by trent dillman on 2006-03-24
You shouldn't have to hose your system. Install Winblows, then reboot with the Ubuntu disk, do an expert install, reinstall grub, and that should be it.

[http://ubuntuforums.org/showpost.php?p=854389&postcount=7](http://ubuntuforums.org/showpost.php?p=854389&postcount=7)

---

### Post by Mustard on 2006-03-24
If you have a live CD you can reinstall grub, or you can even do it with an install CD.  Instructions for doing so can be found in various places both in this forum and on the wiki.  Having recently mucked around with partimage myself, I wonder whether you could just make a backup of your MBR using the dd command and then you a live CD to restore your previous MBR from the backup.  I suppose you would then have to manually edit the grub menu to boot into windows.  Reinstalling grub with a live CD or install CD might be an easier option.

-edit-

Actually, I was just thinking, there is a live CD of a manageable download size called System Rescue CD.  It's got some good tools on it for doing this type of thing.  It's mostly command line stuff with some help functions.  It's got options to help with installing grub or lilo and even the GAG bootloader.

Another option would be to create a boot floppy, so you can boot from a floppy disk at a pinch.

To summarise I guess the best thing to do is read a lot before proceeding and print out some instructions, so you don't have to keep going online to get the instructions. :)

[http://www.ubuntulinux.org/wiki/GrubHowto](http://www.ubuntulinux.org/wiki/GrubHowto)  [https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows) 
or troubleshooting grub:
[http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting](http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting)

---

### Post by dvarsam on 2006-03-25
Hello !!!

I do NOT know if this helps, but I will tell you my experience...

I had 1 Hard Drive with "Ubuntu & Suse" Partitions.

When I deleted Suse, I could NOT boot my Ubuntu...

So, a "NON-Booting" problem does NOT only occur with "Linux-XP" cases, but also with "Linux-Linux" cases too!!!

Hope I helped a bit...

Good Luck!

---

