---
title: "Installing and booting mac os x on a single boot install of ubuntu 10.10"
date: 2011-01-23
forum: Apple Hardware Users
---

### Post by zackmacataq on 2011-01-23
hardware and speculations-

white macbook 4,1
os x 10.5.8
120gb hard drive
1gb ram
2.1ghz intel core 2 duo 

the issue-

I  decided to try and dual boot Ubuntu because there were some programs i  wanted to run on my computer that os x couldnt (.exe). so i successfully  installed ubuntu onto my macbook but in the process, deleted my mac  partition and mac os x all together, but thank god i backed all my files  up in time machine to an external hard drive. i didnt intentionally  want to single boot ubuntu to my macbook and have done extensive  research for solutions. im probably not as fluent in computers as some  people on this forum but im not illiterate, more on the amateur side. 

solutions ive tried-

ive  been working for about 3 to 4 days trying to reinstall mac os x through  a dvd and a 4gb flash drive. everytime i boot through the dvd or flash  drive, it will not give me a mac boot option. it will show an icon with a  hard drive with an arrow under it named windows. when i click on the  icon, it boots up only ubuntu. I did partition it for mac settings using  gparted and disk utilitiy. maybe my settings are off? I cannot remember  what i set everything to as ive rebooted so many times. I do know that  im missing the file types: hfs, hfs+ , reiser 4, and ufs when im  partitioning the disk for its file system setting. ive read through  nearly every relative article on the internet for a detailed guide to  properly installing mac os x and most have been vague. so now im at the  source, id really appreciate the replies for this thread to help me out.  id really like to be able to dual-boot os x and ubuntu once i get os x  back up, but at this point ubuntu is expendable to me. please and thank  you everyone

---

### Post by zackmacataq on 2011-01-23
at this point im almost considering getting a new computer, but if theres a way to salvage this computer and get mac os x back on id love to hear any suggestions. with all the research ive done, i havnt found anyone with a successful attempt at this.

---

### Post by srs5694 on 2011-01-23
First, what is your goal: to dual-boot OS X and Ubuntu or to replace Ubuntu with OS X? Both are possible, but the latter is eaiser.

Second, please boot into Ubuntu, launch a Terminal window, and type the following two commands:

```

sudo parted /dev/sda print
sudo fdisk -lu

```

Post the results here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings to preserve the formatting and make the output legible. Note that these commands won't do anything to fix your issue; they're diagnostic and will provide us with information on how your disk is currently laid out.

It *is* possible to get OS X re-installed on your computer. Precisely how to do this depends on your goal and how the disk is currently laid out.

---

### Post by zackmacataq on 2011-01-23
```

ubuntu@ubuntu:~$ sudo parted /dev/sda print
Model: ATA FUJITSU MHY2120B (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End  Size  Type  File system  Flags

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002256f

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 4022 MB, 4022337024 bytes
124 heads, 62 sectors/track, 1021 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00074285

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62     7849447     3924693   ee  GPT
ubuntu@ubuntu:~$ 

```

my goal is to get mac os x back on my computer, ubuntu is great but id rather have just have os x.

---

### Post by srs5694 on 2011-01-23
It looks like /dev/sda is your hard disk, with no partitions but set up with a Master Boot Record (MBR; aka "msdos") partition table, which is not what Macs use natively. It also looks like you're booting Linux from a 4 GB disk (a USB flash drive, I presume) on /dev/sdb, which uses the Mac's native GUID Partition Table (GPT). If this is incorrect, please post corrections before proceeding.

The simplest way to get yourself back on track is this:


