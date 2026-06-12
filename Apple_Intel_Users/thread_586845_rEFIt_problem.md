---
title: "rEFIt problem"
date: 2007-10-22
forum: Apple Intel Users
---

### Post by Pan007 on 2007-10-22
I am about to install 7.10 on my macbook Pro. :-)

So far i have OS X(Tiger) and WinXP installed. I have a partition ready for Ubuntu 7.10

diskutil list in terminal gives this information:

pan007-95c4b683:~ Pan007$ diskutil list
/dev/disk0
   #:                   type name               size      identifier
   0:  GUID_partition_scheme                    *149.1 GB disk0
   1:                    EFI                    200.0 MB  disk0s1
   2:              Apple_HFS Macintosh HD       60.0 GB   disk0s2
   3:   Microsoft Basic Data                    39.5 GB   disk0s3
   4:     Microsoft Reserved                    49.4 GB   disk0s4

disk0s3 show up as MicrosoftBasic Data??

This is my question.

When i now restart, rEFIt show up 3 os´s to choose from.
disk0s3 is still empty, and when i select the 2´nd choice (Boot legacy from HD, grey icon) it boot´s into my WinXP. This also happend if i select 3´rd choice of cource. 
Is this normal and will the grey icon go away when i install ubuntu? If not, how can i get rid of his grey icon under the rEFIt menu?

One more thing...is it normal that one can´t get into Recovery console? I do get a blue screen when i try to do that. (I have the WinXP cd inserted, select WinXP from HD, and then recovery console)

---

### Post by cyberdork33 on 2007-10-22
I think that the grey icon is rEFIt seeing a partition there that is marked as bootable, but there is nothing on it, and either option defaults to the MBR bootcode where the Windows bootloader is located.

When you install ubuntu, the grey icon should change to a Tux icon for linux (rEFIt will actually be able to detect the OS type at that point).

Your partitioning scheme looks good though. Keep in mind that if you do not want to have to use grub to boot windows AND linux, then you need to specify to install grub to the 3rd partition instead of the MBR. (On the Live cd, click the "Advanced" button after you have done all the system configuration in the installer).

I don't know what to tell you about the BSoD when starting the Recovery Console.

---

### Post by Pan007 on 2007-10-22
Thanks...
Will try and install Ubuntu later tonight...

Weird this Recovery console problem, but maybe it´s because of the fact that this is a Apple machine not a PC....something about drivers perhaps.

---

### Post by Pan007 on 2007-10-22
OK i have now finished with the installation of Ubuntu 7.10 on my macbook pro. :)

First question:

When rebooting the machine 1 still get 4 boot icons in rEFIt.
1 for OS X (Apple icon)
1 for Boot Legacy OS from (Grey icon with HD) when choosing this I boot up in WinXP
1 for Linux from partition 3 (Penguin icon)
1 for Windows from partition 4 (Windows icon)

How can i remove the grey icon?

Second question:

Grub is installed in the linux partition (disk0s3)
Is grub supposed to be text only? When booting into Linux, grub start with boring txt info :( 
How can i get rid of the Windows XP choice in Grub again. (I don't remember.)

Information only:

diskutil list shows:

pan007-95c4b683:~ Pan007$ diskutil list
/dev/disk0
#: type name size identifier
0: GUID_partition_scheme *149.1 GB disk0
1: EFI 200.0 MB disk0s1
2: Apple_HFS Macintosh HD 60.0 GB disk0s2
3: Microsoft Basic Data 37.3 GB disk0s3
4: Microsoft Reserved 49.4 GB disk0s4
5: Linux Swap 2.2GB disk0s5

---

### Post by cyberdork33 on 2007-10-22
i don't know why you are getting that grey icon still. do you have an external drive plugged in? I know that mine does that when it sees a USB flash drive.


Grub is text only, yes, but you can 'theme' it...
[http://ubuntuforums.org/showthread.php?t=30341](http://ubuntuforums.org/showthread.php?t=30341)

If you want to rremove the Windows choice from grub, you can remove the lines in your /boot/grub/menu.lst file

---

