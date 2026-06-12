---
title: "accessing windows partitions"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by u04f061 on 2006-05-27
in the beginning (one weak before) i was not sure that i'll use ubuntu as an operating syatem.so i made my pc dual boot ,preffering windows over ubuntu.so i gave two partitions of my hard disk to windows and only one to ubuntu.now that seems too small for me.unfortunately i can't format my windows just because of matlab 7.0 and orcad capture .these are softwares for electrical engineers.

now i want to access my those drives using ubuntu and data on those drives.
how can i do that.
if it possible please demonstrate clearly through valid commands
thnx

---

### Post by aysiu on 2006-05-27
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Personatech on 2006-05-27
Which version of Ubuntu are you running?  I'm running Dapper RC (6.06) and it accesses my NTFS primary partition just fine (at least it shows it on the desktop - I've never had to read or write data to it).

If you're running Breezy (5.10) then perhaps all you'll have to do is wait a week then upgrade!

---

### Post by aysiu on 2006-05-27
[QUOTE=Personatech]
If you're running Breezy (5.10) then perhaps all you'll have to do is wait a week then upgrade![/QUOTE] Or follow the instructions I linked to. They're not difficult.

---

### Post by jgoguen on 2006-05-27
Well first I need to know, is your Windows partition NTFS or FAT32?  If it's NTFS, you'll only have read-only access, thanks to MS being idiots as usual :)

To enable NTFS read-only support, first find the device WinXP is on.
```
sudo fdisk -l
``` This will bring up a list of all partitions.  One of them will have NTFS in the last column.  Take the device name in the first column of that row, you'll need it later.  If one of them says FAT in the last column (or FAT32 or something similar) you have a FAT partition and can have read-write access.

Now, open /etc/fstab
```
sudo gedit /etc/fstab
``` and add the following line to the end:
```
/dev/hda1     /winxp     ntfs     utf8,users,ro,posix=1,umask=0222,uid=yourusername     0     0
``` 
If instead you have FAT, use this line:
```
/dev/hda1     /winxp     vfat     utf8,users,rw,uid=yourusername     0     0
``` Replace /dev/hda1 with the device found above, /winxp with the full path to where you want it mounted (probably in your home folder), and yourusername with your Ubuntu username.  Finally, mount the partition:
```
sudo mount /winxp
``` Again, replace /winxp with the path to where you want it mounted.  Nautilus will (should) open the folder.

Now, having said you only have read-only access to NTFS...there *are* ways of getting read-write access, but don't try it unless you're willing to turn your NTFS partition into a useless mess.

---

### Post by u04f061 on 2006-05-27
[QUOTE=jgoguen]Well first I need to know, is your Windows partition NTFS or FAT32?  If it's NTFS, you'll only have read-only access, thanks to MS being idiots as usual :)

To enable NTFS read-only support, first find the device WinXP is on.
```
sudo fdisk -l
``` This will bring up a list of all partitions.  One of them will have NTFS in the last column.  Take the device name in the first column of that row, you'll need it later.  If one of them says FAT in the last column (or FAT32 or something similar) you have a FAT partition and can have read-write access.

Now, open /etc/fstab
```
sudo gedit /etc/fstab
``` and add the following line to the end:
```
/dev/hda1     /winxp     ntfs     utf8,users,ro,posix=1,umask=0222,uid=yourusername     0     0
``` 
If instead you have FAT, use this line:
```
/dev/hda1     /winxp     vfat     utf8,users,rw,uid=yourusername     0     0
``` Replace /dev/hda1 with the device found above, /winxp with the full path to where you want it mounted (probably in your home folder), and yourusername with your Ubuntu username.  Finally, mount the partition:
```
sudo mount /winxp
``` Again, replace /winxp with the path to where you want it mounted.  Nautilus will (should) open the folder.

Now, having said you only have read-only access to NTFS...there *are* ways of getting read-write access, but don't try it unless you're willing to turn your NTFS partition into a useless mess.[/QUOTE]


i have two partitions for windows.
1-fat32 in which my data is stored
2-ntfs in which widows os is installed

i am using windows 2000 with service ppack 2

the link above  which was given by aysiu says unmount.

i can't understand the term.what does it mean?will it erase all my data?
should i be able to access it through windows as well or after unmounting it will be a part of ubuntu space only?

i am not taking any action of instructions on the site as well as above  commands written by nice fellow  bcoz i am not sure about my data.
plz tell me of this so that i may take a step

---

### Post by aysiu on 2006-05-27
[QUOTE=u04f061]
the link above  which was given by aysiu says unmount.

i can't understand the term.what does it mean?will it erase all my data?
should i be able to access it through windows as well or after unmounting it will be a part of ubuntu space only?[/QUOTE] A mounted partition is one that is in use. If you mount a partition in Ubuntu, it will be mounted to a folder, and its contents will appear in that folder as if it *is* that folder... except that it's not a folder--it's a partition. It only *appears* to be a folder.

