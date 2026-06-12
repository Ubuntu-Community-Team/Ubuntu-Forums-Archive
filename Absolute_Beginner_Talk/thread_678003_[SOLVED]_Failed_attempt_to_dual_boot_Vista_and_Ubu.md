---
title: "[SOLVED] Failed attempt to dual boot Vista and Ubuntu"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by karl-arthur on 2008-01-25
Hi,

I just got a new Dell laptop (vostro 1400) with Vista pre-installed. I followed the instructions here: [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)  
i.e, I used Vista's disk managment tool to resize the partition, leaving about 40 gigs of "unallocated space". Then I let the Live CD 7.10 use the guided partitioning finding the largest contious space. However, there was a error on the disk (later confirmed with the "test cd" option in the startup screen), so the install was aborted. Trying to boot back into Vista to make a new Live Disk, it seems like the computer no longer recognizes the hard drive as a bootable device: "No bootable device -- strike F1 to retry boot, F2 for settup Utility. Press F5 for onboard diagnostics."

Any ideas? I have the Dell recovery disk and a Live disk with Ubuntu 7.04 that I know works, but I'm nervous that if I just install Ubuntu, I'll be unable to access Vista again. Help appreciated.

---

### Post by obscur156 on 2008-01-25
A very simple tutorial to dual boot vista and ubuntu.
I have used it as a total noob to linux and ubuntu and it worked straight forward without any problems.

Follow the step by step instruction and you will be running ubuntu in 25 minutes.

If you dont have 2 pc to follow the instruction,just print the instruction before installing ubuntu.

Its very simple so dont be scared and try it.
Follow that link:
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty]("http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty")

Good luck and give feedback if it worked or not.
Best regards

---

### Post by karl-arthur on 2008-01-25
This looks like a good howto, but I've already been through all of its steps, and the problem is that now my computer doesn't boot into Vista at all, and doesn't have Ubuntu installed because of the flawed disk. I'm hoping that it'll work if I just get a working Live disk and install Ubuntu, so that Vista will be able to boot from Grub, but I wanted to hear what people here had to say first, as I'm really only pretending to know about these matters. So if anyone has any ideas as to why the harddrive is no longer bootable, and how I can fix it, that would be great.

---

### Post by cmo220 on 2008-01-25
You can try super grub disk. [http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

I have used it several times for similar things and gotten it fixed.  If you choose the option to use super grub disk with help you should be able to figure out what to do.  Reinstalling with a good live cd should work also.  It had no problem finding my vista installation on its own.

---

### Post by obscur156 on 2008-01-25
Looks like your grub are screwed up,cmo220 gives you a good link to resolve the issue.

Maybe just installing ubuntu the ritgh way can repare the grub menu,not sure.

You can check your CD image when booting from the cd to make sure that the image is ok.You can even do a md5checksum to see if the image is good.

Good luck,best regards.

---

### Post by rosegarden78 on 2008-01-25
Last time I checked guided partitioning it asked me to use entire drive.  If that happened the whole drive was formatted and split up for use with Linux.  If you run Ubuntu live cd installation stop at Step 4.  Use custom instead of guided.  You should see like sda1 used for ext3 used as /, and a partition called swap with no mount points.  If you still have windows you should see it as NTFS or FAT32.

If windows still exists get your Dell Vista Recovery CD.  My XP used to let my repair a previous installation.  When it asks for partitions use the first one.  Then install Ubuntu GG 7.10 as usual but stop at Step 4 and use custom.

If you must, split your windows 50/50, 60/40, or even 20/80 if you seldom use XP.  Make all partitions "primary."  This is important.  Now let Ubuntu continue to install on the second part you just split.  If it asks make sure you have a "/" or root file system and a swap.

Then check my post for how to make your desktop Vista/OSX.
[http://ubuntuforums.org/showthread.php?t=677959](http://ubuntuforums.org/showthread.php?t=677959)

---

### Post by karl-arthur on 2008-01-25
Thank you so much, that was exactly (and all of) the information I needed!

---

