---
title: "[Tut] How to create an Ubuntu live USB for both Mac and PC"
date: 2010-03-31
forum: Apple Hardware Users
---

### Post by Neds Moar Salt on 2010-03-31
I spent a week figuring this out.  You can boot Ubuntu from a flash drive on an intel mac and easily.  These instructions are for Ubuntu 9.10 and 10.04.

You will need:
```
[LIST]
[*]rEFIt
[*]A working ubuntu installation, VM or real
[*]1GB or larger flash drive
[*]Working OS X installation
[*]gparted
[*]Administrator privileges on both mac and linux
[/LIST]
```

First, open up Disk Utility (Utilities > Disk Utility) and format you drive with this:
```
[LIST]
[*]GUID Partition Table
[*]4.2 MB Free Space at beginning of drive
[*]64 MB HFS+ (Mac Journaled)
[*]64 MB FAT for GRUB
[*]600MB FAT for Ubuntu Live
[*]Rest of your drive FAT for data
[/LIST]
```

Next, install rEFIt to your hard drive.

Then, install rEFIt to your flash drive:
```
[LIST=1]
[*]Copy the efi directory on / to your rEFIt partiton
[*]In Terminal.app (Utilities > Terminal), type "sudo ", drag the "enable.sh" file in /Volumes/rEFIt/efi/whatever into the terminal, and press enter.
[/LIST]
```

Then, boot into Ubuntu and:
```
[LIST=1]
[*]Open gparted
[*]Select your flash drive in the top right corner
[*]Select your GRUB partition
[*]Right click, format as ext2
[*]Right click > Label and set as "Grub"
[*]Right click > Manage flags and check "boot" (if it is already checked, uncheck it then recheck it)
[*]Open System > Disk utility and mount your Grub partition
[*]Open a terminal
[*]Execute "sudo grub-install --root-directory=/media/Grub /dev/sdb".  You should get no errors or warnings.  If you do, you either didn't set the Grub partition's boot flag or left out the 4.2 MB free space at the beginning of the drive.
[/LIST]
```

Now, to put Ubuntu on the flash drive:
```
[LIST=1]
[*]Mount your iso file or cd.  For iso's, just use "Open with Archive Mounter".
[*]Select everything in the mounted iso and copy it to the Live CD partition of your flash drive with nautilus.
[*]You now have Ubuntu installed on your flash drive!
[/LIST]
```

To use the grub menu, in the Grub partition, create /boot/grub/grub.cfg and copy this into it:
```
menuentry "Chainload to HD" {
 set root=(hd1)
 chainloader +1
}
menuentry "Ubuntu Live" {
 set root=(hd0,3) # Replace this with you Live partition
 linux /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash
 initrd /casper/initrd.lz
}
```

To boot into linux, reboot holding the option key and select the rEFIt option for your flash drive, then select boot linux from your HD (the one with the USB picture above it).  If your flash drive doesn't show up when you use the option key, reinstall rEFIt to your flash drive.

In a little while, I will edit in how to save your home directory.

Edit: Alright, now for saving your home directory.
Boot into your live linux and copy the /home/ubuntu to your data partition.  Name it however you like.  Save the following text as "Mount.sh", and of course, change the <the folder you just copied part>.```
# Mount the home directory
sudo mount --bind /media/DATA/<the folder you just copied> /home/ubuntu
# Log out and restart X
sudo killall -9 Xorg
```
To use your new home, just run the Mount.sh file.  It will log you out.  Log in with "ubuntu" as your username and "" for your password.  It will take longer to log in this way and you will probably get an error about ICE something.  You can save your changes now.

---

### Post by produnis on 2010-04-23
Thanks,
but it won't work for me.
At startup, holding down ALT lets me select my USB-Efi-Partition,
but after that, my Book keeps booting not from USB but from HD..
strange..

---

### Post by npfthunfan on 2010-04-29
I get a permissions denied error when trying to create a file in the Grub partition...

---

### Post by npfthunfan on 2010-04-30
> **produnis said:**
> Thanks,
but it won't work for me.
At startup, holding down ALT lets me select my USB-Efi-Partition,
but after that, my Book keeps booting not from USB but from HD..
strange..

I get that too :S

---

### Post by Neds Moar Salt on 2010-05-03
> **produnis said:**
> Thanks,
but it won't work for me.
At startup, holding down ALT lets me select my USB-Efi-Partition,
but after that, my Book keeps booting not from USB but from HD..
strange..

You didn't select your flash drive from rEFIt?

---

### Post by Neds Moar Salt on 2010-05-03
> **npfthunfan said:**
> I get a permissions denied error when trying to create a file in the Grub partition...

Use 'sudo'

---

### Post by npfthunfan on 2010-05-03
> **Neds Moar Salt said:**
> You didn't select your flash drive from rEFIt?

I'm pretty sure I tried all the combinations... and definitely did what you said... didn't work.

---

### Post by Neds Moar Salt on 2010-05-03
> **npfthunfan said:**
> I'm pretty sure I tried all the combinations... and definitely did what you said... didn't work.

