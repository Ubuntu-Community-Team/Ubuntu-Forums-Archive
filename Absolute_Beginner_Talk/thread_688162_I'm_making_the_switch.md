---
title: "I'm making the switch"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by anathema415 on 2008-02-05
I've been using Ubuntu as my Primary OS for all of two weeks now on a dual boot setup with Windows Vista. I've learned a lot and love Ubuntu. The only program I was going back to Vista for was my nntp reader (Newsleecher). I couldn't find a suitable replacement for Linux. Tonight I decided to try out Wine and got Grabit working flawlessly with it so I have no use for Windows anymore. All my hardware is compatible with Linux so I want to make the switch completely.

I have my Vista recovery discs burnt and I'm going to keep my 8 gig recovery partition for now, as a last resort. 

I also have Gparted both as an installed program and as a bootable disc. I want to delete  my Windows partition and add it to my linux partition. I just want to make sure that I can just delete the Windows Partition and add it onto this partition. The bootloader isn't on the C drive is it? Is it as simple as I'm hoping it is?

Thanks,

James

---

### Post by stchman on 2008-02-05
> **anathema415 said:**
> I've been using Ubuntu as my Primary OS for all of two weeks now on a dual boot setup with Windows Vista. I've learned a lot and love Ubuntu. The only program I was going back to Vista for was my nntp reader (Newsleecher). I couldn't find a suitable replacement for Linux. Tonight I decided to try out Wine and got Grabit working flawlessly with it so I have no use for Windows anymore. All my hardware is compatible with Linux so I want to make the switch completely.

I have my Vista recovery discs burnt and I'm going to keep my 8 gig recovery partition for now, as a last resort. 

I also have Gparted both as an installed program and as a bootable disc. I want to delete  my Windows partition and add it to my linux partition. I just want to make sure that I can just delete the Windows Partition and add it onto this partition. The bootloader isn't on the C drive is it? Is it as simple as I'm hoping it is?

Thanks,

James

If you have enough room you can just keep dual booting.  I have XP around for the occasional game I play.

---

### Post by anathema415 on 2008-02-05
Maybe.

The only game I play is EVE, and it has a Linux client which has given me no problems. Maybe just downsize the partition to gain more space on this partition?

---

### Post by hyper_ch on 2008-02-05
My main reason for keeping XP on a 30gb partition is Fantasy Grounds... it requires DX and couldn't run it yet in Ubuntu and neither in a VM...

---

### Post by jaytek13 on 2008-02-05
Assuming you installed Ubuntu after you installed Windows, I'm not sure you would simply be able to add the space to the Ubuntu partition. If you have a hard disk, and you have sectors 1-3 dedicated to windows, 4-6 dedicated to ubuntu, deleted the windows partition wouldn't result in appending the extra space to the back of the ubuntu partition since it is logically stored before the ubuntu partition. 

If you wanted to proceed with this, you may be able to add the space as an extra volume, so the former windows partition would act as a second hard drive, but don't quote me on this.

Really if you wanted to wipe Windows off your drive it might be best to just back up your home folder to a cd or something and reinstall Ubuntu completely using the entire drive.

---

### Post by anathema415 on 2008-02-05
> **jaytek13 said:**
> Assuming you installed Ubuntu after you installed Windows, I'm not sure you would simply be able to add the space to the Ubuntu partition. If you have a hard disk, and you have sectors 1-3 dedicated to windows, 4-6 dedicated to ubuntu, deleted the windows partition wouldn't result in appending the extra space to the back of the ubuntu partition since it is logically stored before the ubuntu partition. 

If you wanted to proceed with this, you may be able to add the space as an extra volume, so the former windows partition would act as a second hard drive, but don't quote me on this.

Really if you wanted to wipe Windows off your drive it might be best to just back up your home folder to a cd or something and reinstall Ubuntu completely using the entire drive.

If that's the case would backing up my home folder and copying it on a new install put all the programs I've installed on the system? And my settings?

Maybe your first suggestion of just wiping the win partition and formatting it to ext3 is my best bet.

---

### Post by jaytek13 on 2008-02-05
> **anathema415 said:**
> If that's the case would backing up my home folder and copying it on a new install put all the programs I've installed on the system? And my settings?

Maybe your first suggestion of just wiping the win partition and formatting it to ext3 is my best bet.

It would keep your settings but wouldn't include any of the programs you've installed.

---

### Post by candtalan on 2008-02-05
> **anathema415 said:**
> The only program I was going back to Vista for was my nntp reader (Newsleecher). I couldn't find a suitable replacement for Linux
Welcome!
I find Thunderbird is quite good for basic news things, although I notice newsleecher has some good features.
> 
I also have Gparted both as an installed program and as a bootable disc. I want to delete  my Windows partition and add it to my linux partition. I just want to make sure that I can just delete the Windows Partition and add it onto this partition. The bootloader isn't on the C drive is it? Is it as simple as I'm hoping it is?
Deleting a partition is not the simplest thing becauseI think the other remaining partitions will get re named, causing you some complication. It is easiest to reformat the windows partition, without changing the partition boundaries. If it is ntfs now, you could reformat to ntfs. Or choose ext3. If the windows partition is included in your ubuntu file /etc/fstab then you will need to comment out (use #) the line containing it and consider editing it to be suitable for an ext3 file system on that partition. fstab enables the partition to be mounted automatically and you can use it as a data or backup or whatever suits you. Best to comment out first, to avoid complications maybe.

Grub comments:
I believe the boot process begins by the bios using the hard drive master boot record which then redirects to the boot loader. After a dual boot installation the boot loader is in the ubuntu partition, so ubuntu will boot as long as you have not actually got rid of the ex-windows partition. The boot loader is usually grub. It will be expecting to find the boot files (I guess) on the first hard drive (grub knows it as hd '0') and the second partition (grub sees this as partition '1'). Note grub counts begin at zero, not one.
good luck

---

### Post by dark_harmonics on 2008-02-05
I agree with the above poster. Resizing partitions is dangerous. Its safer for your system to just wipe the partition if you want to rid yourself of your Microsoft infection. You should back up any documents and files you need before you do anything with partitions though. Call me paranoid up front but then when my tweaking screws something up, I still have my data in the end.

---

### Post by txHarleyMan on 2008-02-05
Backup your personal data files, use gParted to redo your partitions and wipe away windows.  Then install Ubuntu fresh.

I installed XP inside a VM ( VirtualBox ) as a guest only because I need it in order to connect to where I work.  Works great.

---

### Post by stoodleysnow on 2008-02-05
You can use AptOnCD to transfer your installed programs. :-)
Worked for me.

---

### Post by anathema415 on 2008-02-05
So I just didn't feel like dealing with partitions anymore and wiped my hard drive. I am now Windows free! It feels pretty darn good! :popcorn:

---

### Post by steveneddy on 2008-02-05
Keep dual booting. You have a fall back in case something drastic happens, like you break Ubuntu messing around with Compiz-Fusion and nVidia graphic drivers and xorg.conf.

But none of us have ever done anything like that before. 8-[

---

