---
title: "want to switch from all ubuntu to a dual boot"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by swishthetoad on 2008-01-03
i'm running gutsy and I can't get the roaming wireless to run properly. 

so now i want to switch my hard drive from just ubuntu to ubuntu/vista in order to pick up the internet. 

and how would i do that?

i tried booting up the vista cd and it won't partition my hard drive...says it's the wrong format and refuses to format it. 

what can i do?

---

### Post by SteveHillier on 2008-01-03
First remember that when you do get to install Windows again it will delete anything to do with Linux.
Second, I had a similar problem when I had two HDDs partitioned as GPRT rather than MBR. As these were new disks I was lost until I remembers I had put them into a FreeNAS box I was testing and had partitioned them there.  My solution was put these disks back into the FreeNAS box and delete the partitions.  
I suspect you will need to use some none windows partition editor to remove the current partitions and re-allow MBR which WIndows can see.  Others may point you in the right direction for this.
Lots of luck

---

### Post by p_quarles on 2008-01-03
> **swishthetoad said:**
> i'm running gutsy and I can't get the roaming wireless to run properly. 

so now i want to switch my hard drive from just ubuntu to ubuntu/vista in order to pick up the internet. 

and how would i do that?

i tried booting up the vista cd and it won't partition my hard drive...says it's the wrong format and refuses to format it. 

what can i do?
Use the [Gparted LiveCD]("http://gparted-livecd.tuxfamily.org/") to free up some space. Leave it unformatted, and the Vista recovery disk should do the rest.

---

### Post by swishthetoad on 2008-01-03
i tried running the cd and it didn't recognize any devices...after taking about 20 minutes to load...

---

### Post by p_quarles on 2008-01-03
Hmm. That's really weird. Did you check the MD5 on the copy you downloaded? If not, you can do this easily by cd'ing to the directory you downloaded it to, and running this:
```
md5sum gparted-livecd(*restoffilename)*
```
If you downloaded the latest version, it should return this:
```
ea35e53c1f4d8ce0001f123b2b682a5e
```

---

### Post by hyper_ch on 2008-01-03
Before you do any repartitioning:

**MAKE A BACKUP!**

Just to be sure ;)

You can use the Ubuntu DesktopCD to re-partition and resize your drive but you'll need to unmount your partitions first. The DesktopCD will auto-mount ext3 and swap partition.

---

### Post by threetimes on 2008-01-03
I have the same problem, but i used PertedMagic to format/move/resize/etc my partitions.
The result:
```
(parted) print                                                            

Disk /dev/hda: 80,0GB
Sector size (logical/phisical): 512B/512B
Partition table: msdos


Number  Begin   End     Size     Type     File system  Flags
 1      32,3kB  2147MB  2147MB   primary  linux-swap          <- Swap
 2      2147MB  34,4GB  32,2GB   primary  ext2         boot   <- Ubuntu
 3      34,4GB  61,2GB  26,8GB   primary  ntfs                <- Reserved for Vista
 4      61,2GB  80,0GB  18,8GB   primary  ntfs                <- Reserved for XP

```(translated)
Vista sees all partitions, but it says: "Windows is unable to find a system volume that meets its criteria for installation"...

---

### Post by hyper_ch on 2008-01-03
leave partition 3 unpartitioned... meaning delete that partition and leave it as empty space. Maybe that will trigger the vista partitioning manager.

---

### Post by rcsarver on 2008-01-03
in my experience, ive found it faster to install windows, then install ubuntu. ubuntu automagically configures the boot menu.

---

### Post by Sbarton on 2008-01-03
If you have'nt done so yet, have a look here it might give you info you need.
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

regards

---

### Post by LowSky on 2008-01-03
I try to read your old thread about your bad connection. It seems that you may have a bad port on your laptop. and you say that the internet doesn't work with Vista, So how would Vista make it work if it didn't before?

if ts a driver issue please type this command into terminal and post the results
```
lspci
```

we can look up what model ethernet card your using and make sure we can get the correct drivers.

---

### Post by threetimes on 2008-01-03
> **hyper_ch said:**
> leave partition 3 unpartitioned... meaning delete that partition and leave it as empty space. Maybe that will trigger the vista partitioning manager.
Doesn't work, I get the same error
> **Sbarton said:**
> If you have'nt done so yet, have a look here it might give you info you need.
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