I am making another one right now.  I'll let you know what I did...

---

### Post by JoelThomas on 2010-05-04
Thanks for posting this walkthough.  It saved a lot of time researching.

I couldn't get Grub to install without using --force, and I had to add a couple of kernel options (root and the ignore_uuid option so the boot wouldn't hang with stdin: error 0), but it does now boot into Lucid on my PC.  

On my Macbook Pro, I can select rEFIt, and I get the option to choose an apple or a penguin, but choosing penguin leads to a "no bootable device" error...so still some troubleshooting to do.

Here's my modified grub.cfg in case it helps anyone else.

```
menuentry "Chainload to HD" {
 set root=(hd1)
 chainloader +1
}
menuentry "Ubuntu Live" {
 set root=(hd0,3)
 linux /casper/vmlinuz file=/preseed/ubuntu.seed boot=casper root=/dev/sdb3 ignore_uuid quiet splash --
 initrd /casper/initrd.lz
}

```

---

### Post by Merath on 2010-05-10
Does anyone else's Disk Utility on Mac fail in the middle of partitioning their usb drive specified above?  Mine gets through several of the partitions and then I get the message saying this disk is not initialized and the option to ignore or eject it, I hit either and the disk utility tells me it has lost connection with the disk manager or something similar and closes...  Is it possible to setup the thumb drive's partitions with gparted in stead of in os x's disk utility?

---

### Post by godavid on 2010-05-13
> **Merath said:**
> Does anyone else's Disk Utility on Mac fail in the middle of partitioning their usb drive specified above?  Mine gets through several of the partitions and then I get the message saying this disk is not initialized and the option to ignore or eject it, I hit either and the disk utility tells me it has lost connection with the disk manager or something similar and closes...

I get the exact same error. I can't create the free space at the beginning of the usb drive.

---

### Post by linuxopjemac on 2010-05-14
I also followed the tutorial yesterday and for me it doesn't work as I probably don't have the right firmware on my MacBook 2,1 to allow USB booting. I could do the whole manual though, it all works.

---

### Post by fraterf93 on 2010-05-18
Great!  So how can I do this on my PPC Mac?

---

### Post by linuxopjemac on 2010-05-19
on a PPC Mac it's a different story.
[http://mac.linux.be/content/booting-open-firmware](http://mac.linux.be/content/booting-open-firmware)
[http://mac.linux.be/phpBB3/viewtopic.php?f=10&t=85](http://mac.linux.be/phpBB3/viewtopic.php?f=10&t=85)
[http://mac.linux.be/phpBB3/viewtopic.php?f=10&t=91](http://mac.linux.be/phpBB3/viewtopic.php?f=10&t=91)
[http://mac.linux.be/content/mint-lxde-debian-lenny-ppc](http://mac.linux.be/content/mint-lxde-debian-lenny-ppc)

---

### Post by TeknoJuce on 2010-05-24
Get a black screen with a blinking cursor no errors?

Also your documentation says copy / efi to run the sh from your refit partition should it not say from your partition on the key that you formatted with the mac journal file system?

---

### Post by Phidaux on 2010-06-02
I appreciate all of your work but alas, after spending far too long trying this (not to mention the other dozen tutorials out there) I'm finally going to ask for help from someone who has gotten this to work. 

So, if anyone out there can point me in the right direction I'd really appreciate it. 

This is my most recent attempt to boot/install ubuntu 10.04 live to my 3,1 macbook pro (all the updates, most recent OS, etc blah blah blah) from usb and yes, my optical drive is dead. 

1) I've created a usb boot key with the aforementioned method
2) it starts the boot process as far as I can tell
3) and hangs indefinitely on the same screen after it identifies the video card? with no activity on the usb stick.

##### The following is my grub.cfg 

menuentry "Chainload to HD" {
 set root=(hd1)
 chainloader +1
}
menuentry "Ubuntu Live" {
 set root=(hd0,3) # Replace this with you Live partition
 linux /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash
 initrd /casper/initrd.lz
}
menuentry "alt 1 Ubuntu Live" {
 set root=(hd0,3) # Replace this with you Live partition
 linux /casper/vmlinuz file=/preseed/ubuntu.seed boot=casper quiet splash
 initrd /casper/initrd.lz
}
menuentry "alt 2 Ubuntu Live" {
 set root=(hd0,3)
 linux /casper/vmlinuz file=/preseed/ubuntu.seed boot=casper root=/dev/sdb3 ignore_uuid quiet splash --
 initrd /casper/initrd.lz
}

######

help help help me please ... i've banged my head against this problem for too long and I'm on the verge of taking a hammer and using the usb key as a nail as I'm starting to think that's the only way I'll be able to get ubuntu into this god forsaken mac.


much love & gratitude,
prd

---

### Post by Neds Moar Salt on 2010-06-07
> **Phidaux said:**
> I appreciate all of your work but alas, after spending far too long trying this (not to mention the other dozen tutorials out there) I'm finally going to ask for help from someone who has gotten this to work. 

So, if anyone out there can point me in the right direction I'd really appreciate it. 

This is my most recent attempt to boot/install ubuntu 10.04 live to my 3,1 macbook pro (all the updates, most recent OS, etc blah blah blah) from usb and yes, my optical drive is dead. 

1) I've created a usb boot key with the aforementioned method
2) it starts the boot process as far as I can tell
3) and hangs indefinitely on the same screen after it identifies the video card? with no activity on the usb stick.

