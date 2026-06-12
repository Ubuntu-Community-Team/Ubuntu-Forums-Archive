---
title: "Ubuntu on External USB, Cannot boot once unplug restart computer"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by CuriousTeen on 2007-03-27
Hi,

Once I unplug/power off external USB Hard-disk (Ubuntu) , my system can't boot at all.

Any  solution?

Thanks

---

### Post by chewearn on 2007-03-27
Please boot up to ubuntu, post the output of:
```
sudo fdisk -l
```

---

### Post by CuriousTeen on 2007-03-27
> **AstalaVista said:**
> Please boot up to ubuntu, post the output of:
```
sudo fdisk -l
```

Boot to Ubuntu? I now using ubuntu os.

Is it mean to use terminal and paste your command 'sudo fdisk?

---

### Post by CuriousTeen on 2007-03-27
Hi

Here's the output: 

> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/sda2            5223        9728    36194445    f  W95 Ext'd (LBA)
/dev/sda5            5223        9728    36194413+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       15591   125234676    7  HPFS/NTFS
/dev/sdb2           15592       15722     1052257+  82  Linux swap / Solaris
/dev/sdb3           15723       17634    15358140   83  Linux
/dev/sdb4           17635       18271     5116702+  83  Linux
curiousteen@curiousteen-laptop:~$ 


tks

---

### Post by chewearn on 2007-03-27
Ok, I'm guessing that you have grub in the mbr of sda.  But since your /boot/grub is in sdb, when you unplug it, grub can't locate the files in /boot/grub (e.g. menu.lst).

I can think of two ways for you to solve this:

1. Install linux in hda
This is matter of choice; since you decided to install linux in sdb already, I reckoned you might not want to do this.

2. put grub in mbr of sdb
First, boot into ubuntu, open a terminal:
```
sudo grub
```At the grub prompt, just to be sure about the disk assignment:
```
find /boot/grub/stage1
```You should get something like (hd1,2).  Next, type in:
```
root (hd1)
```The number 1 in (hd1) should be the same as the number 1 in (hd1,2) you get in the previous command.  I.e. if you get (hd2,2), then it should be (hd2).  (I am try to be 100% sure the changes you will be making is correct) :)
Finally, to quit:
```
quit
```Next, you will need to restore the windows bootloader in sda; google "fdisk /fixmbr" if you are unsure.

Once this is done, you should be able to boot into Windows when the external drive is unplug (you might need to set your BIOS to boot from primary drive, if it complains).
Also, when you plug the external drive in, you might need to change the BIOS boot to the second drive.

It's a hassle to change BIOS boot order everytime, but it depends on how intelligent your BIOS is.

---

### Post by CuriousTeen on 2007-03-27
> **AstalaVista said:**
> 
Finally, to quit:
```
quit
```Next, you will need to restore the windows bootloader in sda; google "fdisk /fixmbr" if you are unsure.

Once this is done, you should be able to boot into Windows when the external drive is unplug (you might need to set your BIOS to boot from primary drive, if it complains).
Also, when you plug the external drive in, you might need to change the BIOS boot to the second drive.

It's a hassle to change BIOS boot order everytime, but it depends on how intelligent your BIOS is.

Once I type 'Quit' and enter:

```
curiousteen@curiousteen-laptop:~$ sudo grub
Password:
Probing devices to guess BIOS drives. This may take a long time.
curiousteen@curiousteen-laptop:~$ 
curiousteen@curiousteen-laptop:~$ 
```

I not sure on  sda; google "fdisk /fixmbr".

---

### Post by CuriousTeen on 2007-03-27
Don't work.

I restart Ubuntu, quick power-off my External USB HD whem I saw my computer boot to black screen.

After that, error code 21.

---

### Post by CuriousTeen on 2007-03-27
no one can help me?

---

### Post by confused57 on 2007-03-27
> **CuriousTeen said:**
> Don't work.

I restart Ubuntu, quick power-off my External USB HD whem I saw my computer boot to black screen.

After that, error code 21.
Did you get your internal Window's drive mbr restored?  If not, this guide may help you:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
You'll need to do this in order to boot your Window's drive with the external drive disconnected.

If you were able to get grub installed to your external drive mbr and get a grub menu at boot when booting first to your external drive, then you can try highlighting your Ubuntu entry, press "e", change root from (hd1,x) to (hd0,x), then press "b" to boot( the x in the entry means leave this as it already is).  This change is only temporary if it works & can be made permanent in your /boot/grub/menu.lst if it works.

