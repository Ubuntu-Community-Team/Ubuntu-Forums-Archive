---
title: "rEFIt &quot;F&quot; Up!"
date: 2009-03-08
forum: Apple Hardware Users
---

### Post by WA_Garrett on 2009-03-08
I'm triple booting on my Macbook (Tiger, Hardy, XP) using rEFIt. Recently I had to reinstall Ubuntu on my ext3 partition. After I reinstalled Ubuntu, rEFIt Registered 2 Linux partitions on it (rather than one) (I did not create any new partitions when I reinstalled Ubuntu, I just installed over the existing installation)

My partitioning Scheme is like this 
200 mb for EFI
92 GB for OS X
11 GB for Ubuntu
9 GB for WIN

Previously when booting, rEFIt had 3 boot options, 1st the Apple Logo (For OS X), 2nd Tux (For my Linux Distro) and 3rd Windows (For Windows). Now it looks like this. 1st the Apple Logo (For OS X, boots normally by the way), 2nd Tux (Non Functional) and 3rd another Tux (Brings Up BIOS type boot option selector) and 4th Windows (Brings Up same BIOS type boot option selector). So the first Tux Doesn't work the 2nd tux and windows logo both bring up the same BIOS type boot option selector, where you have to use the up down arrow keys to choose between windows or Linux. 

Now all 3 of my operating systems seem to be working fine by the way. But this whole extra tux thing is just annoying me to insanity, considering on how I didn't create any new partitions either. 

I'm wondering if anyone knows how I could tell rEFIt that I only have 3 OSes instead of 4. Now I have everything working fine on all my OSes so I would appreciate it if any ideas didn't require the re-installation of any OSes. I would appreciate any ideas/advice about this situation though. 

Thank you to whoever reads this.

---

### Post by Rog-Mahal on 2009-03-08
I haven't had this problem myself, but I've heard of it. I think it might be related to your new install of ubuntu messing up the partition table for refit. One thing you could try would be to go into the refit menu and sync partition tables. Hopefully that will solve it. If not there are other options like using a live cd to manually reinstall grub, but that's beyond my knowledge.

---

### Post by inphektion on 2009-03-08
maybe you installed grub to mbr the second time around?

---

### Post by WA_Garrett on 2009-03-09
> **Rog-Mahal said:**
> I haven't had this problem myself, but I've heard of it. I think it might be related to your new install of ubuntu messing up the partition table for refit. One thing you could try would be to go into the refit menu and sync partition tables. Hopefully that will solve it. If not there are other options like using a live cd to manually reinstall grub, but that's beyond my knowledge.

The first thing I tried when this happened was I went into rEFIt's Partitioning tool to see if I could update the MBR partition table but it listed my 4 partitions and said the tables were in sync. I then booted up in my live CD and followed the instructions at this page [http://ubuntuforums.org/showpost.php?p=3303463&postcount=11]("http://ubuntuforums.org/showpost.php?p=3303463&postcount=11") to update grub. 

At this point I don't know of anything else I could do.

---

### Post by WA_Garrett on 2009-03-09
> **inphektion said:**
> maybe you installed grub to mbr the second time around?

If I did, how would I know and how would I just make sure grub is installed once?

---

### Post by cyberdork33 on 2009-03-09
> **inphektion said:**
> maybe you installed grub to mbr the second time around?
I am pretty sure this is exactly what happened.

