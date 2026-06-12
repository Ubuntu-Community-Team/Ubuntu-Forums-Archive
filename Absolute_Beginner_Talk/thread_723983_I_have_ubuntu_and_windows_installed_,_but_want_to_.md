---
title: "I have ubuntu and windows installed , but want to re-install windows ...!"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by quecoder on 2008-03-14
hello , 
I have ubuntu installed on a separate partition and windows XP in partition C ... I want to re-install windows using the recovery CD shipped with my laptop .. it will format the drive C and re-install windows again ..... the dual boot will disappear of course ... 
Question is :
* Do I need to do any thing before re-installing windows or after ?
* what exactly should I do to to make the grub appear again ?

---

### Post by maniac_X on 2008-03-14
Grub is currently in control of your MBR. You want to fix that first. You can do this with your Windows CD by booting and going to the Recovery console.

Boot with the XP installation CD.

When prompted, press **R** to repair a Windows XP installation.

If repairing a host with multiple operating systems, select the appropriate one (XP) from the menu. If you have only one operating system, enter 1 to select it.

Enter the administrator password if prompted.

To fix the MBR, use the following command:

```
fixmbr
```


This assumes that your installation is on the C:\ drive. You will be presented with several scary warning lines the reading of which will make you want to say no. Microsoft is exceptionally vague regarding the conditions under which fixmbr can cause problems although they are clear about the consequences (losing all data on the hard drive), so use this at your own risk.

Type **y **and ENTER to fix the MBR.

Type exit to leave the recovery console and reboot.

Now just reboot the CD, delete all partitions and let WinXP do its thing by using the whole harddrive and you will be back to where you were before you installed Ubuntu.

---

### Post by quecoder on 2008-03-14
oh , but I do have other drives with data I need ..
and I didn't see such options in the windows CD ..it only asks me if I want to install windows again , and if yes , it will format the first drive ( C ) and install it again with utitlities my toshiba laptop needs to function properly //

** well , if I don't want to keep ubuntu after installation  , ( will install it again after I install windows ) .. what to do ?

---

### Post by erginemr on 2008-03-14
Assuming that you still want to dual-boot Windows with Ubuntu:

All above info is OK, but be careful not to have your Ubuntu partition wiped off by the Windows installer.

And when the installation is done, you will need to reinstall grub by following:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

or by using Super Grub Live CD:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by quecoder on 2008-03-14
I don't have such options in the recovery CD ,, it only can format C , reinstall windows after .

---

### Post by maniac_X on 2008-03-14
> **quecoder said:**
> 

** well , if I don't want to keep ubuntu after installation  , ( will install it again after I install windows ) .. what to do ?

It depends on "when" you want to reinstall Ubuntu again. 

If you want to reinstall Ubuntu right after you reinstall Windows, then just choose the C drive to install Windows on to and do as ***erginemr*** suggests and repair your Grub. 

If on the other hand you want to just forego Ubuntu for the immediate time, repair your MBR as I outlined above, install Windows to the C drive, and get a partitioning program such as [PartedMagic Live CD]("http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads")  to delete the linux partitions and grow your remaining partitions into the empty space.


Oh, and most important....backup your important data/files as a precautionary measure. Remember Murphy's Law. ;)

---

### Post by quecoder on 2008-03-14
what do you mean by fixing the MBR ? 
I can not do it using windows xp installtion CD ,, because my recovery CD doesn't have these options .it only can format C , reinstall windows after .

---

### Post by quecoder on 2008-03-14
I got this solution from some one ,
Re-install windos on drive C ( after formatting it ) ...remove ubnutu using live CD gparted .

the MBR will be overwritten by windows in this way..

can I follow this ?

---

### Post by sandysandy on 2008-03-14
please state again what do u wish to do.

if u want to just re-install windows, u can do so on windows partition itself leaving the ubuntu partition untouched. However, Back up important data.

the grub (in MBR) will go once windows is reinstalled. in the posts above links to restore grub have been provided. or u can use super grub disk to restore grub.

regards

---

### Post by kamitsukai on 2008-03-14
> **quecoder said:**
> I don't have such options in the recovery CD ,, it only can format C , reinstall windows after .

I think you will find that he doesent have a windows intall disc but in fact a restore disc which came with the pc?

[COLOR="Lime"]***Edit***[/COLOR]
Re-read your post as i just skimmed through it last time, i shouldn't think there is anything you need to do to grub as the disc will completley restore your whole drive to how it originally was, but could you explain your second question in more detail?

---

### Post by maniac_X on 2008-03-14
> **kamitsukai said:**
> I think you will find that he doesent have a windows intall disc but in fact a restore disc which came with the pc?

[COLOR="Lime"]***Edit***[/COLOR]
Re-read your post as i just skimmed through it last time, i shouldn't think there is anything you need to do to grub as the disc will completley restore your whole drive to how it originally was, but could you explain your second question in more detail?

I am thinking he has other partitions with data/music on them that he wants to keep in tact, therefore doing a complete install from the "recovery CD" might not be the option he is looking for because more than likely it will wipe out those partitions.

Overall, if the recovery CD is going to be a pain and not give any options, it's better to just back up the important data/music files and then let the recovery CD do it's thing and restore the data after the fact.

---

### Post by Duck2006 on 2008-03-14
You need to format your C: drive so you can recover your installation, try the live cd of gparted to format your drive to ntfs.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

