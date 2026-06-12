---
title: "how this installation method works? tries to install without CD"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by quecoder on 2008-02-28
Hello ,
I have found this method ( it's new for me , but may be very old for some ppl here )..
It's located in [http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html](http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html)
the installation steps are , as usual , very very brief  , I don't understand what he is meaning all the time ..
first ,* 3)Before installing Ubuntu you will need to partition your drive. In essence you will need to boot from another media either a floppy, 2nd drive or USB key and run some type of partition software. Create one new partition for the Ubuntu installation, one to hold the .iso file & additional boot files (say 700megs). You might need to resize your existing OS to make space for the above 2 partitions.*

what does he mean ?? 
* I can make it boot from hard drive only ? and partitions , one that holds the iso file , and anther one for ubuntu installation or they are the same 700MB ? and what is the type for the new partition , can I make it NTFS >>>

* what is the difference between drive and partition ?

[I]4)Now you need to Install grub onto either a floppy or hard drive and create a similar entry in your menu.lst file

title Install Ubuntu
root (hd0,2)
kernel /boot/vmlinuz vga=normal ramdisk_size=14972 root=/dev/rd/0 rw &#8211;
initrd /boot/initrd.gz

**(hd0,2) refers to the 1st hard drive &#8216;hd0&#8242; and the 3rd partition &#8216;2&#8242;.

The counting of partitions and hard drives starts at zero.

Change (hd0,2) to match the drive and partition of your .iso file.[/I]

* install grub from where, ? add similar entry to what ? and where is menu.lst ...
* (hd0,2) what this is for ?? how can I know the number of partition or drive , assuming that I know the difference between both of them ,but actually i don't !!


I want to understand just this part of explanation , before adding other steps ...please help me , I had a LOT of troubles with linux , 2 months and still trying to understand how to get it just installed  ...

---

