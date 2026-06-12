---
title: "How To: Boot PowerPC live/desktop ISOs via grub2"
date: 2012-09-01
forum: Apple Hardware Users
---

### Post by rsavage on 2012-09-01
This how to shows how grub2 can be used to boot a PowerPC live/desktop iso file stored on a USB flash drive.  It is an alternative to using the dd command or extracting the contents of the iso file.  
 
This method is so easy my dog could do it!
 
I've tested this on a fat32 flash drive using an MS-DOS partition table.  You'll have to do some adjustments if the flash drive is formatted with an Apple Partition Map (becuase the map takes up partition 1).
 
Copy the live/desktop iso file to the first partition of your USB flash drive.
Copy the attached files (grub.cfg, grub.img and ofboot.b) to the first partition of your USB flash drive.
 
Boot into openfirmware
 
Check you have fat support: 
```

dev /packages ls

``` 
and look for the listing "/fat-files". 
 
Find your usb partition using the dir command (this command lists files).  Your partition will probably be usb0/disk@1:1 , usb1/disk@1:1 or ud:1
```

dir usb0/disk@1:1,\
dir usb1/disk@1:1,\
dir ud:1,\

```
 
Then boot the ofboot.b file.  For example:
```

boot usb0/disk@1:1,\ofboot.b

```
 
You'll get some error message about prefix not being set.  Just ignore it.
 
Choose your ubuntu derivative and machine from the menu.  The menu entries are setup for 12.04, so if you've downloaded a different version you'll have to edit the menu entry by pressing 'e'.  Change the isofile value to the name of the iso. 
 
Your live system should now boot!
 
For info:
 
The gub.img was created with this command
 
```

sudo grub-mkimage --prefix="(grubdevice,1)" -o grub.img -O powerpc-ieee1275 -v part_apple part_msdos hfs hfsplus ext2 fat iso9660 loopback linux configfile

```
 
If you want to re-run the command you need to install the grub-ieee1275 package.

---

### Post by rsavage on 2012-09-13
If you need to add a 'yaboot parameter' then at the grub menu hit the  'e' key. Add the parameter(s) after the words "quiet splash" (or delete the word splash).  When  you've made the changes use Ctrl+x to boot.

For some reason you don't see the b43 firmware messages....so if you are using 12.04 and it hangs for no reason and you have an airport extreme card then try using the 'yaboot parameter' b43.blacklist=yes (see PowerPC Known Issues wiki)

If you have stored the grub files somewhere other than the first partition then use the 'configfile' command.  It you don't have a USB flash drive then you could use a hard disk partition.

