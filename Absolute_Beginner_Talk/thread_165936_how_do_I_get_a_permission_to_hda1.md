---
title: "how do I get a permission to hda1"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by Isoss on 2006-04-25
hey

I am new to linux, and I have installed in with windows xp. I have three partitions, hda1 (ntfs) for windows, hda5 (ntfs) for my stuff and junks, and hda3 (ext3) for linux

the Access path of hda1 is /media/hda1 ... and same for hda5: /media/hda5.

Now when I click on the hda1 or hda5 I get this Error:

Error Displaying Folder

**[SIZE="3"]The forlder contents could not  be displayed[/SIZE]**

you do not have the permission neccessary to view the contects of "hda1"


How do I get the permission? why can't I act like root everywhere else in the system except with terminal?

I need to access my files ... get stuff ... copy, paste delete ... everything ... it's kinda irritating when you are not allowed to deal with your own files like that ](*,)

---

### Post by aysiu on 2006-04-25
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Isoss on 2006-04-25
Ok, let me make it more clear cuz this didn't work the way I desire.

The link you gave me is clear, but unfortunately, I am somehow disappointed. Cuz my windows partition is NTFS and it says that in ubuntu, NTFS is read only ... that's not what I want .. I want a full permission to read, write and execute whatever I want.

In the mountwindows page there is an explaination of how I can unmount and create my own mount point and then how to edit the fstab ... before I did what it said I had a hda1 "file" on my Desktop, and after I did it it disappeared ... I know they exist in /Windows in the filesystem, but how can I make it apear just like the way it was "on my desktop" ... 

And if it's not possible to change the read only thing with NTFS, how can I change this into FAT so it can be read, write, and excute? Will the convert require to format? cuz I don't want anything to be lost.

Thanks for helping.

---

### Post by jazzmuzik on 2006-04-25
That's a great article. I was able to fix my fat32 mounts even better than before.

My only suggestion is if you only want to grant yourself permissions to the fat32 drives, add gid=499 to the partition's options in fstab, then create a group called 'vfat' with a group id of 499 and add your username to the vfat group.

---

### Post by aysiu on 2006-04-25
[QUOTE=Isoss]
In the mountwindows page there is an explaination of how I can unmount and create my own mount point and then how to edit the fstab ... before I did what it said I had a hda1 "file" on my Desktop, and after I did it it disappeared ... I know they exist in /Windows in the filesystem, but how can I make it apear just like the way it was "on my desktop" ... [/QUOTE] Are you using Ubuntu or Kubuntu? 

If you're using Ubuntu, open up the file browser and go to the top-level directory. Find the /windows folder and middle-click-drag it to the desktop. Then select "link here."

If you're using Kubuntu, just drag the /windows folder to the desktop (regular left-click-drag) and select "link here."

> 
And if it's not possible to change the read only thing with NTFS, how can I change this into FAT so it can be read, write, and excute? Will the convert require to format? cuz I don't want anything to be lost. Yes, you'll need to back up that data and reformat the partition. I don't believe NTFS can just be converted to FAT32 without loss of data.

---

### Post by OffHand on 2006-04-25
[QUOTE=aysiu]
 Yes, you'll need to back up that data and reformat the partition. I don't believe NTFS can just be converted to FAT32 without loss of data.[/QUOTE]That's right. If you format it, all data will be lost. To the original poster: Blame microsoft for not being able to write to NTFS. They will not tell others how to do it. They might even have a patent on it.

---

### Post by Isoss on 2006-04-25
[QUOTE='aysiu']Are you using Ubuntu or Kubuntu?

If you're using Ubuntu, open up the file browser and go to the top-level directory. Find the /windows folder and middle-click-drag it to the desktop. Then select "link here."
[/QUOTE]

I use Ubuntu ... :-k  but I am not sure of what you ment by middle-click-drag it to the desktop, can u please explain more?