[list=1]
[*]Boot Linux from the USB drive.
[*]Launch GParted by typing "sudo gparted" in a Terminal or by locating its entry in your menus.
[*]Ensure that you're working on the right disk by selecting it from the list at the top-right of the window. (It should be "/dev/sda (120 GiB)" or something similar -- the exact size may be different.) When selected, you should see no partitions defined.
[*]In GParted, select Device -> Create Partition Table. This should bring up a dialog box.
[*]In the dialog box, click the Advanced selector. This will open a new option, "Select new partition table type"
[*]Select a partition table type of "gpt"
[*]Click Apply. The operation should take just a moment or two.
[*]Quit from GParted.
[*]Shut down the computer.
[*]Remove the USB flash drive.
[*]Start the computer and insert your OS X disk in the drive. It should now boot. If it doesn't, reboot and hold down the Option key to get to a boot menu that will let you boot the disc.
[*]The OS X installer should start. When you get to the screen that asks what disk to install to, it will probably show no options. That's OK....
[*]Go up to the menus and locate an entry for Disk Utility. (I don't recall the exact menu it's in.) Launch it.
[*]Use Disk Utility to set up your OS X partition(s) in whatever way you like.
[*]Quit from Disk Utility.
[*]You should now be able to select a partition on which to install OS X and proceed with a normal OS X installation.
[/list]


This is a little vague around the OS X installation since I don't want to start the installer on my own Mac just to check this out, but it shouldn't be too difficult to find what you need.

