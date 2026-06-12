---
title: "Multibooting on a Macbook?"
date: 2007-09-01
forum: Apple Intel Users
---

### Post by PaulFXH on 2007-09-01
Just started dual booting Ubuntu Feisty on my new Macbook yesterday thanks to some vital assistance from this forum.
Most things are working very well but still a few things I'm puzzled about.
For example, if I type 
```
diskutil list
```
in an OS X terminal, I get this output
```
/dev/disk0
   #:                   type name               size      identifier
   0:  GUID_partition_scheme                    *149.1 GB disk0
   1:                    EFI                    200.0 MB  disk0s1
   2:              Apple_HFS Mac HD             113.0 GB  disk0s2
   3:   Microsoft Basic Data                    9.0 GB    disk0s3
   4:   Microsoft Basic Data                    6.7 GB    disk0s4
   5:             Linux Swap                    2.0 GB    disk0s5

```
This seems to indicate I have five partitions (3, 4 and 5 are /, /home and swap for Ubuntu). But are they logical or primary partitions or what?
This is important to me as I would like to add another two Linux OSes (would share Swap and /home -- so two more partitions needed). So, what is the limit on number of partitions here in OS X?

Secondly, when I choose the Linux (Tux) iccn in rEFIt, I get a mesage about Grub loading and then
> Press 'Esc' to enter the new menu
However, no amount of Esc pressing brings up a Grub menu and the default option is always booted.
I imagine that were it possible to add some further Linux OSes, the only way they would be accessible would be through the Grub menu.
But, if that menu is not available???
Thanks for any comments
Paul

---

### Post by russo.mic on 2007-09-01
well, the ESC thing could easily be because of the dead keyboard bug in mac book firmware.  Basiclly, after you use rEFIt to select which OS to boot into, it stops responding to keyboard stimuli until the OS keyboard driver is loaded.

---

### Post by pxwpxw on 2007-09-01
**PaulFXH**

I have looked at the same problem for multiple linux systems,
and from a few tests (on one MacBook) conclude:
 
Use refit to select separate grub first  stages,  installed on available MBR primary boot sectors (but not on the MasterBootSector).

Then it depends on disposal of the (unused at present) EFI primary and the MacosX partition also on a primary, at present only leaving 2 for Linux.

Refit installation requires a running Macosx, but can then function on a non-primary hfs+ partition (I have it on p6), or even a USB stick.

The Partition utility (gptsync) in Refit will give a picture of the MBR and GPT tables. It will also offer to bring the MBR into line with the GPT. May not be a good idea, be carefull with it. The ubuntu gptsync will align the 2 without asking.

The keyboard problem is not permanent, you can win occasionally, and there are various tricks (external keyboard, holding down keys etc).

---

### Post by PaulFXH on 2007-09-01
Thanks for the replies.
Over about 8-10 reboots of the Macbook that I've done today, I find that the Esc key DOES actually function about half the time and then gives access to the Grub boot menu.
However, I wonder why it doesn't just go straight to the menu as it has done on every other system that I've ever seen. Does anybody know if this feature is configurable?

So, if the Grub menu can be made available during the boot (e.g. hitting the rEFIt Linux icon and being brought to the Grub menu), then it should be a piece of cake to boot multiple Linux OSes provided that partitions are available for them to be installed.

Please be aware that I am extremely new to OS X and I am still unclear about the partition availability situation. I presume that no more than four primary partitions are allowed on any one disk, but what about logical partitions?
Is what pxwpxw refers to as a "non-primary hfs+ partition" equivalent to a logical partition? If so, where's the extended partition?
As right now I have five partitions (EFI, OS X, Ubuntu /, Ubuntu /home and Ubuntu swap) at least two of them have to be logical partitions (unless there's something major i don't know about partitioning in OS X -- which is by no means impossible:))
However, where did these logicals come from as I am not aware that I purposely created them?
Also, pxwpxw refers to p6 which suggests again some logical partitions?

I can probably condense this rambling post to just one question:
1) How many more partitions can I create on my Macbook internal HD given that I already have five?

Thanks
Paul

---

### Post by pxwpxw on 2007-09-02
**PaulFXH**

1. Menu question:

Easy, see /boot/grub/menu.lst

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmen

2. Partitions question:

This is my understanding of the GPT/MBR compatibily mode, 
and partition availability.

