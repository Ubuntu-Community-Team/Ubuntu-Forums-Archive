---
title: "GRUB list file. Config file?"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by Spidermans_DarkSide on 2007-02-08
Hi all,

Can anyone please tell me how i can create a lst file from the terminal when in root as super user please?

I can mount my windows partition with.>>

mkdir /windows

mount /dev/hde1 /windows -t ntfs

then when i type.>>

sudo nautilus

i can navigate and see my windows files. :-)

However i'd like to put a lst file on my hard-drive so i can boot into linux,windows etc.

Another student told me the above command sequence.

I need windows partition back up and running for my university course.

Finally He recommended Linux Mandrake as the easiest for dealing with the hard-drive
partitions graphically. Any thoughts please?

Please help in this regard otherwise i'm downloading k3b or putting the hard drive in question into a usb enclosure and booting my p.c. with this hard drive, that is running right now, to access my files.
I'd prefer to get the other drive back up and running though.

Help please.


Regards,

S_DS

---

### Post by confused57 on 2007-02-08
Do you have Ubuntu installed or are you just using the live cd?  If you have Ubuntu installed, you should be able to add an entry to boot Windows from grub.

Here's my setup:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

If you have Ubuntu installed and you're able to boot it successfully from the grub menu, you might want to post the output of:

```
sudo fdisk -l
```
The -l is a small "L"

```
cat /boot/grub/menu.lst
```
menu.lst is short for menu.list
you just need to post the entries to boot Ubuntu & Windows(if an entry is listed)

```
cat /boot/grub/device.map
```
this will show how grub recognizes the boot order of your hard drives

---

### Post by Spidermans_DarkSide on 2007-02-08
Hi,

Thanks for your reply. :-)

Ubuntu Linux not installed as i went on the cautious side so i am working off the live cd only.

hd partitions are

/dev/hde1 #WIN-XP-SP2
/dev/hde2 #/BOOT i think
/dev/hde3 #not assigned and it came up as too small for SWAP


Regards,

S_DS

---

### Post by confused57 on 2007-02-08
I'm not sure what you're wanting to do, but you can post the first command from the live cd:
```
sudo fdisk -l
```

If you're wanting to boot Windows, you might want to look into the Super Grub Disk(approx 500 kb download:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

What other OS do you have on your computer, that you are using?

---

### Post by Spidermans_DarkSide on 2007-02-11
Hi,

 I had a flash of inspiration. :-) ;-)

 I managed to sort it with the gpart disk partitioner from the live cd. My m.b.r.   was corrupt so i deleted and recreated my Linux partitions within an extended partition and went through the install after clicking the 'INSTALL' icon from the live dvd disk.

Now i know, and remember what i'm doing i might triple boot with UBUNTU, Windows XP and my MSDNAA download of Windows Vista business edition. :-)

Thanks for your help.


Regards,

S_DS

---