If you decide you want to dual-boot OS X and Linux, you can do so; just set aside some space for Linux when you partition the disk and then follow any of several guides on the topic (such as [the one I wrote.](http://www.rodsbooks.com/ubuntu-efi/index.html))

If you have more problems, post back again with more details.

---

### Post by zackmacataq on 2011-01-26
srs5694

although im still having issues installing, thank you for your help. the flash drive does not contain the ubuntu install files, i used a cd-rw to install ubuntu from. i dont really believe it makes that much of a difference though, its most likely my os x install disc. i had to burn it from another (windows)computer cause im in colombia (south america) and apple products are virtually non-existant here. ill be back in the states in a few days where i can get a real one, but its been almost a week without os x and naturally want to fix this as soon as possible. ive booted my mac with the burnt mac os x numerous times. 

heres how it goes:

after partitioning my hard drive in ubuntu, i restart the computer with the dvd in the drive. then, the apple styled mouse cursor shows up like mac os x is about to boot. finally, after a few minutes an icon flashes on and off with a folder that has a question mark on it. 

ive deducted some possibilities that either a file cant be found that boots the files correctly, or that the os x file on the dvd is the wrong file type.

---

### Post by srs5694 on 2011-01-27
If the disk was copied on a Windows machine, then it might well be unbootable. Apple does peculiar things with the format of its OS installation discs. I've just checked my OS X 10.6 install disc, and it seems to be partitioned like a hard disk, but using the Apple Partition Map (APM) system, which Apple used on its 680x0- and PowerPC-based computers. The twist is that one partition contains an ISO-9660 filesystem with Boot Camp files for Windows, and the other contains an HFS+ partition with the OS X install files. The disc is written in such a way that Windows (and Linux) treats it like a plain ISO-9660 disc.

Thus, depending on how the disc was copied, the copy might only contain the ISO-9660 files, not the HFS+ files, and it would be useless as an OS X install disc.

---

### Post by zackmacataq on 2011-01-27
i see, the format i downloaded it in was a file type called .cdr if i remember correctly. it was the only one that would fit onto a single layer dvd (no dual-layer dvds here :/ ). i guess at this point in time ill have to wait until i get back in the states to buy the disc or i could also get a dual-layer dvd but probably wont, its not worth the hassle. rather pay $50 for an official copy. so, i will follow up with results in a few days

---

### Post by srs5694 on 2011-01-27
FWIW, a single copy of OS X 10.6 is US$30, while a "family pack" (good for installing on up to five computers) is $50. A "box set" that's bundled with iLife, iWork, and a few other things is $130. If you've just got the one Mac, the single license for $30 is probably the way to go, unless you need the software bundled with the box set.

---

### Post by zackmacataq on 2011-01-27
hmmm...  i know were mostly on topic of apple products rather than ubuntu, but my backed up files and programs were on os x 10.5.8, you think time machine will bring my files back through snow leopard if i upgraded it? would it matter?

---

### Post by zackmacataq on 2011-02-11
**update** i have returned back into the states, purchased snow leopard, and successfully booted and backed up all my files. i am considering dual booting ubuntu now that i have os x back up and running and have the disc. for any users that might have the same problem as i had, $30 will get you back up and running as srs5694 had stated.

for new ubuntu users installing on a mac, the best thing you could do is make sure you back everything up with time machine before booting. i dont remember exactly how i erased the os x partition, but its a mistake that can be replicated if not careful. so on my end, lesson learned and thank you srs5694 for your help

---

### Post by staxxthedan on 2011-04-20
> **srs5694 said:**
> It looks like /dev/sda is your hard disk, with no partitions but set up with a Master Boot Record (MBR; aka "msdos") partition table, which is not what Macs use natively. It also looks like you're booting Linux from a 4 GB disk (a USB flash drive, I presume) on /dev/sdb, which uses the Mac's native GUID Partition Table (GPT). If this is incorrect, please post corrections before proceeding.

The simplest way to get yourself back on track is this:


[LIST=1]
[*]Boot Linux from the USB drive.
[*]Launch GParted by typing "sudo gparted" in a Terminal or by locating its entry in your menus.
[*]Ensure that you're working on the right disk by selecting it from the list at the top-right of the window. (It should be "/dev/sda (120 GiB)" or something similar -- the exact size may be different.) When selected, you should see no partitions defined.
[*]In GParted, select Device -> Create Partition Table. This should bring up a dialog box.
[*]In the dialog box, click the Advanced selector. This will open a new option, "Select new partition table type"
[*]Select a partition table type of "gpt"
[*]Click Apply. The operation should take just a moment or two.
[*]Quit from GParted.
[*]Shut down the computer.
[*]Remove the USB flash drive.
[*]Start the computer and insert your OS X disk in the drive. It should now boot. If it doesn't, reboot and hold down the Option key to get to a boot menu that will let you boot the disc.
[*]The OS X installer should start. When you get to the screen that asks what disk to install to, it will probably show no options. That's OK....
[*]Go up to the menus and locate an entry for Disk Utility. (I don't recall the exact menu it's in.) Launch it.
[*]Use Disk Utility to set up your OS X partition(s) in whatever way you like.
[*]Quit from Disk Utility.
[*]You should now be able to select a partition on which to install OS X and proceed with a normal OS X installation.
[/LIST]


This is a little vague around the OS X installation since I don't want to start the installer on my own Mac just to check this out, but it shouldn't be too difficult to find what you need.

If you decide you want to dual-boot OS X and Linux, you can do so; just set aside some space for Linux when you partition the disk and then follow any of several guides on the topic (such as [the one I wrote.]("http://www.rodsbooks.com/ubuntu-efi/index.html"))

If you have more problems, post back again with more details.

With this approach (Dual Boot linux & OS X), do you have bluetooth and internal wifi card working? what hardware issues do you have?

---

### Post by srs5694 on 2011-04-20
I have no need for either Bluetooth or Wi-Fi on my Mac Mini, so I've not bothered to try to configure either of them. Both do seem to be detected, though. I have no hardware issues with my machine under Linux; however, Apple's hardware varies a lot from model to model. My Mac Mini is a first-generation Intel-based computer, and other models are very different from it. Some of them do seem to cause problems, judging by posts here and elsewhere.

---

### Post by MESA62606 on 2011-04-20
This is a lil off tha map but Im in desperate need ov sum assistance..kinda with tha same issue. Im trying 2 run Ubuntu 10.10 alongside Mac os x 10.5.8. Im NOT a genius on mac. !st one & i LOVE it. My problem is sumtimes , i kno jus enuf about sumthen 2 get me n TROUBLE! N e help is much obliged & much LUV

---

### Post by MESA62606 on 2011-04-20
:popcorn:

---