### Post by Arkenzor on 2008-02-28
You should probably take a look at [this guide](https://help.ubuntu.com/community/Installation/FromWindows) (section "The CD Image Approach" at the end of the page) instead, it seems much more detailed and easy to understand.


But unless you can't boot from a CD at all you should really settle for the usual installation method, it's a lot easier that way.

---

### Post by seshomaru samma on 2008-02-28
firstly I think this a very complicated method , if you don't have a CD , you should try running[ Unetbooting]("http://sourceforge.net/project/showfiles.php?group_id=198821"). Go to the link I posted look for "netbooting ubuntu 7.10" download it and install it on your windows. Reboot and you will get a new menu before windows come up with an option to start an ubuntu installation. This installation will download the files from the internet. If you have internet connection (not wireless though) this will be the simplest way to do it.

You can have several partitions on a drive (maximum of 4 if they are "primary" partitions). The partitions are what Windows call "C Drive " or "D Drive". Notice however that Linux names them differently.
You cannot install another OS on teh same partition as Windows , so if you have only one Windows partition (just a C , no D or E or whatever Windows name it) then you will have to create a new one. You cannot do it within Windows , so you need to boot from an external media. If you Partition Magic (a Windows programme)  just use that to resize the Windows partition and create a new one for Linux. 
if you have several partitions on your disc , you can just format one and install Linux on it.

I suggest you make a back up of all your important files before you start!

Also before you install Linux please read [this]("http://www.psychocats.net/ubuntu/")

---

### Post by quecoder on 2008-02-28
> **Arkenzor said:**
> You should probably take a look at [this guide](https://help.ubuntu.com/community/Installation/FromWindows) (section "The CD Image Approach" at the end of the page) instead, it seems much more detailed and easy to understand.


But unless you can't boot from a CD at all you should really settle for the usual installation method, it's a lot easier that way.

ok let me tell you the steps I have done using the guide you gave me :
1-I downloaded initrd.gz & vmlinuz into hd-media folder in C drive.
2- I download grub for dos and extracted a file , that has no extension in windows here , called grldr and I put it in C drive root .
3-I put the alternate  ISO **ubuntu-7.10-alternate-i386.iso** in C drive root .

I should now make 2 things according to the guide , 
1- adding c:\grldr="Install Ubuntu" to boot.ini
2- creating menu.lst with 
[CENTER][I]title Install Ubuntu
kernel   (hd0,0)/hd-media/vmlinuz root=/dev/ram0 ramdisk_size=128000
initrd   (hd0,0)/hd-media/initrd.gz[/I][/CENTER]

I noticed that  hd0,0  is my C drive that will take the vmlinuz and initrd from , depending on my last steps ... but where will it installs ubuntu into ??
are these all the steps needed or I need to make a new partition ?? if yes , how to make it and it's size and other needed information please ..

thanks for your help

---

### Post by quecoder on 2008-02-28
> **seshomaru samma said:**
> firstly I think this a very complicated method , if you don't have a CD , you should try running[ Unetbooting]("http://sourceforge.net/project/showfiles.php?group_id=198821"). Go to the link I posted look for "netbooting ubuntu 7.10" download it and install it on your windows. Reboot and you will get a new menu before windows come up with an option to start an ubuntu installation. This installation will download the files from the internet. If you have internet connection (not wireless though) this will be the simplest way to do it.

You can have several partitions on a drive (maximum of 4 if they are "primary" partitions). The partitions are what Windows call "C Drive " or "D Drive". Notice however that Linux names them differently.
You cannot install another OS on teh same partition as Windows , so if you have only one Windows partition (just a C , no D or E or whatever Windows name it) then you will have to create a new one. You cannot do it within Windows , so you need to boot from an external media. If you Partition Magic (a Windows programme)  just use that to resize the Windows partition and create a new one for Linux. 
if you have several partitions on your disc , you can just format one and install Linux on it.

I suggest you make a back up of all your important files before you start!

Also before you install Linux please read [this]("http://www.psychocats.net/ubuntu/")

The problem with unetbootin is , there is no clear explanation for using a downloaded iso , I don't want it to download a new iso while I have one already .. my internet connection is slow and this is my first time installing any linux distro .. i'm afraid I stuck there alone and don't know what to do without any help if things went wrong with downloading..as i have a single PC  at home :)
I'm a typical noob when it comes to linux

---

### Post by quecoder on 2008-02-28
up

---

### Post by quecoder on 2008-02-28
:(

---

### Post by dstew on 2008-02-28
Hi quecoder. It seems you have a machine without a CD-ROM drive, and you want to install Ubuntu on it, correct? There are many ways to do that. Does your machine have a bootable floppy drive, or a bootable USB port? Is the hard drive a regular IDE drive? How do you plan to get the .iso file into your machine?

The method you refer to requires that you create partitions on your hard drive before you put the kernel and .iso on there. Without a CDROM, and if you don't have a bootable USB drive, you might have to use a text-based partitioner from a floppy boot.

---

### Post by quecoder on 2008-02-28
> **dstew said:**
> Hi quecoder. It seems you have a machine without a CD-ROM drive, and you want to install Ubuntu on it, correct? There are many ways to do that. Does your machine have a bootable floppy drive, or a bootable USB port? Is the hard drive a regular IDE drive? How do you plan to get the .iso file into your machine?

The method you refer to requires that you create partitions on your hard drive before you put the kernel and .iso on there. Without a CDROM, and if you don't have a bootable USB drive, you might have to use a text-based partitioner from a floppy boot.

no , my laptop has a CD-ROM but I'm getting errors when trying to boot from the CD ..media check failure  error , and some CDs go blank when booting from.. although , my windows recovery CD is booting very well.
so , I'm trying to find an easy way to install ubuntu without needing to boot from a CD

---

### Post by dstew on 2008-02-28
It sounds like either your .iso has errors on it, or it did not burn true. The media check failure usually means the latter. Did you do the MD5 checksum on the original .iso before you burned it? What speed did you use to burn the image?

If you have a DSL or faster network connection, you can easily install over the internet using unetbootin. If you do not have a high-speed connection, I suggest trying to burn another image CD (after checking the MD5 sum of the .iso of course). Burn at the very slowest speed possible. If you drop a single bit from a CD image, the installation will probably fail. Music CDs are different, and very fault tolerant, so you can burn them at a much faster speed. You get errors, but you don't notice them.

---

### Post by goodmaj on 2008-02-28
Are you sure that you have burned the iso correctly?  It is not just a data disk.  Try to get the Windows app DeepBurner.  It is free and will burn an iso correctly.

Also, check the MD5sum of the iso image to assure that it is correct.

---

### Post by quecoder on 2008-02-28
> **dstew said:**
> It sounds like either your .iso has errors on it, or it did not burn true. The media check failure usually means the latter. Did you do the MD5 checksum on the original .iso before you burned it? What speed did you use to burn the image?

If you have a DSL or faster network connection, you can easily install over the internet using unetbootin. If you do not have a high-speed connection, I suggest trying to burn another image CD (after checking the MD5 sum of the .iso of course). Burn at the very slowest speed possible. If you drop a single bit from a CD image, the installation will probably fail. Music CDs are different, and very fault tolerant, so you can burn them at a much faster speed. You get errors, but you don't notice them.

does the burning speed matter ? and i'm not sure if I was checking the MD5 on every CD I burned or no ..
I don't prefer downloading a new iso when it's installing the linux , i don't know , I have not tried that before  and my connection is slowing from time to time and may break for more than half an hour although I can download by 150KB/s on regular times. I don't want to mess with that or to keep it at last

---

### Post by dstew on 2008-02-28
> does the burning speed matter ?Yes it matters very much when you are burning images.> i'm not sure if I was checking the MD5 on every CD I burnedYou check the MD5 sum on the .iso file *before* you burn it.> I can download by 150KB/s on regular timesIf that is the case, I recommend the network installation using [unetbootin]("http://lubi.sourceforge.net/unetbootin.html"). It includes a partitioning step. If you want, you can break a network installation down into two steps. First, install a Base System (command line only). That takes about an hour at DSL speeds. Then, using the command line, install the Ubuntu desktop with sudo apt-get install ubuntu-desktop. That takes about an hour and a half.

---

### Post by quecoder on 2008-02-28
thanks alot dstew for your help , and please , how much the speed you find it good to burn at ?

---

### Post by dstew on 2008-02-28
4x at most.

---

### Post by philinux on 2008-02-28
> **quecoder said:**
> thanks alot dstew for your help , and please , how much the speed you find it good to burn at ?


4 times is best.

---

### Post by quecoder on 2008-02-28
Thanks alot dstew ,philinux :)

---

