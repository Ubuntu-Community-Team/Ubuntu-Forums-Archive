---
title: "Lost Grub on multiboot system"
date: 2008-01-08
forum: Apple Intel Users
---

### Post by PaulFXH on 2008-01-08
I have 3 Linux OSes (Gutsy, openSUSE 10.3 and Sidux 2007-4) on my MacBook (C2D).
I use rEFIt which brings up the icon menu (Mac Apple + Tux). When I click on the penguin, I get a further menu allowing me to choose which Linux OS I want.
However, today I tried to install a further Linux OS but this one was to be stored on a usb HDD hooked up to the MacBook (I have already done this a number of times without problem).
The install went fine, but when I rebooted to get back to the /boot/grub/menu.lst on the Gutsy partition (which is where I boot all my Linux OSes from), instead of grub starting up and showing me the boot menu, I get this message:
> No bootable device -- insert boot disk and press any key

So, I thought grub had been messed up by the install (although I really don't understand why installing something to a usb HDD should mess up grub on the internal drive) so I re-setup grub on the Gutsy partition.
However, this made no difference.
Grub still doesn't start which means that I cannot boot to any of my Linux OSes on this MacBook.
Any advice?
Thanks
Paul

---

### Post by PaulFXH on 2008-01-08
OK, I've solved this.
The problem was that my partition table were out of sync. However, I really have no idea how they got out of sync.
I can't rule out the possibility that the re-installation of rEFIt that I did might have induced this although no change at all to the appearance of the "no bootable device" message ocurred after the re-install which would argue against this.
Then you have to ask how installation of a Linux OS on a usb HDD could have had any effect on the MacBook partition tables.
Beats me

---

### Post by cyberdork33 on 2008-01-09
> **PaulFXH said:**
> OK, I've solved this.
The problem was that my partition table were out of sync. However, I really have no idea how they got out of sync.
I can't rule out the possibility that the re-installation of rEFIt that I did might have induced this although no change at all to the appearance of the "no bootable device" message ocurred after the re-install which would argue against this.
Then you have to ask how installation of a Linux OS on a usb HDD could have had any effect on the MacBook partition tables.
Beats meJust to add speculation, I would guess that your latest install altered the partition table for some reason, and the partitioner did not see the GPT, only the MBR... It could have been the fact that you have the USB device plugged in during boot too, I have noticed that rEFIt acts strangely sometimes when I have my iPod or a flash drive in the USB port.

---

### Post by ronocdh on 2008-01-22
> **PaulFXH said:**
> OK, I've solved this.
The problem was that my partition table were out of sync. However, I really have no idea how they got out of sync.
I can't rule out the possibility that the re-installation of rEFIt that I did might have induced this although no change at all to the appearance of the "no bootable device" message ocurred after the re-install which would argue against this.
Then you have to ask how installation of a Linux OS on a usb HDD could have had any effect on the MacBook partition tables.
Beats me
I am having a similar problem to this. I've been working on it for two days now and I'm at wit's end. Found this thread and I'd like to add to it with my woes.

Somehow my GPT and MBR got out of sync. I did not reinstall rEFIt&#8211;I'm hardly ever in OS X. I had a hard crash in Ubuntu one night, and went to bed after it. When I booted up in the morning, GRUB would hang at the "loading stage2" screen and never get passed it. I tried reinstalling GRUB, but I kept getting perplexing errors.

When I try the following method of grub installation:
```
sudo grub-install /dev/sda3
```
I get this error:
```
Could not find device for /boot: Not found or not a block device.
```
When I use another method of installing grub:
```
sudo grub
find /boot/grub/stage1          \output is (hd0,2)
root (hd0,2)
setup (hd0)
Checking if "/boot/grub/stage1 exists... yes
Checking if "/boot/grub/stage2 exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... failed (this is not fatal)
Running "embed /boot/grub/e2fs_stage1_5 (hd0,2)"... failed (this is not fatal)
Running "install /boot/grub/stage1 (hd0) /boot/grub/stage2 p /boot/grub/menu.lst "... succeeded
Done.
```
Then when I try assigning grub to the boot sector of just the Ubuntu partition, I get the same problem:
```
setup (hd0)
Checking if "/boot/grub/stage1 exists... yes
Checking if "/boot/grub/stage2 exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0,2)"... failed (this is not fatal)
Running "embed /boot/grub/e2fs_stage1_5 (hd0,2)"... failed (this is not fatal)
Running "install /boot/grub/stage1 (hd0) /boot/grub/stage2 p /boot/grub/menu.lst "... succeeded
Done.
```
After these methods I reboot and check the GPT/MBR sync in rEFIt, and the MBR is blank. More on that below.

Now, I have found [one plan]("http://www.linuxforums.org/forum/debian-linux-help/55618-wont-boot-after-upgrade-2.html") that actually does let me install GRUB without issue. This is how that went:
```
sudo grub-install --root-directory=/mnt/root hd0
Due to a bug in xfs_freeze, the following command might produce a segmentation fault when /mnt/root/boot/grub is not in an XFS filesystem. This error is harmless and can be ignored. 
xfs_freeze: specified file ["/mnt/root/boot/grub/"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /mnt/root/boot/grub/device.map
Check if this is correct or not. If any of the lines is incorrect, fix it and re-run the script 'grub-install'.

(hd0)    /dev/sda
```

Even after this method, which looks like it might have worked, I reboot and scope out the MBR. This is what the rEFIt Partitioning Tool screen tells me:

```
Current GPT partition table:
#      Start LBA        End LBA          Type
1      40              409639           EFI System (FAT)
2      409640          139230615        Mac OS X HFS+
3      139235355       168852887        Unknown
4      168852888       234441607        Basic Data

Current MBR partition table:
#     Start LBA      End LBA           Type
1     1              234441647         EE EFI Protective

Status: GPT partition of type "Unknown" found, will not touch this disk.
**Error: Not Found returned from gptsync.efi**

* Hit any key to continue * 
```

Regarding the GPT, partition 3 is ext3 Ubuntu and 4 is FAT32 Windows. Why aren't these being recognized anymore? How do I correct this GPT?

I'm fairly positive that if I could just get rEFIt to read my GPT correctly, then I could transfer that to the MBR and all would be well. Thoughts?

[COLOR="Red"]**Update:**[/color]
 I got the GRUB screen back by updating my version of rEFIt. See link [here]("http://refit.sourceforge.net/doc/c4s5_parted.html") about that. I still cannot get into Linux or Windows, as Ubuntu hangs at *Running local boot scripts (/etc/rc.local)* which I think has something to do with the fact that I was editing GRUB files on my Ubuntu partition (via the live CD) instead of just adding them to the boot sector. I don't think anything in /etc should have been changed but I could be wrong. Choosing Windows on the GRUB screen doesn't get me anywhere.

---

### Post by cyberdork33 on 2008-01-22
> **ronocdh said:**
> [COLOR=Red]**Update:**[/COLOR]
 I got the GRUB screen back by updating my version of rEFIt. See link [here]("http://refit.sourceforge.net/doc/c4s5_parted.html") about that. I still cannot get into Linux or Windows, as Ubuntu hangs at *Running local boot scripts (/etc/rc.local)* which I think has something to do with the fact that I was editing GRUB files on my Ubuntu partition (via the live CD) instead of just adding them to the boot sector. I don't think anything in /etc should have been changed but I could be wrong. Choosing Windows on the GRUB screen doesn't get me anywhere. Good note about that boot flag issue. I think you could have just booted and Ubuntu Live CD into Gparted and unmarked the boot flag though...


editing grub files from the cd shouldn't have really caused any problems.... the rc.local scripts aren't run until after the kernel is loaded anyway, which is a point afterwhich grub is no longer even involved. have you tried booting in safe mode, checking the filesystem?

---

### Post by ronocdh on 2008-01-23
> **cyberdork33 said:**
> Good note about that boot flag issue. I think you could have just booted and Ubuntu Live CD into Gparted and unmarked the boot flag though...
I thought I tried this. I booted into my GParted live CD and checked for flags and was surprised that I couldn't remove them&#8211;there simply were none to take off that partition.

> editing grub files from the cd shouldn't have really caused any problems.... the rc.local scripts aren't run until after the kernel is loaded anyway, which is a point afterwhich grub is no longer even involved. have you tried booting in safe mode, checking the filesystem?
I fsck'd a thousand times, always came up clean. I haven't quite resolved the boot scripts issue yet, but I'm back in Ubuntu. Apparently I'm [not alone]("http://ubuntuforums.org/showthread.php?t=670935") in that problem, and although for some users hitting enter gets past that stage, I had to open another terminal and login via text.

I didn't transcribe the error that I saw because I was so giddy it was working, but I remember a bit of it. First, I got an Xserver failure when I typed **startx** so I had to reconfigure my graphics driver (fglrx). When I tried to do this, it notified me that dpkg had previously been interrupted, and to resolve the problem I needed to manually run:
```
dpkg --reconfigure -a
```
Pretty sure that was the command. I did, all was while, configured the driver again using **aticonfig** and I'm back in business.

Windows is as yet unusable... the GRUB reinstalls somehow didn't detect it. I'm going to try again, with that, maybe run **fixmbr** from a Windows CD, then reinstall GRUB yet again. Anyway, hope this info helps someone at some point!

---

### Post by cyberdork33 on 2008-01-23
> **ronocdh said:**
> Windows is as yet unusable... the GRUB reinstalls somehow didn't detect it. I'm going to try again, with that, maybe run **fixmbr** from a Windows CD, then reinstall GRUB yet again. Anyway, hope this info helps someone at some point!

Just add a Windows Entry to your menu.lst:
```
title=Windows
rootnoverify (hd0,5)
makeactive
chainloader +1
```NOTE: change the (hd0,5) to the right partition for you!

The rc.local problem still sounds very strange... The thread you linked to was from a release candidate of gutsy. I could understand something like that before the final release, but it is strange that is happening now. 
Might check for bug reports: 
[https://bugs.launchpad.net/ubuntu/+bug/164244](https://bugs.launchpad.net/ubuntu/+bug/164244)
[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/184683](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/184683)
[https://bugs.launchpad.net/ubuntu/+bug/109299](https://bugs.launchpad.net/ubuntu/+bug/109299)

---