regards
You sent the wrong link, is must be: [http://apcmag.com/5045/how_to_dual_boot_vista_with_linux](http://apcmag.com/5045/how_to_dual_boot_vista_with_linux) (Ubuntu first)

I get to this screen: [http://apcmag.com/system/files/images/ubuntu_vista_05.preview.jpg](http://apcmag.com/system/files/images/ubuntu_vista_05.preview.jpg) but when i select my 25GB empty space (or ntfs partition before I deleted it) is displays the error on the bottom of that screen...

---

### Post by Sbarton on 2008-01-03
Please look at the link I posted ... it says ..5046 not 5045
regards

---

### Post by threetimes on 2008-01-03
> **Sbarton said:**
> Please look at the link I posted ... it says ..5046 not 5045
regardsI have ubuntu right now installed, and I DON'T want to remove it.
Your link asumes vista is already installed as only os, and my link says ubuntu is already installed as only os.
If I remove ubuntu, and all partitions on my harddrive, install vista, and install ubuntu at the end, your link is right, but i am not going to remove my current ubuntu installation (even if that means no vista).

---

### Post by Sbarton on 2008-01-03
OK! I understand threetimes, I am sure there is a answer somewhere that will help you. Regrettably I do not have that sorry! I understand your dilemma now!  Good luck with that. It would be nice to know the answer, so that others can benefit from that. Please post your solution!
regards and best wishes.

---

### Post by threetimes on 2008-01-04
Sometimes (also on winxp) when I have a memory card or usb device plugged in on a certain port, after a while it says i unplugged the device or removed my memory card.
Maybe it is a problem with the internal usb connection. The page below says that could be the problem.
[http://support.microsoft.com/kb/927520](http://support.microsoft.com/kb/927520)
> CAUSE
This problem may occur for one of the following reasons:
...
&#8226;	A data cable in the computer is loose, or another hardware issue has occurred.
...
Or maybe my harddrive is not compatible with vista (WD's site says it is NOT vista certified)...
hdparm -I /dev/hda says:
```
/dev/hda:

ATA device, with non-removable media
        Model Number:       WDC WD800BB-00JHC0                      
        Serial Number:      WD-WCAM9H706539
        Firmware Revision:  05.01C05
```

**Edit:** There are no drivers on WD's site(?), so I can't put them on a usb stick to load them during vista's setup...

---

### Post by threetimes on 2008-01-04
I've got it: my hard drive is NOT compatible with vista, but my pc says:
[IMG]http://img.microsoft.com/library/media/1033/windowsvista/images/wv_home_img_capable2.png[/IMG]
Does that mean that HP must buy me a new, vista compatible, harddrive, or do I have a real problem.

---

### Post by hyper_ch on 2008-01-04
> **threetimes said:**
> I've got it: my hard drive is NOT compatible with vista
You're joking? That can't be true... VISTA should support IDE and SATA... what's there about being compatible or not... I know XP doesn't support SATA natively... can you make a screenshot?

---

### Post by threetimes on 2008-01-04
[http://westerndigital.com/en/products/productcatalog.asp](http://westerndigital.com/en/products/productcatalog.asp) or see attachment

---

### Post by hyper_ch on 2008-01-04
if it's not VISTA certified you can't install VISTA on it? If so, I'd say f*** *** VISTA ;)

---

### Post by threetimes on 2008-01-04
> **hyper_ch said:**
> if it's not VISTA certified you can't install VISTA on it? If so, I'd say f*** *** VISTA ;)
I agree :P

---

### Post by threetimes on 2008-01-04
HP's customer service says the hdd is vista capable, and says i should contact M$:mad:

---

### Post by LowSky on 2008-01-04
why do you have a partition for XP if it isn't installed? Also you have 4 partitions on your hard drive already. When windows installs itself it makes 2 for god knows why. One is NTFS and the other is always sized 8MB and is unallocated.
If I were you I would delete what ever partions you made that you dont need create a new extended partion and create new partions within that for Vista

---

### Post by threetimes on 2008-01-04
I'll try that in about an hour from now

**Edit:** it doesn't work

---

### Post by Sbarton on 2008-01-04
Hmmm! thats interesting about HDD not being compatible with Vista. I am surprised! Anyway maybe that confirms in someway that it is better to have Windows installed first for dual boot systems. If vista had not installed on that drive firstly then  dual boot would not have been possible , at least with vista.   XP probably!  If you have a second drive available try the windows first and Ubuntu after.
regards

---

### Post by threetimes on 2008-01-04
I don't think vista will install when ubuntu is not installed, but i'll try XP. This means not that I am stopped with trying vista, it just means i swiched from Ubuntu>Vista>XP to Ubuntu>XP>Vista!

---

### Post by threetimes on 2008-01-05
XP doesn't work ](*,)

When i copied the files and rebooted from hd, the windows bootloader (I think), says it can't read the drive.
So I reinstalled grub from the PartedMagic cd, and re-made my ntfs partition.
The situation now:```
parted) print                                                            

Disk /dev/hda: 80,0GB
Sector size (logical/phisical): 512B/512B
Partition table: msdos


Number  Begin   End     Size     Type     File system  Flags
 1      32,3kB  2147MB  2147MB   primair  linux-swap             <- swap
 2      2147MB  26,3GB  24,2GB   primair  ext2                   <- ubuntu
 3      26,3GB  53,2GB  26,8GB   primair  fat32            boot  <- data
 4      53,2GB  80,0GB  26,8GB   primair  ntfs                   <- XP
```Don't ask me why 'data' is boot, but when i select "disk 1 part 4" frum grub's menu on the cd, it throws that error.

---

### Post by threetimes on 2008-01-05
Strange...
Sudddenly XP works...:)

---

### Post by threetimes on 2008-01-05
Strange...
Sudddenly XP stops working...:(

I replaced MS' bootloader with grub, and now when i select windows, i get ```
Starting up...
_
``` and does nothing, no cpu usage and no hdd activity.

The installation of win xp was fine, and after that it rebooted and continued the installation (asks for location settings, name, etc...). I nedded to get some info from my ubuntu installation, so i decided to stop xp's setup and get that data. I restored grub from the partedmagic cd, and boted from ubuntu and printed the info and added windows to menu.lst. I also tried a splashimage in grub, and it doesn't work,
see the attachment for the splashimage error and the menu.lst.

---

### Post by threetimes on 2008-01-07
Strange...
Sudddenly XP works again:)...
 
I reinstalled XP, and it works, including grub!
 
However, I still got the splashimage problem.

---

