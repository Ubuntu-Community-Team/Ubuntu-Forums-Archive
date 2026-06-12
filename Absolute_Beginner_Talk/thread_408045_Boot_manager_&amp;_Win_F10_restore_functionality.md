---
title: "Boot manager &amp; Win F10 restore functionality"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by DigitalRanger on 2007-04-12
I have spent an entire night looking on the web for this, but I can't quite find what I need to answer my question (despite having found a lot of material about GRUB in the process).

I'm lining myself up to switch over to Ubuntu when Feisty is unleashed. I'm currently using a [Clevo M570A laptop]("http://www.clevo.com.tw/products/M570U.asp") (&#8220;[Xtreme CT]("http://www.bit-tech.net/hardware/2005/11/25/rock_extreme_ct/2.html")&#8221;, from [Rock Direct]("http://www.rockdirect.co.uk/")), which was bought with Win XP Home installed.

Ultimately, I want to [completely switch to Linux]("http://digitalranger.livejournal.com/142929.html#cutid1"), although in the meantime, (and because I've paid for it) I want to dual boot with XP.

This isn't a problem, I've dual booted windows with Linux before (Win95 and Mandrake, so a long time ago!).

The problem is that my laptop has one of these F10 restore partitions, which I see as a handy &#8220;last resort&#8221; feature, and I also thought it would come in useful if I wanted to sell the laptop at some point and restore it to &#8220;factory condition&#8221;.

I know that, in principal, I could set up a triple boot with GRUB, between Ubuntu, WinXP and WinXPRestore. Although I do not know what is required to trigger the restore software, and if this would damage the Ubuntu install or not. Also, I have from my laptop vendor, a program to restore the "F10" boot loader, although this would probably kill GRUB in the process, and I don't necessarily want to loose my Linux install just because I'm restoring a factory XP install.

Hence, what I want to know, is it possible to dual boot WinXP and Ubuntu, and still retain the F10 restore function so that I can restore XP to &#8220;factory condition&#8221; ?

Thanks for reading.

---

### Post by alexlex on 2007-04-14
yes it is possible but a little complicated if you wnat to retain that function **DO NOT** install grub on hda0 (or sda0 what ever the case) you want to install it on your linux partition ie.hda3. after doing this  you need to tell the windows boot loader to add linux to its options in the boot.ini system folder located on drive d: (your restore partition) there is a very helpful command line tool to use in windows called bootpart. please be aware you need to run this in windows cmd prompt as it will not run just by clicking on it........when you run bootpart it will list your partitions. in normal cases the first type83 partition will be your linux boot you will need its corresponding number. ie

1   type 28
2   type 28
3   type 83

when you have identified that partition you would type something like: bootpart 4 linux.inx
this will create a .inx file of your linux boot on which ever hard drive you have installed bootpart on.

then in you boot.ini file you would add a 3rd line to it it will be something like this.

d:\linux.ini="ubuntu"

this is what my boot.ini looks like  

[boot loader]

timeout=15

default=D:\linux.ini

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP" /fastdetect

D:\CMDCONS\BOOTSECT.DAT="Windows XP Recovery Console" /cmdcons

D:\linux.ini="Ubuntu Edgy"

then you would adjust your timeout to something like 15 sec before it auto boots into windows.
note that your default is the os it will auto boot to after 15 sec if no keys a pressed.
you may change this to whatever you want. furthermore to access the boot.ini you must set your folder options to show hidden folders and system folders.
also take not to the fact that even though your recov partition might show as D: it is normally your first partition on your hard drive.

if you have done this correctly when you boot you will see this:

Microsoft Windows XP
Microsoft Windows Recovery Partition
Ubuntu

i know this all sounds kinda hard but if you need any help feel free to send me a message. i will be more than willing to give you a walk through but i would need more detailed specs on your system.

ps...the reason you need boot part is because most computers bios will not read past the first 1024 cy. so you need to link the linux boot loader to the windows.

PPS. with the setup you have there is no point in booting to the recovery partition via the boot loader. if you do so you will get a command prompt. if you want the gui you must hit F10

alexlex

---

### Post by alexlex on 2007-04-14
as a side note consider revising your threads, alot of people wont bother if they have to read alot. keep it short and to the point. just a suggestion no offense. 

alexlex

---

### Post by DigitalRanger on 2007-04-16
I could do with some more guidance on this, so I'll just list some configuration information for my laptop and see what you make of it:

Restore partition, **D**:, is the first partition on the disk.
Windows partition, **C:**, is the second partition on the disk.

**D:** does not have a boot.ini file. It does however have an autorun.inf file (which I assume is for the restore software), which reads:

> [AUTORUN]
OPEN=Info.exe folder.htt 480 480

**C:** has a boot.ini file which reads:

> [boot loader]
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

Having ran bootpart I get the following read out (disks 1 & 2 are removable drives):

> Physical number of disk 0 : 508eb134
 0 : C:  type=b  (Win95 Fat32), size= 4016218 KB, Lba Pos=63
 1 : C:* type=7  (HPFS/NTFS), size= 93666982 KB, Lba Pos=8032500
Physical number of disk 1 : 1f6430b
 2 : D:  type=c  (Win95 Fat32 LBA), size= 93666951 KB, Lba Pos=63
 3 : D:  type=f  (Win95 XInt 13 extended), size= 199382715 KB, Lba Pos=187333965
 4 : D:  type=b   (Win95 Fat32), size= 199382683 KB, Lba Pos=187334028
Physical number of disk 2 : 0
 5 : E:* type=6  (BIGDOS Fat16), size= 509152 KB, Lba Pos=63

Thanks again for reading,
DR.

---

### Post by alexlex on 2007-04-18
> **DigitalRanger said:**
> I could do with some more guidance on this, so I'll just list some configuration information for my laptop and see what you make of it:

Restore partition, **D**:, is the first partition on the disk.
Windows partition, **C:**, is the second partition on the disk.

**D:** does not have a boot.ini file. It does however have an autorun.inf file (which I assume is for the restore software), which reads:



**C:** has a boot.ini file which reads:



Having ran bootpart I get the following read out (disks 1 & 2 are removable drives):



Thanks again for reading,
DR.

I think I have made it sound more complicated than it actually is... the key thing to remember is when you install ubuntu's Grub MBR manager to make sure you install it on your linux boot partition that you will create and not. you will need to shrink your partitions to make room for ubuntu do not install it un D: (hd0) as you do not have enough room. given your config. you will probalby install grub on hd3 but it is hard to say. but don't worry as long as you have a windows disk if you accendently mess up your MBR it can be fixed by putting the cd in and hitting r for repair when the screen comes up and you would get dos like cmd line and just type "fixmb" and the windows boot will be fixed. after you have installed linux you will want to run bootpart again to see which is your linux partition.

---

### Post by alexlex on 2007-04-18
do your self another favor..... go ahead and print out your boot.ini file . this could prove very helpful incase the mbr gets messed up...

---

### Post by DigitalRanger on 2007-04-18
Thanks for that.

One other question - Does the Ubuntu LiveCD install provide a choice for where to install GRUB, or should I use the Alternate CD ?

---

### Post by DigitalRanger on 2007-04-19
> **DigitalRanger said:**
> Thanks for that.

One other question - Does the Ubuntu LiveCD install provide a choice for where to install GRUB, or should I use the Alternate CD ?

Found out for myself now - [Fiesty Release notes]("http://releases.ubuntu.com/7.04/").

> **Alternate install CD**

The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:

    * creating pre-configured OEM systems;
    * setting up automated deployments;
    * upgrading from older installations without network access;
    * LVM and/or RAID partitioning;
    ***[COLOR="Red"] installing GRUB to a location other than the Master Boot Record;[/COLOR]**
    * installs on systems with less than about 192MB of RAM.

---

