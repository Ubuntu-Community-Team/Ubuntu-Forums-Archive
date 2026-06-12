---
title: "Notes about installing 10.10 on a core 2 duo (9,1) iMac"
date: 2010-12-18
forum: Apple Hardware Users
---

### Post by gsteff on 2010-12-18
I had a lot of trouble installing 10.10 on my early 2009 iMac.  I installed refit, and was able to get it to detect the bootable livecd, but I'd get a blank screen with a small, incomprehensible icon at the bottom center (part of it looked like a person inside a circle) and then it would hang indefinitely.  Running the alternative install cd worked much better, though after several attempts at repartitioning both within OS X and the Ubuntu installer, I evidently got the two versions of the partition table out of sync and confused refit, which I solved the quick and dirty way by completely reinstalling OS X after using the disk utility inside the OS X installer to wipe out the old partition info.  

At some point in my installation attempts, I also got a kernel panic message about "not syncing: VFS: unable to mount root fs" that I'm guessing was because all my partitions were formatted as HFS, and the livecd couldn't mount any of them as a filesystem.  Or maybe not, I'm not sure.  I don't remember how I got those to go away- that was more than a week ago- but it may have been by formatting one of the partitions as something other than HFS.  I know that in my last attempt, I started the installer with an HFS partition followed by a big block of free space, which worked fine.

After completing the installer, Ubuntu still wouldn't boot- in recovery mode, I'd see a "pramin flush timeout" error message, which was related to problems with the builtin nouveau nvidia driver.  By adding "nouveau.noaccel=1 blacklist=vga16fb" to the kernel boot options, I was able to get past that error and boot, then fix the problem permanently by installing the proprietary nvidia driver.  I was able to get wireless to work by installing the Broadcom STA proprietary driver (the b43 wouldn't work for me).  Sound, the keyboard and the mouse all worked fine out of the box.  

So, in summary: the nVidia cards that come with some apple machines don't work with the default nouveau driver, which will cause both the livecd and the initial 10.10 install to fail.  Use the alternative installer, and then add the above kernel options to get yourself a usable system.

---

### Post by Symbolix on 2011-12-26
Hi,
Could you please give some more information about this. I have exactly the same model and have been trying fragmented solutions I got from various posts. But it is still a huge mess, no luck.

The partitioning worked fine, I have three partitions working fine. OSX, XP and LINUX.

However the problem is always around the "Nvidia driver issues" some other problems. Basically the "nomodeset" solution works, the Linux boots, the other grub line aiming to prevent the nvidia drivers messing up also kind of works but the X Windows does not start and it is all a huge mess :(

I am trying 11.10 (mac) and couple of other 11.10 64bit install packages but do not have a lot of hope.

Could you please share your solutions in more detailed way?

Thanks.

---

