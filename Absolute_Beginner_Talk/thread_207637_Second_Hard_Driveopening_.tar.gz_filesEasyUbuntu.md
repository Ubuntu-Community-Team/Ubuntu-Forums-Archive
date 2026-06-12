---
title: "Second Hard Drive/opening .tar.gz files/EasyUbuntu"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by SpunkyMonkey on 2006-07-02
Sorry about the title. I just couldn't think of anything that would exactly fit my post.

I have three questions. I am new to Kubuntu and to Linux in general, but I am getting the hang of it. I have three problems that have me stumped, however.

1. I cannot seem to properly extract .tar.gz files. Every time I try it tells me that the extraction operation failed, and only extracts some of the files. If I try to extract via Konsole, it doesn't give me any errors, but, once again, it only extracts some of the files. Because of this I haven't been able to install any software.

2. I have two hard drives. One is a 40GB drive, and the other is a 120GB drive. I installed Kubuntu on the 40GB drive (hda1), but it will not show the 120GB drive (hdb1 I'm guessing?). Because of this, I cannot save to the 120GB hard drive and I'm restricted to a mere 40GB. Is there a way that I can get Kubuntu to recognize my 120GB hard drive?

3. I found a handy dandy little application on Digg.com called [EasyUbuntu](http://web.informbank.com/articles/technology/perfect-linux-desktop.htm). I ran it and installed everything that came with it without reading anything first. It's a bad habit I carried over from Mac OS X. My brother later informed me that some of the things that I installed from EasyUbuntu are actaully illegal to use on Kubuntu, but neither of us know exactly what. Is this true? And if so, what are they and how can I get rid of them? The last thing that I need is to get myself into trouble. From the site:
> What is EasyUbuntu able to install:

Multimedia:

    * Enhance the video player by replacing totem-gstreamer with totem-xine [color=blue](I installed this)[/color]
    * Codecs for playing MP3s [color=blue](I installed this)[/color]
    * All the video codecs you need - w32codecs [color=blue](I installed this)[/color]
    * All you need to read encrypted and commercial DVDs [color=blue](I installed this)[/color]
    * Support for playing MIDI files [color=blue](I installed this)[/color]

Web:
Flash and Java plugins for Firefox will be installed. [color=blue](I installed these)[/color]

Archives:
Can't find a .tar.gz version of the file you have on your old CDs? Now you'll be able to open RAR, ACE and 7-zip formats, too. [color=blue](I installed hese)[/color]

VoIP:
Skype will be installed for you. By the way, Skype released a new beta version of Skype for Linux yesterday. It was a long wait. EasyUbuntu offers you the OpenWengo application, too. [color=blue](I installed Skype, but not OpenWengo)[/color]

System:

    * Installation of Microsoft's Fonts (Arial, Verdana, Comic Sans...) and more nice fonts [color=blue](I installed this)[/color]
    * Installation of the official Nvidia or ATI drivers for your graphics card [color=blue](I installed the ATI drivers)[/color]

Thanks for your help.

---

### Post by givré on 2006-07-02
1: tar -xzvf in a terminal should work, if not, your archive is corrupted. this command is one of the base of all distro, which is use by a lot of apps, so yes it works.
But if you are new to linux, installing apps from tarball is not the recommanded way. You should search in synaptic or in apps/remove apps before.

2: Let see your /etc/fstab

---

### Post by SpunkyMonkey on 2006-07-02
/etc/fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by someusernoob on 2006-07-02
[QUOTE=SpunkyMonkey]/etc/fstab:[/QUOTE]
What file system does your hdb1 use? the 120Gig disk.

---

### Post by SpunkyMonkey on 2006-07-02
Both disks are on NTFS.

---

### Post by givré on 2006-07-02
Try that [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

EDIT : and to be sure of the name of the partition(s),  sudo fdisk -l in a terminal

---

### Post by someusernoob on 2006-07-02
[QUOTE=SpunkyMonkey]Both disks are on NTFS.[/QUOTE]
Then i got bad news for you. Linux doesnt have NTFS write support. Although there is support for it, I wouldnt recommend it since its still unreliable. It can break down your disk.

But you can automount the partition, so you can read the data which is allready on there.

[http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

Choose only the folder you want to have it mounted in and the right disk off course. This speaks for itself i guess. Change gedit with kate or kedit.

---

### Post by SpunkyMonkey on 2006-07-02
Hmm, well I do know that hda1 used to be NTFS while I had Windows installed. I didn't see an option to change that anywhere when I installed Kubuntu so I just assumed that it's still NTFS. How can I check be be certain?

---

### Post by givré on 2006-07-02
sudo fdisk -l in a terminal
And if you want to mount ntfs partition, see that [http://ubuntuforums.org/showthread.php?t=142481](http://ubuntuforums.org/showthread.php?t=142481)
Yes it's experimental, but if you don't use your ntfs partition intensivly, it's quite safe, i use it.

EDIT: An interesting link to understand why it's safe, even if it will not work all the time [http://wiki.linux-ntfs.org/doku.php?id=ntfsmount](http://wiki.linux-ntfs.org/doku.php?id=ntfsmount)
But don't install it from this link, use the ubuntu howto, it's more easy

EDIT2: But using fat32 or ext3 to share files between win and linux is always a better idea

---

### Post by someusernoob on 2006-07-02
[QUOTE=SpunkyMonkey]Hmm, well I do know that hda1 used to be NTFS while I had Windows installed. I didn't see an option to change that anywhere when I installed Kubuntu so I just assumed that it's still NTFS. How can I check be be certain?[/QUOTE]
In your fstab its showing hda1 is using ext3. If you installad Kubuntu over the Windows installation, the installer did the format to ext3 for you. ext3 is the standard filesystem Kubuntu/Ubuntu/Anybuntu uses.

---

### Post by SpunkyMonkey on 2006-07-02
EDIT: Nevermind. Thanks someusernoob. I did install Kubuntu over Windows.

Okay I did "sudo fdisk -l" and got:
> Disk /dev/hda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4798    38539903+  83  Linux
/dev/hda2            4799        5005     1662727+   5  Extended
/dev/hda5            4799        5005     1662696   82  Linux swap / Solaris

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14945   120045681    7  HPFS/NTFS
So from that I got that my 120GB hard drive (hdb1) is NTFS. How about hda1 though (my 40GB that I have Kubuntu installed on)?

---

### Post by someusernoob on 2006-07-02
hda1 works just fine. Dont change anything on that, in the worst scenario you cant mount your root file system, so you cant startup Ubuntu anymore.

And since hda1 is ext3 you can just read and write to it (store files in your /home directory etc.)

The only "problem" you have now is the 120GB drive. Do you want to let it be read only, do you want to try the program the other guy linked to so you can also write to NTFS, or do you want to go the safe way and format it to another filesystem so you can just safely read and write to it? In the last case you have to backup the files you do not want to loose.

---

And about your 3rd question. Read this: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by SpunkyMonkey on 2006-07-02
The safe way sounds great. There's nothing on there worth backing up, so I just want to be able to format it so that I can safely read and write to it.

Thanks for the link regarding my third question.

---

### Post by someusernoob on 2006-07-02
You can do 2 things then. Boot from the live (install) cd to work with the Partition Editor (dont know where it is on KDE), or install, and correct me if im wrong: sudo apt-get install qtparted   and format (maybe create partitions) the drive with this application.

But the 2nd option should work without a problem since hdb isn't mounted. Make sure you select hdb when you edit anything. 

Most logical choice would be to format it to ext3. You could consider fat32 so when you want to go back to Windows the disk is ready for use. But is has a file size limit of 4GB. 

After you did that i'll give you instructions (if you need) how to automount it and make it ready for use when you boot into Kubuntu.

---

### Post by SpunkyMonkey on 2006-07-03
I found the partition editor in the Utilities folder when running off the CD, and now my 120GB drive is on ext3. Thanks a LOT for all of your guys' help. All three questions have been answered. :)

---

### Post by someusernoob on 2006-07-03
Nice to hear that :)

Did you also manage to get the disk automount on startup? That would be easy if you want to use the disk a lot. There should appear an icon on the desktop if it's mounted. Im not into the details of this because im not using KDE but Gnome, so cant help you out on that, about the icon i mean.

---

### Post by SpunkyMonkey on 2006-07-04
Well the icon doesn't show up on the desktop, but I can still access it just fine.

---