The GPT view of the disk can have as many partitions as you want, just using Linear Base Addressing. If the Macosx installation was started from an empty disk, using the Apple partitioner (no need for bootcamp resizing) , you could choose a GPT or MBR or some other system, but only GPT if you want to install MacosX. You could make as many partitions as required, initially, but it will be a GPT (or GUID) partitioning system.
This is what you have now. 

 The apple Macosx install also sets up an EFI partition and a DOS MBR partitining system, mirror version, which has the 4 primaries limit, and cant see beyond 4. I think the lowest 4 partitins are considered MBR primaries, but not created in the GPT as such.

This limits the choice of MBR boot partition for windows or the grub/lilo linux boot loaders, but when grub is started, it can then load linux kernels from any partition, so you can install multiple linux roots on any GPT partition, but you can only install grub stage1 on the MBR primaries.

The 2 table situation should be a bit clearer if you use the refit Partition icon to show both the MBR and GPT table views.

 It also possible to run Macosx from a DOS MBR partition, (but not to install directly there). I dont know where that leaves refit.

 I expect it is also possible to install Macosx on any of the GPT partitions, i.e. beyond the 4 primaries. This is what I have done previusly in the non-intel Apple PPC (G5,G4,and earlier) for macosx with the hfs+ filesystem, and multiple linux or data partitions. There is no requirement to install Macosx on any particular partition that I know of.

However, all sorts of constraints arise when Windows gets involved.

So, you may be able to create more GPT partitions using the macosx "diskutil" , or from linux using "parted" or gparted.
It is not an MBR limitation. The choice of method needs some more advice, can be hazardous.

Sorry if thats a bit rough, hope it makes sense.

---

### Post by PaulFXH on 2007-09-02
@pxwpxw
Thanks for your reply.

OK, as you suggested it was very simple to get the Grub menu to appear on bootup. However, once again, the Macbook keyboard keys don't always work even when the menu is there..
So, it's two steps forward, one step back -- but it's still progess:)

Can't say that I yet understand very much about partitioning a Macbook HD, but, from what you wrote, I don't feel discouraged to have a go to install at least one further Linux OS (on an additional partition) on my Macbook some time this week.
Certainly the three partitions I created (/, /home and swap) are all there and apparently functioning (from /etc/mtab and "free" command). So, these in addition to the OS X and EFI partitions make a total of five.
In addition, I'm in the happy position that I have nothing really important on this machine up to now, so even if things get totally messed up I will have lost very little and possibly gained a lot of experience.:grin:

---

### Post by pxwpxw on 2007-09-02
I think you can install another linux anywhere it will let you, but dont install the grub bootloader for it, just edit another item in your existing grub menu to boot the new root as well.

---

### Post by cyberdork33 on 2007-09-02
You are going to have the grub keyboard bug until Apple fixes the firmware most likely. There isn't anything that can be done.

Any bootable legacy partition has to be one of the first 4 (to be recognized as "primary"). If you install another distro, it will not likely be bootable. However, home, swap, and even your OSX partition can be after 4. There are no "extended" or "logical" partitions on a GPT system.

---

### Post by PaulFXH on 2007-09-03
@cyberdork33
Thanks for that interesting explanation.
However, when you say
> If you install another distro, it will not likely be bootable
I would be almost certain it can be made bootable. 
Given that I already have a bootable Ubuntu / partition with Grub, it should just be a matter of booting the vmlinuz and initrd.img of the "new" OS from the bootable Ubuntu / and then switching to the new OS's "real" root on the non-bootable partition.
I have done this quite a few times in getting Linux OSes to boot from non-bootable external drives and it "almost always" works.

---

### Post by pxwpxw on 2007-09-03
I agree that it is grub stage1 that needs to be on a primary, but then grub is capable of loadiing kernels from anywhere in the LBA system, similar to a straight PC MBR system.

You should not need to copy the kernel images to the grub partition.

This can be checked by running grub command line and doing a bit of "0> root (hd ... " exploring.

Suggest also check that /boot/grub/device.map is in good order

Edit: nearby thread has related issue
[http://ubuntuforums.org/showthread.php?t=541108](http://ubuntuforums.org/showthread.php?t=541108)

---

### Post by cyberdork33 on 2007-09-03
> **PaulFXH said:**
> @cyberdork33
Thanks for that interesting explanation.
However, when you say

I would be almost certain it can be made bootable. 
Given that I already have a bootable Ubuntu / partition with Grub, it should just be a matter of booting the vmlinuz and initrd.img of the "new" OS from the bootable Ubuntu / and then switching to the new OS's "real" root on the non-bootable partition.
I have done this quite a few times in getting Linux OSes to boot from non-bootable external drives and it "almost always" works.

Yes this is correct, thus the original partition is the bootable one still. It is an issue with Apple EFI and its emulated BIOS, not Grub.

---