[QUOTE='subsonic_shadow']
[QUOTE='aysiu']
Yes, you'll need to back up that data and reformat the partition. I don't believe NTFS can just be converted to FAT32 without loss of data.
[/QUOTE]
That's right. If you format it, all data will be lost. To the original poster: Blame microsoft for not being able to write to NTFS. They will not tell others how to do it. They might even have a patent on it.
[/QUOTE]
Ok thanks, I guess what I'monna do is take a back up of hda5 and format it ... I can't format hda1 cuz it's windows. and yes, I think Bill Gates is the one to blame on this :-?  ... I don't like this guy [-( 

any way, thanks guys

---

### Post by aysiu on 2006-04-25
[QUOTE=Isoss]I use Ubuntu ... :-k  but I am not sure of what you ment by middle-click-drag it to the desktop, can u please explain more?[/QUOTE] If you have a scroll wheel like this one (see what's circled in green), press down on it when your mouse pointer is hovered over the /windows folder. Then, hold it down while you drag the pointer to the desktop area. Then let go.

---

### Post by phil66 on 2006-04-25
Using the psychocats mount windows thread I am down to changing the /etc/fstab file

The file is basically about ntfs and I want to mount my fats32 windows.

My windows partion are at /dev/hda1 and /dev/hdb1 they are w95 fats 32 (lba)

Would someone please give me the proper code to add to /etc/fstab.

Help will be appreciated
Ray

---

### Post by Isoss on 2006-04-25
alright, thanks .. this is something new to me .. it worked. thanks.

---

### Post by pbaehr on 2006-04-25
Wow, aysiu, visual aids! A+ for presentation!

---

### Post by aysiu on 2006-04-25
[QUOTE=phil66]Using the psychocats mount windows thread I am down to changing the /etc/fstab file

The file is basically about ntfs and I want to mount my fats32 windows.

My windows partion are at /dev/hda1 and /dev/hdb1 they are w95 fats 32 (lba)

Would someone please give me the proper code to add to /etc/fstab.

Help will be appreciated
Ray[/QUOTE] [http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

---

### Post by delta32 on 2006-04-25
Nevermind, aysiu got to it before me. :)

---

### Post by phil66 on 2006-04-25
ram7lc@ubuntu:~$ sudo mount /dev/hda1 /media/windows -t vfat -o iocharset=utf8,unmask=000
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ram7lc@ubuntu:~$ dmesg | tail
[4294730.060000] Bluetooth: RFCOMM socket layer initialized
[4294730.060000] Bluetooth: RFCOMM TTY layer initialized
[4294801.794000] CSLIP: code copyright 1989 Regents of the University of California
[4294801.854000] PPP generic driver version 2.4.2
[4294803.840000] PPP BSD Compression module registered
[4294803.954000] PPP Deflate Compression module registered
[4294804.894000] ip_tables: (C) 2000-2002 Netfilter core team
[4294804.977000] ip_conntrack version 2.1 (1014 buckets, 8112 max) - 248 bytes per conntrack
[4294961.442000] Inbound IN=ppp0 OUT= MAC= SRC=222.134.45.53 DST=216.119.133.95 LEN=490 TOS=0x00 PREC=0x00 TTL=39 ID=0 DF PROTO=UDP SPT=55991 DPT=1032 LEN=470
[4295045.438000] FAT: Unrecognized mount option "unmask=000" or missing value

This is the error I got using suggest code from 5.04 starter I am using Breezy 5.10
Thanks
Ray

---

### Post by delta32 on 2006-04-25
Add that to your fstab.

```
sudo gedit /etc/fstab
*paste fstab info and save*
mount /media/windows
```

Also, that should be umask, not unmask.

---

### Post by aysiu on 2006-04-25
[QUOTE=phil66]```
ram7lc@ubuntu:~$ sudo mount /dev/hda1 /media/windows -t vfat -o iocharset=utf8,**unmask=000**
```[/QUOTE] It's *umask*, not *u**n**mask*.

---

### Post by phil66 on 2006-04-25
HI guys

Thanks for the tips and corrections to my typing.

In /etc/fstab I had to use from the Ubuntu Wiki:
"/dev/hda1 /media/windows vfat iocharset=utf8,umask=000    0     0

I corrected the typing error of unmask to umask and entered.

I now have windows on my desktop and also in file system under /media/windows.

Thanks for the info and help it was greatly appreciated
Ray

---