##### The following is my grub.cfg 

menuentry "Chainload to HD" {
 set root=(hd1)
 chainloader +1
}
menuentry "Ubuntu Live" {
 set root=(hd0,3) # Replace this with you Live partition
 linux /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash
 initrd /casper/initrd.lz
}
menuentry "alt 1 Ubuntu Live" {
 set root=(hd0,3) # Replace this with you Live partition
 linux /casper/vmlinuz file=/preseed/ubuntu.seed boot=casper quiet splash
 initrd /casper/initrd.lz
}
menuentry "alt 2 Ubuntu Live" {
 set root=(hd0,3)
 linux /casper/vmlinuz file=/preseed/ubuntu.seed boot=casper root=/dev/sdb3 ignore_uuid quiet splash --
 initrd /casper/initrd.lz
}

######

help help help me please ... i've banged my head against this problem for too long and I'm on the verge of taking a hammer and using the usb key as a nail as I'm starting to think that's the only way I'll be able to get ubuntu into this god forsaken mac.


much love & gratitude,
prd

It turns out this is not a very good way, there is a much more simpler and reliable way that I have found and I will make a guide soon.

---

### Post by DoubleClicker on 2010-06-07
Since you have a working LiveUSB, how about making an ubuntu-10.4.dmg disk image, so that the newbies, can just download it in Mac OS X, and "restore" it to a thumb drive using Disk Utility.  Making it available as such will save a lot of grief for the less technical users, who won't have to reinvent the wheel.

EDIT: ..Or better yet, if you are willing,  provide both 32-bit and 64-bit versions

---

### Post by linuxopjemac on 2010-06-07
good idea doubleclicker, I can host the file if you want.

---

### Post by Neds Moar Salt on 2010-06-07
> **DoubleClicker said:**
> Since you have a working LiveUSB, how about making an ubuntu-10.4.dmg disk image, so that the newbies, can just download it in Mac OS X, and "restore" it to a thumb drive using Disk Utility.  Making it available as such will save a lot of grief for the less technical users, who won't have to reinvent the wheel.

EDIT: ..Or better yet, if you are willing,  provide both 32-bit and 64-bit versions

I could but that's a 2gb upload for me...

---

### Post by DoubleClicker on 2010-06-08
> **Neds Moar Salt said:**
> I could but that's a 2gb upload for me...

2 GB????   What do you have in there?

I presume that you know that a dmg is not the size of the the USB drive, but the size of the data on it after, it has been compressed.   So I would expect that a vanilla install from the iso, would produce a dmg which is smaller than the iso

---

### Post by hydrox24 on 2010-12-29
When partitioning the USB on my macbook pro Intel from late 2008, the setup mentioned here causes it to freeze or "hang" on the "creating partition map" if I force close Disk util then open it up I find that the USB has three partitions not five.
Interestingly, these three partitions are the three FAT partitions so I think that the issue maybe to do with the size of the HFS+ Disk. Also, If I leave each partition at the same size (about 700Mb) and change each partition to the correct formatting in the right order, It works perfectly, 
I will post again if I get it working but in the meantime, can ANYBODY help me, I am kinda desperate.

Edit: I fixed the issue by making the blank space partition much larger. Will post details asap (will probably be atleast five days)

Edit-2: I worked around the bug in the OSX disk utility by making the "free space" partition 500Mb and ignoring that the 64Mb HFS+ partition was supposedly full acording to the mac. (to put the rEFIt files on it I just used the graphical finder (drag and drop)).
Hope that I could help!

---

### Post by Neds Moar Salt on 2010-12-30
> **hydrox24 said:**
> When partitioning the USB on my macbook pro Intel from late 2008, the setup mentioned here causes it to freeze or "hang" on the "creating partition map" if I force close Disk util then open it up I find that the USB has three partitions not five.
Interestingly, these three partitions are the three FAT partitions so I think that the issue maybe to do with the size of the HFS+ Disk. Also, If I leave each partition at the same size (about 700Mb) and change each partition to the correct formatting in the right order, It works perfectly, 
I will post again if I get it working but in the meantime, can ANYBODY help me, I am kinda desperate.

rEFIt is a PAIN, especially for having it boot as bios for a usb disk.  Things that will boot pc's and virtualbox will not always boot from refit.  I am finding out right now how to make a gpt-mbr hybrid on my flash drive so that refit won't freak.  Ill post back when I find out, probably tonight or tomorrow.

Edit: wait a second, I wrote this: [http://ubuntuforums.org/showthread.php?t=1504038](http://ubuntuforums.org/showthread.php?t=1504038)
Just tried it, and it worked.

---