It's sort of like a **shortcut** in Windows or an **alias** in Mac.

When you click on a shortcut to a folder, it goes straight to the contents of that folder as if it the icon you clicked *was* the folder--but it's not.

Does that make sense to you? Right now, your Windows partition may be mounted (but not with the correct permissions) or it may not be mounted. The unmount command just makes sure we're starting from square one either way. That way, when we finally do issue the ```
sudo mount -a
``` command, we won't get back an error saying the partition is already mounted.

**Edit**: Maybe this screenshot will help explain a little better.

---

### Post by u04f061 on 2006-05-27
[QUOTE=aysiu]A mounted partition is one that is in use. If you mount a partition in Ubuntu, it will be mounted to a folder, and its contents will appear in that folder as if it *is* that folder... except that it's not a folder--it's a partition. It only *appears* to be a folder.

It's sort of like a **shortcut** in Windows or an **alias** in Mac.

When you click on a shortcut to a folder, it goes straight to the contents of that folder as if it the icon you clicked *was* the folder--but it's not.

Does that make sense to you? Right now, your Windows partition may be mounted (but not with the correct permissions) or it may not be mounted. The unmount command just makes sure we're starting from square one either way. That way, when we finally do issue the ```
sudo mount -a
``` command, we won't get back an error saying the partition is already mounted.

**Edit**: Maybe this screenshot will help explain a little better.[/QUOTE]

i am sorry,let me tell u english is not my native language ,so i can't understand the ups and downs in texts and speeches like one u posted
 "Does that make sense to you? Right now, your Windows partition may be mounted (but not with the correct permissions) or it may not be mounted. The unmount command just makes sure we're starting from square one either way. "

u may think of me as an idiot , but it is a problem with me that i can't understand such things

due to above ups and downs , i can't find the answer to my question that is 
 whether my data would be lost or not?
whether i be able to acces my fat32 partition in windows aftwer doing all above process?
i would be very very thankful to the person answering in simple words like yes,no,etc so that i may understand

sorry once again

my question

---

### Post by aysiu on 2006-05-27
[QUOTE=u04f061]
 whether my data would be lost or not?[/quote] If you mount your FAT32 partition and then decide to highlight every file and press the Delete button, then, yes, your data will be lost.

If you just mount the partition, your data will not be lost.

> 
whether i be able to acces my fat32 partition in windows aftwer doing all above process? Yes, but you have to pay attention to which partition is FAT32 and which one is NTFS.

They do not mount in exactly the same way.

> 
i would be very very thankful to the person answering in simple words like yes,no,etc so that i may understand The attached screenshot in the last post didn't help?

By the way, there are other Ubuntu Forums out there. This one is in English, but I happen to know, for example, that there's a French one and German one. There may be a forum that is targeted to your native language.

---

### Post by u04f061 on 2006-05-27
my native is urdu and urdu is like arabic.so typing such languages in pc is difficult for normal users .so i don't think there would be any forum in urdu here
if u know plz tell me.thnx

---

### Post by u04f061 on 2006-05-27
[QUOTE=aysiu]If you mount your FAT32 partition and then decide to highlight every file and press the Delete button, then, yes, your data will be lost.

If you just mount the partition, your data will not be lost.

 Yes, but you have to pay attention to which partition is FAT32 and which one is NTFS.

They do not mount in exactly the same way.

 The attached screenshot in the last post didn't help?

By the way, there are other Ubuntu Forums out there. This one is in English, but I happen to know, for example, that there's a French one and German one. There may be a forum that is targeted to your native language.[/QUOTE]


the link u gave me and i followed it but the following error encountered 
ejaz@ejaz:~$ sudo fdisk -l
Password:

Disk /dev/hda: 20.0 GB, 20000268288 bytes
255 heads, 63 sectors/track, 2431 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         730     5863693+   7  HPFS/NTFS
/dev/hda2            1734        2431     5606685    f  W95 Ext'd (LBA)
/dev/hda3             731        1733     8056597+  83  Linux
/dev/hda5            1782        2431     5221093+   b  W95 FAT32
/dev/hda6            1734        1781      385497   82  Linux swap / Solaris

Partition table entries are not in disk order
ejaz@ejaz:~$ sudo umount/dev/hda5
sudo: umount/dev/hda5: command not found
ejaz@ejaz:~$

---

### Post by aysiu on 2006-05-28
[QUOTE=u04f061]
ejaz@ejaz:~$ sudo umount/dev/hda5
sudo: umount/dev/hda5: command not found
ejaz@ejaz:~$[/QUOTE] You don't have a space between *umount* and *dev/hda5*.

Instead of ```
sudo umount/dev/hda5
``` you should type ```
sudo umount /dev/hda5
``` Do you see the difference?

---

### Post by u04f061 on 2006-05-28
still found nothing

Disk /dev/hda: 20.0 GB, 20000268288 bytes
255 heads, 63 sectors/track, 2431 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         730     5863693+   7  HPFS/NTFS
/dev/hda2            1734        2431     5606685    f  W95 Ext'd (LBA)
/dev/hda3             731        1733     8056597+  83  Linux
/dev/hda5            1782        2431     5221093+   b  W95 FAT32
/dev/hda6            1734        1781      385497   82  Linux swap / Solaris

Partition table entries are not in disk order
ejaz@ejaz:~$ sudo umount /dev/hda5
umount: /dev/hda5: not mounted
ejaz@ejaz:~$

---

### Post by catlett on 2006-05-28
I was tyring to use this website [http://apniurdu.com/Translate.html](http://apniurdu.com/Translate.html) to translate the sentences that follow



Everything is fine. umount means that the partition is not mounted, and that is what the output is.
the directions won't hurt your partitions.
only if you press delete after your partitions are mounted will you loose data

---

### Post by u04f061 on 2006-05-28
but what about above post that is umount command is not working

still found nothing

Disk /dev/hda: 20.0 GB, 20000268288 bytes
255 heads, 63 sectors/track, 2431 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 730 5863693+ 7 HPFS/NTFS
/dev/hda2 1734 2431 5606685 f W95 Ext'd (LBA)
/dev/hda3 731 1733 8056597+ 83 Linux
/dev/hda5 1782 2431 5221093+ b W95 FAT32
/dev/hda6 1734 1781 385497 82 Linux swap / Solaris

Partition table entries are not in disk order
ejaz@ejaz:~$ sudo umount /dev/hda5
umount: /dev/hda5: not mounted
ejaz@ejaz:~$

---

### Post by catlett on 2006-05-28
umount=not mounted
umount can't do anything
it is already unmounted
mount is what mounts the partition
Do this to mount it for this session 
```
sudo mkdir /media/partition5
```
```
sudo mount /dev/hda5 -t vfat /media/partition5
```
That will mount for this session only. Follow Aysiu's guide for permanent mounting

---

### Post by jgoguen on 2006-05-28
[quote=u04f061]i have two partitions for windows.
1-fat32 in which my data is stored
2-ntfs in which widows os is installed

i am using windows 2000 with service ppack 2

the link above  which was given by aysiu says unmount.

i can't understand the term.what does it mean?will it erase all my data?
should i be able to access it through windows as well or after unmounting it will be a part of ubuntu space only?

i am not taking any action of instructions on the site as well as above  commands written by nice fellow  bcoz i am not sure about my data.
plz tell me of this so that i may take a step[/quote] That fdisk output helps a lot.  You want to mount /dev/hda5, which I see you've been using already.  I'm going to assume that you mount your Windows data on the folder /home/ejaz/windata/.  To make this, use
```
mkdir /home/ejaz/windata
``` To mount your Windows data on that folder without the /etc/fstab entry I gave above:
```
sudo mount -t vfat -o rw,utf8,users,uid=ejaz /dev/hda5 /home/ejaz/windata
``` Or if you've already made the change to your /etc/fstab:
```
sudo mount /home/ejaz/windata
``` This allows you to read the data in Linux.  Open Nautilus and go to the windata folder in your Home directory, and it's all there.  You can safely edit, create, delete, etc. whatever you want.  You **will not** lose your data just by mounting and unmounting, FAT doesn't have that problem.
Now, to unmount, use the command:
```
sudo umount /home/ejaz/windata
``` The data is still there, you just can't view it in Linux until you mount it again.  If you give the umount command before mounting, it will come back with an error and tell you that /dev/hda5 is not mounted.  That's expected, it's just telling you that you can't remove something that isn't there.

To permanently mount, put the following line in your /etc/fstab:
```
/dev/hda5     /home/ejaz/windata     vfat     rw,uid=ejaz,utf8,users     0     0
``` This will make Ubuntu mount your Windows data every time the computer boots into Ubuntu.

Now, there's one thing to keep in mind.  Linux ends lines in text files differently than Windows does.  [technical]Linux uses LF (\n) while Windows user CRLF (\r\n) to designate the end of a line.[/technical]  If you create a text file in Linux and then open it in Windows Notepad, it will appear to be all on one line.  I suggest using something other than Notepad in Windows (I use [Crimson Editor]("http://robotics.snu.ac.kr/pds/CrimsonEditor/cedt370r.exe")) so that you can easily share text files between Linux and Windows.  Crimson Editor will not only properly read Linux text files, but also save text files with Linux-style end-of-line.

---