You need to reinstall grub (that bios-style boot selector, which is actually the application that loads the linux kernel) to the Ubuntu partition first:
[http://ubuntuforums.org/showpost.php?p=3303463&postcount=11](http://ubuntuforums.org/showpost.php?p=3303463&postcount=11)

Then boot up your Windows CD into the recovery console and use the FIXMBR command to replace the bootcode in the MBR with the Windows bootloader.

---

### Post by WA_Garrett on 2009-03-09
> **cyberdork33 said:**
> I am pretty sure this is exactly what happened.

You need to reinstall grub (that bios-style boot selector, which is actually the application that loads the linux kernel) to the Ubuntu partition first:
[http://ubuntuforums.org/showpost.php?p=3303463&postcount=11](http://ubuntuforums.org/showpost.php?p=3303463&postcount=11)

Then boot up your Windows CD into the recovery console and use the FIXMBR command to replace the bootcode in the MBR with the Windows bootloader.

I'm uneasy about letting a windows disk take as much control over my booting prospects as asking it to fix my Master Boot Record. Mostly because windows was never designed to triple boot with 2 other operating systems on a mac. I also talked to my friend who knows a little bit about this and he said that doing that might just make it so that I could only boot in windows. Is there any way to change the MBR on the Linux or Mac side?

---

### Post by cyberdork33 on 2009-03-09
> **WA_Garrett said:**
> I'm uneasy about letting a windows disk take as much control over my booting prospects as asking it to fix my Master Boot Record. Mostly because windows was never designed to triple boot with 2 other operating systems on a mac. I also talked to my friend who knows a little bit about this and he said that doing that might just make it so that I could only boot in windows. Is there any way to change the MBR on the Linux or Mac side?Well, since neither OSX or Ubuntu need the MBR boot code to startup, and several people have done just what I said to do and it works, it is pretty safe. I don't think your friend understands the differences between the Mac system and the normal PC system.

When you install windows, it installs it's bootloader in the MBR. Normally, when installing Ubuntu, you want GRUB to take it's place, and allow it load windows and Ubuntu... On the mac, you want refit to handle redirecting control instead of grub so that you don't have to go through two menus to get to windows.

---

### Post by WA_Garrett on 2009-03-09
> **cyberdork33 said:**
> Well, since neither OSX or Ubuntu need the MBR boot code to startup, and several people have done just what I said to do and it works, it is pretty safe. I don't think your friend understands the differences between the Mac system and the normal PC system.

When you install windows, it installs it's bootloader in the MBR. Normally, when installing Ubuntu, you want GRUB to take it's place, and allow it load windows and Ubuntu... On the mac, you want refit to handle redirecting control instead of grub so that you don't have to go through two menus to get to windows.

I'll try it this weekend when I won't need my computer for anything important and I'll have time to mess with it. Thanks.

---

### Post by WA_Garrett on 2009-03-17
> **cyberdork33 said:**
> Well, since neither OSX or Ubuntu need the MBR boot code to startup, and several people have done just what I said to do and it works, it is pretty safe. I don't think your friend understands the differences between the Mac system and the normal PC system.

When you install windows, it installs it's bootloader in the MBR. Normally, when installing Ubuntu, you want GRUB to take it's place, and allow it load windows and Ubuntu... On the mac, you want refit to handle redirecting control instead of grub so that you don't have to go through two menus to get to windows.

This just might be me, but this process seems like a pretty serious thing, I booted the windows CD and applied the FIXMBR command. Then the following text came up

> This computer appears to have a non-standard or invalid Master Boot Record.

FIXMBR may damage your partition tables if you proceed.

This could cause all the partitions on the current hard disk to become inaccessible.

If you are not having problems accessing your dive do not continue.

Are you sure you want to write a new MBR?

I'm wondering if that warning is supposed to come up and if it does or doesn't matter in this case. I'm not having any trouble booting in any of my operating systems or accessing any drives(I just have that extra inoperable Tux pop up in rEFIt) so I'm abit worried about running this command. 

Also, not knowing much about MBRs, I'm curious to know how this will help rEFIt realize I only have 3 boot-able partitions rather than 4 (which I don't have).

Thanks.

---

### Post by cyberdork33 on 2009-03-17
> **WA_Garrett said:**
>  I'm wondering if that warning is supposed to come up and if it does or doesn't matter in this case. I'm not having any trouble booting in any of my operating systems or accessing any drives(I just have that extra inoperable Tux pop up in rEFIt) so I'm abit worried about running this command. I believe the warning is normal. 

> Also, not knowing much about MBRs, I'm curious to know how this will help rEFIt realize I only have 3 boot-able partitions rather than 4 (which I don't have).
you have more than one tux, because you have a linux bootloader in more than one location. (One in the MBR, the other on the Ubuntu partition.) Windows' bootloader can only be installed to the MBR (and on a PC, you replace it with GRUB and use grub to chainload windows). On the Mac, the EFI system is capable of booting the MBR or any other partition directly (while a PC's BIOS can usually only executable the bootloader from the MBR). Since Grub does not have to be in the MBR, you can put windows' bootloader back there, overwriting the installation of GRUB in the MBR. Then you will have 3 icons in rEFIt. One for OSX (bootloader is an efi executable on your OSX partition), one for windows (in the MBR), and one for Linux (on the Linux partition).

---

### Post by IsmailBhai on 2009-03-17
this might help you

[http://hydtech.wordpress.com/2009/01/26/dual-triple-quad-boot-a-macbook-with-mac-os-x-ubuntu-linux-windows-xp-and-windows-vista/](http://hydtech.wordpress.com/2009/01/26/dual-triple-quad-boot-a-macbook-with-mac-os-x-ubuntu-linux-windows-xp-and-windows-vista/)

---

### Post by WA_Garrett on 2009-03-17
> **cyberdork33 said:**
> I believe the warning is normal. 


Hey, I executed FIXMBR and it worked. I just have 3 Icons in rEFIt now and I can still boot from Ubuntu, OS X, and XP. Thanks Alot. 

There's still one thing though, when I boot onto the Linux partition it still brings up the Grub boot loader but atleast now when I boot onto Windows it now goes directly to Windows.

---

### Post by WA_Garrett on 2009-03-17
> **IsmailBhai said:**
> this might help you

[http://hydtech.wordpress.com/2009/01/26/dual-triple-quad-boot-a-macbook-with-mac-os-x-ubuntu-linux-windows-xp-and-windows-vista/](http://hydtech.wordpress.com/2009/01/26/dual-triple-quad-boot-a-macbook-with-mac-os-x-ubuntu-linux-windows-xp-and-windows-vista/)

Boy, I wish I knew about that tutorial when I was just getting started with triple booting. But thanks for it, I bet it might come in handy in the future sometime. :D

---

### Post by cyberdork33 on 2009-03-18
> **WA_Garrett said:**
>  There's still one thing though, when I boot onto the Linux partition it still brings up the Grub boot loader but atleast now when I boot onto Windows it now goes directly to Windows.That's normal. You have to use GRUB (or some other bootloader like lilo) to load a Linux kernel. You can edit the grub config file to shorten the delay to boot into the default entry, and turn on "hidden menu" which prompts you to hit esc to see the menu at all.

---

