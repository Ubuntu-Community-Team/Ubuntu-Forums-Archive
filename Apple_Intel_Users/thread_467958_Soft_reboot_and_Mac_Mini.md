---
title: "Soft reboot and Mac Mini"
date: 2007-06-08
forum: Apple Intel Users
---

### Post by ggreco on 2007-06-08
Hello guys, I'm writing here cause I'm unable to solve this problem myself, I've googled a lot for it and I've tried a few options without luck with any of them.

The problem is that my Mac Mini doesn't boot to linux after a soft reset (restart from gnome menu, also on the login screen).

The Mac is an early 2006 macmini with the firmware updated to the latest version (mm11.0055.b08).

Ubuntu version is 7.04, and works perfectly, the problem is that this computer should be used also in a remote enviroment, so being able to reboot it is very important....

My first installation try has been straight:

After checking the bios version in OSX I restarted the mini with the C pressed & the ubuntu 704 cd inside the optical drive and I installed wiping osx (automatic disk layout, wipe everything).

The system worked correctly after I manually set the linux partition as bootable, but only on hard reboot.

So I thought the problem was the fact I've wiped the efi partition. So I followed another guide: I installed back osx, verified the presence of the efi partition, installed bootcamp, resized the osx partition, installed refit, installed ubuntu. Now I have a dual boot osx/linux machine, I've uncommented in refit directory legacyfirst to boot linux as default os, and this works, the problem is the reboot still doesn't behave correctly if the "shutdown -r now", "reboot" or the gui "restart" option are given by linux. Note, if I boot OSX I can soft reboot to OSX or linux without problems.

NOTE: I've also used GPTSYNC after the linux installation to check if that did the trick.

It seemed a kernel related problem and not a bootloader problem since OSX is able to reboot without problems...

The behaviour is not the same every time, sometimes after a restart I get only a black screen, other times it shows the gray screen and the refit boot menu, then it "power downs" the monitor and stand there forever... maybe a crash of the bios emulation?

Here is the parted output of the partition layout if it can be useful, together with the kernel specification (the vanilla i386 one):

darts@multiview:~$ uname -a
Linux multiview 2.6.20-16-generic #2 SMP Wed May 23 01:46:23 UTC 2007 i686 GNU/Linux

Disk /dev/sda: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
 1      20.5kB  210MB   210MB   fat32        EFI System Partition  boot 
 2      210MB   29.2GB  29.0GB  hfs+         Apple_HFS_Untitled_1       
 3      29.3GB  60.0GB  30.7GB  ext3         Untitled 2

---

### Post by ronocdh on 2007-06-08
Hm, this is very interesting. You mention a suspicion that it might be kernel related; can you document which kernels you've used so far, and what the different effects have been? I think I'm still on 2.6.20.15 because of the wireless problems I ran into when upgrading to .16. 

This is indeed a bizarre problem, but you're not alone. See [here]("http://ubuntuforums.org/showthread.php?t=455531") and also [here]("http://ubuntuforums.org/showthread.php?t=427217"). Hopefully those posters comment on this thread with their experience. If you don't hear anything productive about the situation in a few days, you might want to PM them. But please remember to then post for all to see your progress! Good luck on this one.

---

### Post by ggreco on 2007-06-13
I've done some additional tests on this issue.

I downloaded knoppix 5.1.1 and tried to do a few soft reboots with it, the system worked flawlessy, knoppix used the i810 video driver while I was using the intel one, so I switched back to i810 on the ubuntu distro on the HD, but the soft boot problem is still present :(

The fact is that knoppix live CD rom never fails a reboot, it uses kernel 2.6.19 instead of the 2.6.20.15 and 2.6.20.16 I've tried with ubuntu.

There is an easy way to build a 2.6.19 kernel and use it with an ubuntu feisty distro? I don't care about wireless driver.

---

### Post by ggreco on 2007-06-14
The problem was the 2.6.20.15 (and 16) of feisty. I compiled the latest stable kernel (2.6.21.5 from kernel.org) with make oldconfig (using the 2.6.20.16 ubuntu config), I built a kernel package with the following command:

sudo fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers

I installed the kernel.... no more soft reboot problems! So it seems there is a problem with the stock ubuntu kernel and mac mini...

---