If you're able to boot into Ubuntu, you might want to make a copy of the Super Grub Disk(500 kb download):
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
SGD can boot Windows or Linux and restore your mbr

---

### Post by CuriousTeen on 2007-03-28
> **confused57 said:**
> Did you get your internal Window's drive mbr restored?  If not, this guide may help you:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
You'll need to do this in order to boot your Window's drive with the external drive disconnected.


Thanks.

which title should I read in the link mentioned above?

---

### Post by CuriousTeen on 2007-03-28
I read this part that said hiddenmenu.

But I can't figure out how to do this.... where to open that window and type command?

[http://users.bigpond.net.au/hermanzone/p15.htm#hidethemenu](http://users.bigpond.net.au/hermanzone/p15.htm#hidethemenu)

---

### Post by chewearn on 2007-03-28
> **CuriousTeen said:**
> I read this part that said hiddenmenu.

But I can't figure out how to do this.... where to open that window and type command?

[http://users.bigpond.net.au/hermanzone/p15.htm#hidethemenu](http://users.bigpond.net.au/hermanzone/p15.htm#hidethemenu)


This part is talking about editing menu.lst
```
sudo gedit /boot/grub/menu.lst
```

---

### Post by CuriousTeen on 2007-03-28
[QUOTE=AstalaVista]This part is talking about editing menu.lst
Code:

sudo gedit /boot/grub/menu.lst
[/QUOTE]

Thanks but I restart but still don't work.

I couldn't figure which title to follow mbr restore.

All I can find is back up mbr restore... etc.

---

### Post by confused57 on 2007-03-28
> **CuriousTeen said:**
> Thanks but I restart but still don't work.

I couldn't figure which title to follow mbr restore.

All I can find is back up mbr restore... etc.
Here's the section you need to read to restore your Window's IPL code to your internal hard drive mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_XP_Recovery_Console](http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_XP_Recovery_Console)

The first method in the link involves booting up with your Window's install cd(not a recovery cd), press "r" for recovery & enter FIXMBR to reinstall to your mbr.

The second method involves going to bootdisk.com, downloading the Win98SE oem & making a boot floppy, then fdisk /mbr to repair your mbr.

If you're wanting to reinstall grub, you can use the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)


I would still highly recommend getting a copy of the Super Grub Disk:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by CuriousTeen on 2007-03-30
> **confused57 said:**
> Here's the section you need to read to restore your Window's IPL code to your internal hard drive mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_XP_Recovery_Console](http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_XP_Recovery_Console)

The first method in the link involves booting up with your Window's install cd(not a recovery cd), press "r" for recovery & enter FIXMBR to reinstall to your mbr.

The second method involves going to bootdisk.com, downloading the Win98SE oem & making a boot floppy, then fdisk /mbr to repair your mbr.

Thanks for your help.

I follow this method for WinXP, I boot-up WinXP Cd.

And a warning msg shown below:

[[img]http://upload7.postimage.org/455502/DSC00077.jpg[/img]](http://upload7.postimage.org/455502/photo_hosting.html)

is it safe?

---

### Post by confused57 on 2007-03-30
You might want to read this thread:
[http://ubuntuforums.org/showthread.php?t=190892](http://ubuntuforums.org/showthread.php?t=190892)

Since I've never actually had to do "fixmbr" myself, I can't say for sure if the warning is normal or not(I think it "might" be, but don't quote me on that)...you may want to search around in the forum for restoring mbr, if someone says this is just a routine warning or not...if I find something, I'll post back.

As you'll read in the thread I linked above, adrian15(the developer of the Super Grub Disk) mentions that  SGD can also restore your mbr.

Added:  Found this thread, seems it's just a disclaimer from MS:
[http://www.ubuntuforums.org/showthread.php?t=318308&highlight=uninstall+Ubuntu](http://www.ubuntuforums.org/showthread.php?t=318308&highlight=uninstall+Ubuntu)

---

### Post by bobplano on 2007-03-31
i'm having this same problem but i dont have an XP cd or a floppy drive. should i try supergrub? i dont quite get what it does, will it still work even though i dont know what happened to my windows boot files? i can still boot to windows and ubuntu but only when my external hd is plugged in

edit: i fixed the mbr and ill just do a clean install of ubuntu and put grub on the external drive

---

