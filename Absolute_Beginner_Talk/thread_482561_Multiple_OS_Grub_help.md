---
title: "Multiple OS Grub help"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by KiwiPete on 2007-06-23
Hi

I have been using a dual boot system - WinXP and Ubuntu Edgy - quite successfully overthe last few months.
I have several unused ext3 partitions and thought I'd try adding Fedora 7 as a third OS.
The install went fine, but I stuffed up the Grub and now need some help.

When installing Fedora I selected the "Add Grub to Master Boot Record" option.
The install automatically detected WinXP and added that to the Grub, but it did not detect Ubuntu.

So I now have a sysytem that dual boots WinXP and Fedora.
My question is: 
**How can I add Ubuntu to the Grub? I cannot get back into Ubuntu at all at the moment.**

I have found out how to edit the Grub when the system starts up, but I'm not sure exactly what lines I need to add to that file - and in connection with that I am unsure what kernel my Ubuntu 6.10 uses as I know that one of the lines needs to name the kernel.

One of the related problems caused by my inability to get back into Ubuntu is that the /Home partition seems to have restricted access settings, so when I'm in Fedora all my data files are read only - and I cannot change that from within Fedora.
FYI here is a description of the partitions I have on the two hard drives:

DRIVE 1 40Gb:
NTFS with just one partition used for Win XP

DRIVE 2 280Gb:
Partition 1 about 20Gb NTFS (unused - intended for another Windows OS if I ever want it)
Partition 2 FAT32 about 240Gb - /Home used for data accessed by all OS
Partition 3 Ext - with three logical Ext sub-partitions (5,6 & 7) each about 5Gb - Partition 5 has Ubuntu 6.10 root; Partition 6 now has Fedora 7 root; and Partition 7 unused at the moment. 
Partition 4 Swap 2Gb

Thanks for any help you can offer.

KiwiPete

---

### Post by indralaily on 2007-06-23
it's not big problem i think :D

Fedora Core alway like that, the can deteck another Linux in your computer

the easy think is

boot from your fedora core, at terminal mount your Ubuntu root partitio

$ sudo mount /dev/your_ubuntu_root /mnt

use vi or gedit
$ sudo gedit /mnt/boot/grub/menu.lst

and search line like this
```

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=952e8709-ec70-4459-bf64-459bda357c57 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

```

copy this line, and then open your grub menu for fedora

$ su -c gedit /boot/grub/menu.lst

then paste into this file

sory for my bad english

hope this help you

---

### Post by confused57 on 2007-06-23
You could also reinstall Edgy's grub IPL to the mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

You might then be able to add an entry to boot Fedora, using a configfile entry:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

---

### Post by louieb on 2007-06-23
```

title Ubuntu configfile
     configfile   (hd0,4)/boot/grub/menu.lst

```
Just point Fedora's GRUB configuration file /boot/grub/menu.lst  lto your Ubuntu menu.lst    an don't worry about kernel names or updates.   
The above should work.  you may have to adjust the (hd#,#) part to point to the Ubuntu partition.  
See the dual boot link for more good stuff on GRUB and other boot loaders.

---

### Post by KiwiPete on 2007-06-24
Thanks for all your suggestions, but the problem is proving intractable.
When i boot Fedora I get a message saying
"$HOME/.dmrc file is being ignored"
and I am then unable to use sudo from the Terminal - or change any files in the /home directory.
Message says I am not listed in the "sudoers file"

I did manage to get Ubuntu to start in safe mode, but it too displays the same $HOME/.dmrc file is being ignored.

Any suggestions?
Maybe I should re-install both Ubuntu and Fedora from scaratch and be very careful with the Grub this time?

KiwiPete

---

### Post by confused57 on 2007-06-24
> **KiwiPete said:**
> Thanks for all your suggestions, but the problem is proving intractable.
When i boot Fedora I get a message saying
"$HOME/.dmrc file is being ignored"
and I am then unable to use sudo from the Terminal - or change any files in the /home directory.
Message says I am not listed in the "sudoers file"

I did manage to get Ubuntu to start in safe mode, but it too displays the same $HOME/.dmrc file is being ignored.

Any suggestions?
Maybe I should re-install both Ubuntu and Fedora from scaratch and be very careful with the Grub this time?

KiwiPete

I think your problem may be having a shared /home partition for Ubuntu & Fedora.../home needs to be formatted ext3 also, at least for Ubuntu...unless someone knows a way to repair this, reinstalling may be your best option.

---

### Post by Keen101 on 2007-06-24
you could always try just reinstalling GRUB.  Try downloading and using the SUPER GRUB DISK. Grub should detect all Os and set it up fine. The fedora cd may have had an older version of grub that does not detect Ubuntu.

---