If you'd like to use the the mini.iso then you don't have to download the iso.  Just use the initrd.gz and vmlinux files from here [http://ports.ubuntu.com/dists/precise/main/installer-powerpc/current/images/powerpc/netboot/](http://ports.ubuntu.com/dists/precise/main/installer-powerpc/current/images/powerpc/netboot/) .

If you want to use an alternate CD then download the initrd.gz and vmlinux files from here [http://ports.ubuntu.com/dists/precise/main/installer-powerpc/current/images/powerpc/hd-media/](http://ports.ubuntu.com/dists/precise/main/installer-powerpc/current/images/powerpc/hd-media/) .

You don't have to use the 'loopback' feature with the mini/alternate CDs.  See the yaboot.conf files for what you need to type in grub.  I can give instructions if requested.

Finally, I've put together instructions for using grub2 on an installed system.  I hope they are pretty easy to follow:

[https://wiki.ubuntu.com/PowerPCFAQ#Can_I_install_grub2.3F](https://wiki.ubuntu.com/PowerPCFAQ#Can_I_install_grub2.3F)

---

### Post by Eudaimon on 2012-09-14
Savage, I've got the closest with your method.  However, it says that it can't load because it doesn't have the right "kernel".  I'm a noob so excuse my ignorance, but what kernel am I supposed to load?

---

### Post by rsavage on 2012-09-14
You'll have to give me a bit more to go on ..... what machine do you have and what ISO are you trying to boot ... or is this on an installed system?

---

### Post by Eudaimon on 2012-09-14
I'm working off of an old Mac Powerbook G4 running 10.4.11 512 MB DDR2 SDRAM.  I'm essentially trying to completely erase my old Mac OS and replace it with a Ubuntu so that it runs faster.  It's not an essential laptop, I'm using it as a secondary computer.  I don't have anything on the Mac that I need so I can completely install a new OS and wipe the entire mac without worry. 

I'm trying to load Ubuntu from a USB.   I've wiped the USB using DiskUtility as MS-FAT,  copied ubuntu-12.04.1-desktop-i386.iso onto it, as well as your 3 files (grub.img, ofboot.b, grub.cfg).  Starting in OpenFirmware, I followed your instructions below.  It boots into a black screen, but then when I change the filename as you instructed, it says:

[COLOR=Red][I]error: file not found
error: you need to load the kernel first[/I][/COLOR]

And then it gets into the loopback loop thing. From the loopback window I'm lost.  Thanks again for your quick response.  Cheers!  Eudaimon

---

### Post by rsavage on 2012-09-14
> **Eudaimon said:**
> I'm essentially trying to completely erase my old Mac OS and replace it with a Ubuntu so that it runs faster. 
You'll probably find Ubuntu 12.04 slower (it is designed for modern hardware).  Try Lubuntu or Xubuntu.
 
> 
copied ubuntu-12.04.1-desktop-i386.iso onto it

You need a PowerPC iso. See [https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads) .

---

### Post by Eudaimon on 2012-09-15
Savage, thanks for the update will try again on Monday.  Thanks for the great help!

---

### Post by Eudaimon on 2012-09-19
Savage, 

I'm back to testing the install on a Powerbook G4.  I got hung up on the starting pbbuttonsd prompt, but I found  another thread which mentioned an attempt to install 10.4 which ran  well, trying that now.

also trying the mini installer

---

### Post by Eudaimon on 2012-09-19
Savage, grub worked with Ubuntu 10.04 on my power pc.  Posting from 10.04 now, and over the next few days I'll try to switch over to Lubuntu. 

Thanks for all your help!

---

### Post by Eudaimon on 2012-09-24
Savage,  I'm still trying to load Lubuntu 12.04 on my powerpc Powerbook G4.  I've got the b43.blacklist=yes parameter working, which puts me into the installer, but it freezes on reboot.  

I've tried almost every workaround: 
~$ sudo apt-get install b43-fwcutter firmware-b43-installer
~$ sudo modprobe -r b43 ssb ~$ sudo modprobe b43
 
and many others.  Recently I actually did a successful reboot by following:
sudo leafpad /etc/modprobe.d/blacklist.conf

and put a # in front of the b43 line.  But then upon reboot it hung again.

I think I'm just going to go back to Ubuntu 10.04 and leave it there.  No Lubuntu for me.

---

### Post by rsavage on 2012-10-28
Below are the menu entries for a grub.cfg that should work with the mini.iso (although I haven't tested).  Just download the correct version of the mini.iso (32 or 64) from here [http://cdimage.ubuntu.com/netboot/precise/](http://cdimage.ubuntu.com/netboot/precise/) and use the ofboot.b and grub.img files from post #1.   

```

menuentry "Install" {
  set root=(grubdevice,1)
  set isofile="/mini.iso"
  loopback loop $isofile 
  linux (loop)/vmlinux root=/dev/ram ro --
  initrd (loop)/initrd.gz
}
   
menuentry "Expert" {
  set root=(grubdevice,1)
  set isofile="/mini.iso"
  loopback loop $isofile 
  linux (loop)/vmlinux root=/dev/ram priority=low ro --
  initrd (loop)/initrd.gz
}
   
menuentry "Cli" {
  set root=(grubdevice,1)
  set isofile="/mini.iso"
  loopback loop $isofile 
  linux (loop)/vmlinux root=/dev/ram tasks=standard pkgsel/language-pack-patterns= pkgsel/install-language-support=false ro --
  initrd (loop)/initrd.gz
}

menuentry "Cli-expert" {
  set root=(grubdevice,1)
  set isofile="/mini.iso"
  loopback loop $isofile 
  linux (loop)/vmlinux root=/dev/ram tasks=standard pkgsel/language-pack-patterns= pkgsel/install-language-support=false priority=low ro --
  initrd (loop)/initrd.gz
}
 
menuentry "Rescue" {
  set root=(grubdevice,1)
  set isofile="/mini.iso"
  loopback loop $isofile 
  linux (loop)/vmlinux root=/dev/ram rescue/enable=true ro --
  initrd (loop)/initrd.gz
}  

```

---

### Post by rsavage on 2012-10-28
You don't have to create a new grub.cfg file.  Once grub has booted just drop to a command line (you may have to press 'c'), then type what is in the menuentry you want.  For example, for the 'install' option just type:

```

set root=(grubdevice,1)
set isofile="/mini.iso"
loopback loop $isofile 
linux (loop)/vmlinux root=/dev/ram ro --
initrd (loop)/initrd.gz

```

To make it boot, type:

```

boot

```

If you've just downloaded the vmlinux and initrd.gz files (as explained in post #2) then you would type:

```

set root=(grubdevice,1)
linux /vmlinux root=/dev/ram ro --
initrd /initrd.gz
boot

```

Again, make sure you are using the correct version - powerpc for G3/G4 and powerpc64 for G5 - [http://ports.ubuntu.com/dists/precise/main/installer-powerpc/current/images/](http://ports.ubuntu.com/dists/precise/main/installer-powerpc/current/images/)

---

### Post by rsavage on 2012-10-28
One final thing, that I don't think I've yet said on this thread, is that grub on PowerPC doesn't like the arrow keys being held down.  Single presses only!!

If you use grub2 on an installed system then it looks a lot better than the basic interface I've used in the grub.img.

If you are using a kubuntu/lubuntu alternate ISO with the hd-media vmlinux/initrd.gz files then you may need to ammend the 'Install' option commands to something like this:

```

set root=(grubdevice,1) 
linux /vmlinux root=/dev/ram file=/cdrom/preseed/kubuntu.seed FRONTEND_BACKGROUND=original quiet ro -- 
initrd /initrd.gz
boot

```I haven't used the alternate ISOs from lubuntu/kubuntu in this way so this is just speculation!

---

### Post by rsavage on 2012-11-09
Please ignore post #11!!!! (For some reason I can't edit it)

I wrote it without actually looking at the mini.iso contents - and they are a lot different to what I thought!

Here is what the first menuentry should be:

```

menuentry "Install" {   
   set root=(grubdevice,1)   
   set isofile="/mini.iso" 
   loopback loop $isofile    
   linux (loop)/install/netboot-linux root=/dev/ram ro -- 
   initrd (loop)/install/netboot-initrd.gz 
}

```Note there is no vmlinux file, but it is called /install/netboot-linux instead.  Similarly initrd.gz needs renaming in post #11.

---

### Post by reem98 on 2013-01-26
Hey guys I'm new to the ubuntu thing but I got it working off my usb drive on a powerbook G4 using grub's files and a version of 10.04 desktop powerpc. I couldn't get my G4 to boot off of a disk so I went to the USB drive. Now when I go to install it on my pc it wants to put the image back on my jump drive, and I can't see my hard drive or my CD drive.  Should I be able to at this point??? I got this G4 as a leftover from work so I cant say for certain if the HD is even good but I do here it crunching a bit on startup.
How do I get Ubuntu onto my pc's hard drive and not back on my jump drive.
Thanks

---

### Post by ferdynator on 2013-03-11
hi rsavage, first of all ty for you efforts. I've been trying to get ubuntu 12.04 running on my old Powerbook G4 for some time now. Lately i had Kubuntu 11.10 installed but when i upgraded to 12.04 it stopped working. Since i want Xubuntu anyways I am now trying to re-install the new version. I've downloaded the mini.iso and you grub files. I have no problem booting into grub. It all works fine. But it instantly drops me into the grub console. No nice menu. I actually have no idea how to proceed. I have modified the grub.cfg as u described in #12. But still only the console.  Could you walk me through my next steps? I have also tried yaboot but i cant even load yaboot correctly and i also like grub2 way better :)  sincerely FRED

---

### Post by rsavage on 2013-03-11
You need to follow the advice in post 14.  I got the location of the files wrong in 11 and 12.  Stupidly I wrote the posts without looking at the iso and haven't got the ability to edit posts in this thread for some reason.  

I haven't made menu entries for the mini/alternate iso's so you would need to type out the instructions.

Once at a grub console the commands would be 

```

set root=(grubdevice,1)       
set isofile="/mini.iso"     
loopback loop $isofile        
linux (loop)/install/netboot-linux root=/dev/ram ro --     
initrd (loop)/install/netboot-initrd.gz 
boot

```


The only problem would be the partitioning of your usb device.  Sometimes I've had to use just

```

set root=(grubdevice)

```

If you type

```

ls

```
Then you'll get a list of your partitions.

If you want the menu then use something like this (can't remeber exactly, ammend for your partition)

```

configfile (grubdevice)/grub.cfg

```

---

### Post by ferdynator on 2013-03-13
this worked like charm! Installing right now. Ty again for your efforts. I'll let you know if it worked. // edit: i used root=(grubdevice) instead of root=(grubdevice,1)

---

