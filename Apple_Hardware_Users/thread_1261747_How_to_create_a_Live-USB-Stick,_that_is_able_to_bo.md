---
title: "How to create a Live-USB-Stick, that is able to boot a Mac"
date: 2009-09-09
forum: Apple Hardware Users
---

### Post by produnis on 2009-09-09
Hi folks,

does anyone know how to create an Ubuntu-Live-USB-Stick, which is able to boot a Mac?

I have several Intel-Macs here, they all have rEFIt installed, and they all have both OSX and Ubuntu Jaunty.

If I create a Live-Stick using unetbootin or the usb-creator, I am not able to boot my Mac from that stick.
rEFIt recognizes the stick as bootable, but if I select it, it
a) stops the boot process by saying something like "Apple's firmware is not good to support booting legacy-OS"
b) makes the stick blinking for a short time, and then boots Ubuntu from my HD

(Whether it is a) or b) is dependened to the stick's filesystem:  FAT leads to a)  and HFS leads to b)...)

I tried to format the usb-stick as hfs+ with and without journaling, but won't solve my problems.

Does anybody know how to create a Live-Stick that works on Intel-Macs?

---

### Post by barnex on 2009-09-09
I've had no luck with this. USB boot needs to be supported by the hardware, and I have the impression that at least my macbook does not have this support. I've tried several ways to make the USB disk and although it boots well on a Dell and Asus Eebox, it doesn't on my macbook :( ...

---

### Post by produnis on 2009-09-09
This is remarkable,

as in general the mac is able to boot from a usb stick.

I copied my SnowLeo-Install-DVD to a USB-stick, and my Mac boots from that USB-Stick without any problems...
So, that works fine...

...but creating an UBUNTU-Stick seems to be a great problem...

---

### Post by produnis on 2009-09-10
I already installed Ubuntu to every Mac I got here, and every Mac is able to boot Ubuntu using rEFIt.

Is it possible to use these Ubuntu-Installations to boot from USB-Stick?

I am thinking about an entry in GRUB2 that shows something like "Boot from USB-Stick"...

Does anyone know how to configure GRUB2 to do so?

---

### Post by pxwpxw on 2009-09-10
> **produnis said:**
> I already installed Ubuntu to every Mac I got here, and every Mac is able to boot Ubuntu using rEFIt.

Is it possible to use these Ubuntu-Installations to boot from USB-Stick?

I am thinking about an entry in GRUB2 that shows something like "Boot from USB-Stick"...

Does anyone know how to configure GRUB2 to do so?

Copy from  the usb /boot directory, the 2 kernel files = vmmlinuz... and initrd.img... 
 Copy them to your internal HD linux partition root and rename them usbvmlinuz, usbinitrd.img. (name can be anything). ( Or alternately copy to your OSX partition via another usb stick or partition  readable from OSX).

Then if your usb root is at /dev/sdb2 -
    make a grub2 menuentry 
```

menuentry "usb " {
 search --set -f /usbvmlunuz
 linux /usbvmlinuz root=/dev/sdb2
 initrd /usbinitrd.img
}

```

(The catch is , if you upgrade kernel, you need to copy again to the internal HD.)

You can only boot directly from external using an EFI bootloader, that is what OSX does.

---

### Post by produnis on 2009-09-10
Thanks for that!!!

I am a little bit confused, I just figured out that I have GRUB 0.97 - and not GRUB2 - , so
I used [this tutorial]("http://ubuntuforums.org/showthread.php?t=992426"), and it works fine...

> **pxwpxw said:**
> You can only boot directly from external using an EFI bootloader, that is what OSX does.
But currently, there seems to be no way to create an UBUNTU-Live stick, that uses an EFI bootloader an is able to directly boot a mac, right?

---

### Post by pxwpxw on 2009-09-10
> **produnis said:**
> Thanks for that!!!

I am a little bit confused, I just figured out that I have GRUB 0.97 - and not GRUB2 - , so
I used [this tutorial]("http://ubuntuforums.org/showthread.php?t=992426"), and it works fine...


But currently, there seems to be no way to create an UBUNTU-Live stick, that uses an EFI bootloader an is able to directly boot a mac, right?

The grub-efi attacehed bootusb.tar.gz  will do it.

You need a USB stick 2GB or more, partitioned as MSDOS with one full sized FAT32 partiton (most come like that). I use 8GB.
```

Download and extract the 
      /efi folder which has -

      /efi/boot folder with 3 files -

      /efi/boot/ bootx64.efi	bootx64.icns	grub.cfg

```

Copy the /efi folder to the USB fat32 partition.

Copy a ubuntu-9.04-desktop-amd64.iso to the USB (do not extract it just copy the .iso file (see the grub.cfg to match the name).

If your Mac is recent model with 64bit EFI, you should see an EFIBoot icon when starting up with Option key, or with refit.

You will probably have to experiment with the grub.cfg menu choices and config, but they should boot the ubuntu iso kernel. The grub.cfg has other menuentries for Slax also, easy to boot for a start. 

For 32bit EFI Mac models (MB21 or earlier), 
"bootx64.efi" needs to be renamed to "bootia32.efi" in order to see the Apple startup icon without needing refit.

Still needs some tidying up, that should do for a test.

Refer to these posts in grub2 EFI bootloader thread for some more info 
 #919 Booting ubuntu live iso with grub.efi 
 #930 grub2404b.efi (used for bootx64.efi or bootia32.efi )
 #992 UEFI spec reference.

---

### Post by produnis on 2009-09-10
I CANNOT BELIEVE IT!!

IT WORKS IT WORKS IT WOKRS!!!
:guitar::popcorn::guitar:

Thank you so much for this,
I tried it for about 3 days now to get this working !!!!

I will translate your tuto for the german ubuntuusers-wiki!

Am I allowed to share your attachment [bootusb.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=128096&d=1252588717") there?

---

### Post by 17844 on 2009-09-10
I have a MBA Revision B and I have no luck using the bootefi files above, I do see the USB drive when booting with option key pressed, but choosing it throws me to standard OSX boot.

I have also tried renaming to 32bit name but then the drive does not even show up in the boot menu.

Any ideas?

Thanks so much for all your help guys!

---

### Post by produnis on 2009-09-10
> **17844 said:**
> 
Any ideas?

Have you tried to install [rEFIt]("http://refit.sourceforge.net/")? This might help you to boot from the usb-device...
hmm..

---

### Post by 17844 on 2009-09-10
Do you suggest installing rEFIt on the USB stick or the HD? I will try installing it on the memstick and see if it makes a difference.

BUT from the post above I was under the impression that rEFIt was not needed - always nice to keep it slim.

My main goal was to not install any bootloaders on the built in HDD at all, leaving it unchanged and just play with the mem stick.

Thanks for the input

---

### Post by produnis on 2009-09-10
I ment installing rEFIt at the HDD - not the stick!

But you are right, it should work without refit...

---

### Post by pxwpxw on 2009-09-10
You could try another grub64.efi from post #844 in the grub.efi thread and use rEFIt to start it, may show more info. 
 
[http://ubuntuforums.org/showpost.php?p=7598685&postcount=844](http://ubuntuforums.org/showpost.php?p=7598685&postcount=844)

Or try another download of bootusb.tar.gz - could be an error somewhere in unzipping.

---

### Post by produnis on 2009-09-10
After the enthusiastic peak I again faced reality...
:-)

The sticks boots from my MacPro without problems.

But on my MacbookPro4,1  it just shows the red menu. From there, I get no X.
The red menu remains on the screen, but I am able to type commands in (which are not shown at my screen)...

If I choose boot-option B (fbdev), then ubuntu boots into a console. I am not able to access the GNOME display manager...

I tried grub.refi from #844, but there is the same result....

Do you have any hints on how to set some proper graphic-variabels?

---

### Post by pxwpxw on 2009-09-10
> **produnis said:**
> After the enthusiastic peak I again faced reality...
:-)

The sticks boots from my MacPro without problems.

But on my MacbookPro4,1  it just shows the red menu. From there, I get no X.
The red menu remains on the screen, but I am able to type commands in (which are not shown at my screen)...

If I choose boot-option B (fbdev), then ubuntu boots into a console. I am not able to access the GNOME display manager...

I tried grub.refi from #844, but there is the same result....

Do you have any hints on how to set some proper graphic-variabels?

That is just part 2 of setting up for EFI booting, which is not so simple as grub-pc bios booting. Needs to be taken in steps.
With EFI booting, there may be more setting up needed in linux for X.

If grub-efi is getting to the grub menu, the remaining issue is with configuring to suit the Mac model, mostly with the graphics, the kernel version and the linux distribution.
The grub.efi in the package has all the modules needed for MBP4,1 which I have used to test here, if it is showing the menu, that is enough, so stay with the package. 

Other setting up varies between macs and linux versions. There are also menuentry options to help, see grub wiki "Testing on MacBook" (ref listed post#1 grub2 EFI thread).

The desktop main problem is getting X to run initially because some cases need the xorg fbdev driver with the video=efifb linux command line option. So you have to edit /etc/X11/xorg.conf to use Driver "fbdev" in the Section "Device" like this -

Section "Device"
 ...
 Driver "fbdev"
 ...
EndSection

This is the case with nvidia graphics on MBP41.

If you get to a linux text console you can edit /etc/X11/xorg.conf, using
```

 $ sudo nano /etc/X11/xorg.conf

```
Then restart  X server,  by doing
```

 $ sudo /etc/init.d/gdm restart

```

or 
you can add the option  "single" to the menuentry linux command line, which will stop at a root console.

Then use nano to edit /etc/X11/xorg.conf, exit and resume to continue to desktop.

When that is fixed, you will need to add peristence and small start up script (I can provide) to make it automatic. That is another step needed for the the live system.

If you try a Slax iso, it is easier because it stops at a root command line, and has a xorg.conf-fbdev you can just copy to xorg.conf.
For Slax -
```

# cd /etc/X11
# cp xorg.conf-fbdev xorg.conf
# cd -
# telinit 4

```
Also can use a script to do this with persistence.

---

### Post by pxwpxw on 2009-09-11
The MacBook Air Rev. B late 2008 has nvidia graphics, so the same comments on configuration as for MBP4,1 above should apply.
Get the exact MacBook Air Model (2,1 ?) from OSX "About this mac:More:Model Name" andthe graphics ID under "Graphics/Displays: Chipset Model"

However if the MBAir also has firmware using the Graphics Output Protocol (Gop), it can possibly use the nvidia driver with different configuration (this is the case for some MBPro5x ). This can be checked if rEFIt is installed - it is shown in the "About refit" icon info, the earlier version firmware has UgaDraw as for MBP4,1.

---

### Post by Flavian on 2009-09-11
Hi guys.
I've been fiddeling around with that for days now.
I am trying what you posted about the EFI package.

Anyway, my question is if there is a way to set up an ubuntu live system on a thumb drive that is being able to be booted from either a PC or a MAC without having to change anything on the thumb drive before.
The reason I ask is, because I want a kind of rescue / backup / live system that I can carry around with me, that would be able to be booted from either a mac or a pc.

Thanks in advance.
Flo

---

### Post by produnis on 2009-09-11
> **pxwpxw said:**
> 
When that is fixed, you will need to add peristence and small start up script (I can provide) to make it automatic.
Thank you very much for your time!!
It works the way you described it.

I am very interested in a little start-up script!
:)

---

### Post by pxwpxw on 2009-09-11
> **Flavian said:**
> Hi guys.
I've been fiddeling around with that for days now.
I am trying what you posted about the EFI package.

Anyway, my question is if there is a way to set up an ubuntu live system on a thumb drive that is being able to be booted from either a PC or a MAC without having to change anything on the thumb drive before.
The reason I ask is, because I want a kind of rescue / backup / live system that I can carry around with me, that would be able to be booted from either a mac or a pc.

Thanks in advance.
Flo
USB stick Booting from PC and Mac -

It could probably be done, not too difficult to try if you had success booting Mac with the package above.

First set up a USB Live for PC booting, use Live USB Creator or something like that for Ubuntu and get it going for PC which uses syslinux ( or Slax for testing the idea might be easier to do at first). 
That installs files extracted from an iso to a FAT32 partition on a MSDOS drive 

Then just install the /efi  boot files from the package, in the root of  the FAT32 partition as above. That should boot to the grub-efi boot menu (grub.cfg) on an intel Mac EFI, without conflicting with PC boot files. Then it will need grub.cfg menuentry to boot the /casper vmlinuz and initrd, with live options and additional efi options for the Mac. 

The grub.cfg in the package is for booting  loop mounted iso, so the menuentry would be different, actually simpler.

(It is also possible to boot loop mounted iso on PC, but needs grub2-pc )

---

### Post by pxwpxw on 2009-09-11
> **produnis said:**
> Thank you very much for your time!!
It works the way you described it.

I am very interested in a little start-up script!
:)

I will get it for you (soon).

Have you got persistence running (casper-rw), if so, save a copy of your edited xorg.conf in /etc/X11/xorg.conf-fbdev, the script assumes that it exists.

(thats for ubuntu, or do you mean Slax?)

---

### Post by produnis on 2009-09-11
> **pxwpxw said:**
> I will get it for you (soon).

Have you got persistence running (casper-rw), if so, save a copy of your edited xorg.conf in /etc/X11/xorg.conf-fbdev, the script assumes that it exists.

(thats for ubuntu, or do you mean Slax?)

Yes, I need it for UBUNTU

I havn't tried the "persistence"-flag yet.

Do I understand it right that with this flag all changes are saved to the stick?

---

### Post by pxwpxw on 2009-09-11
> **produnis said:**
> Yes, I need it for UBUNTU

I havn't tried the "persistence"-flag yet.

Do I understand it right that with this flag all changes are saved to the stick?

This should do I hope, you will have to install the script manually. 

swxconfig - use xorg.conf-fbev for xorg.conf.

If the linux command line includes fbdev, swxconfig will use xorg.conf-fbdev for xorg.conf. (so you can control it from the grub.cfg menuentry).
Ubuntu Live rewrites xorg.conf at each start.
-----------------
You need to have persistemce set up  casper-rw installed and checked, with the linux command line "persistent" option, so that this will be saved. Refs on persistence and casper-rw include pendrive linux site and ubuntu wiki.
------------------
Restart with persistent option.

Copy and save this code as swxconfig in ubuntu home directory

```

#!/bin/sh
# swxconfig
 cd /etc/X11
 grep fbdev /proc/cmdline >/dev/null && cp xorg.conf-fbdev xorg.conf


```

Then using terminal command line, install swxconfig as in example below.

 Make it executable and copy it to /etc/init.d/
```

ubuntu@ubuntu:~$ cd
ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# chmod +x swxconfig 
root@ubuntu:/home/ubuntu# cp swxconfig /etc/init.d/

```

Make a sym link /etc/rc2.d/S20swxconfig
```

root@ubuntu:/home/ubuntu# cd /etc/rc2.d/
root@ubuntu:/etc/rc2.d# ln -s ../init.d/swxconfig S20swxconfig
root@ubuntu:/etc/rc2.d# cd
root@ubuntu:~# 

```

Check all correct -
```

ubuntu@ubuntu:~$ ls -l /etc/init.d/swxconfig 
-rwxr-xr-x 1 root root 105 2009-09-11 14:44 /etc/init.d/swxconfig
ubuntu@ubuntu:~$ ls -l /etc/rc2.d/S20swxconfig 
lrwxrwxrwx 1 root root 19 2009-09-11 14:24 /etc/rc2.d/S20swxconfig -> ../init.d/swxconfig
ubuntu@ubuntu:~$ 

```
Note - Slax or Fedora use different start up scripts.

---

### Post by produnis on 2009-09-11
Thanks again for your time, your help and the script..

...unfortunately, there seems to be a problem with the persitence-flag

I booted the stick with persistance and fbdev (using boot option "C" of grub.cfg that comes with your tar.gz attached to the first page of this thread)
...but if I reboot from stick, the script and all the changes are gone...

So, it looks like it wont write the changes down to the stick....
:(

---

### Post by pxwpxw on 2009-09-12
> **produnis said:**
> Thanks again for your time, your help and the script..

...unfortunately, there seems to be a problem with the persitence-flag

I booted the stick with persistance and fbdev (using boot option "C" of grub.cfg that comes with your tar.gz attached to the first page of this thread)
...but if I reboot from stick, the script and all the changes are gone...

So, it looks like it wont write the changes down to the stick....
:(

Maybe something is missing.


Persistent ubuntu live uses casper-rw on the stick (but also possible to have it on HD ).
The linux command line must include  "persistent" without the quotes.
I can confirm that it is working on MBP41 on USB stick right now.

Here is setting up 512MB casper-rw for ubuntu persistence from ubuntu live running on the stick, I also have slaxper.dat for slax live. You can also do it from another linux by mounting the usb stick /dev/sdb1 on /xxx. 

Ubuntu live mounts the stick FAT32 partition on /isodevice
```

ubuntu@ubuntu:~$ mount | grep /sd
/dev/sdb1 on /isodevice type vfat (rw,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1)
ubuntu@ubuntu:~$ 

```
To create casper-rw
```

ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# cd /isodevice 
root@ubuntu:/isodevice# dd if=/dev/zero of=casper-rw bs=1M count=512
root@ubuntu:/isodevice# mkfs.ext3 -F casper-rw 

root@ubuntu:/isodevice# ls -l

-rwxr-xr-x 1 root root 536870912 2009-09-09 12:03 casper-rw
drwxr-xr-x 3 root root      4096 2009-09-09 21:48 efi
-rwxr-xr-x 1 root root 209762304 2009-08-20 22:49 slax-6.1.2.iso
-rwxr-xr-x 1 root root 536870912 2009-09-09 12:06 slaxper.dat
-rwxr-xr-x 1 root root        59 2009-09-09 13:40 swxconfig
-rwxr-xr-x 1 root root 730554368 2009-08-01 12:38 ubuntu-9.04-desktop-amd64.iso

root@ubuntu:/isodevice# cd
root@ubuntu:~# 

```

Then make sure you have "persistent" in the menuentry linux commandline for all restarts.

To check state of casper-rw  -
```
 
ubuntu@ubuntu:~$ dumpe2fs -h /isodevice/casper-rw 

```

---

### Post by produnis on 2009-09-12
YOU ARE A HERO, pxwpxw,

I works now!!!

Thank you so much for your patience... :-)

:popcorn:

---

### Post by vonlaken on 2009-09-12
I used another method of booting in any 32/64 bit enviroment, that doesn t requiere to modify the OSX partitiion or  your hard drive at all......

[http://ubuntuforums.org/showthread.php?t=1194649](http://ubuntuforums.org/showthread.php?t=1194649)

good luck

---

### Post by produnis on 2009-09-14
Just to have it complete:  
Does anyone made the karmic-Alpha5 to boot from USB-Stick?

I downloaded the latest karmic-desktop-amd64.iso, and I modified my grub.cfg to fit the ISO-Filename, and I modified initrd.gz to initrd.lz (as this is the filename within the ISO)...


While booting from CD is no problem,
booting from USB leaves the GRUB2-Menu showing that intitrd was found and after that doing nothing...(the usb-stick's led isnt blinking anymore)

---

### Post by pxwpxw on 2009-09-14
> **produnis said:**
> Just to have it complete:  
Does anyone made the karmic-Alpha5 to boot from USB-Stick?

I downloaded the latest karmic-desktop-amd64.iso, and I modified my grub.cfg to fit the ISO-Filename, and I modified initrd.gz to initrd.lz (as this is the filename within the ISO)...


While booting from CD is no problem,
booting from USB leaves the GRUB2-Menu showing that intitrd was found and after that doing nothing...(the usb-stick's led isnt blinking anymore)

Same here, on MBP41 I have had no good efi results with karmic, varies with the alpha. Currently kernel 2.6.31-9 dies after [Initrd, ..... ]. when booting from the loop mounted iso.
However on MB21 (intel graphics) it gets startup text to a root console after a lot of errors, then has problems and aborting X.
I am not going to try to make it work.

It is some sort of regression in kernel or initrd affecting efi, since Ubuntu904-amd64 is fine, and early karmic booted from elilo.efi, but no longer does. Not worth pursuing until PC booting is bug free.
I will wait until the Karmic release to see if there is still a problem with efi. I already reported the elilo.efi bug with transition to the 2.6.31 kernel.

---

### Post by produnis on 2009-09-14
thx for the info!!!

I do agree that bugfixing an alpha-release would be a waste of time...

let's see how the final version does...

---

### Post by produnis on 2009-09-21
It works now with Alpha6! :-)

---

### Post by produnis on 2010-04-23
Unfortunately,
this method no longer works with LucidLynx...
:(

---

### Post by porg on 2011-07-06
Did not work for me with the following HW and SW.

MacBookPro2,2
8 GB USB Flash Drive SanDisk Cruzer Contour (0x0781 0x540e)

/ubuntu-11.04-desktop-i386.iso
/efi/boot/ bootx32.icns bootx32.efi (renamed from "64")

I came until the grub boot loader selection screen.

Tried all methods:
```
A ubuntu-11.04-desktop-i386.iso
B ubuntu-11.04-desktop-i386.iso fbdev
C ubuntu-11.04-desktop-i386.iso fbdev persistent
```

Tried "grub.conf" with and without the modifier "fix_video". Changed initrd.gz to initrd.lz as I read that this changed somewhen after Ubuntu 9.

With "fix_video" the screen remained as-is for about 40 seconds, then changed into weird output, but I guess the system was not stuck, as key input altered the weird mosaic, which likely was a CLI prompt.

Without "fix_video" and with "fbdev" it booted in console output mode and got stuck with the error message:

```
fb: conflicting fb hw usage radeondrmfb vs EFI VGA - removing generic driver
```

---

### Post by mulbric3 on 2011-11-18
I cannot get this to work on my MBP 3,1 with Ubuntu Oneric.

I'm getting told, that the kernel has to be loaded. What do I do?

---

### Post by Khayyam on 2012-01-24
mulbric3, porg, produnis, pxwpxw ..

I had some trouble with >9.04 but after some trial-and-error was able to boot 11.10 with the following setup.

In my case (Macbook1,1) the missing ingredient was to pass the 'noefi'  switch, without this I could boot (grub2-efi), select the grub entry  etc, but the machine would re-boot once the initrd was loaded.

My current setup:

2GB USB Key partitoned with 1 x 20MB HFS+ (non-journaled) and 1 x 1.9xGB MSDOS. The partition scheme is MBR.

On the HFS+ is grub2-efi (from [this post](http://ubuntuforums.org/showpost.php?p=7926629&postcount=7)):
/efi/boot/bootia32.efi
/efi/boot/grub.cfg

The grub2-efi was blessed (from an OS X install):
```
sudo bless --folder /Volumes/hfsp/efi --file /Volumes/hfsp/efi/boot/bootia32.efi
```[COLOR=DarkRed]Note: [COLOR=Black]'hfsp' is the volume  name of the HFS+ partition on the USB stick. The name shouldn't matter,  but adjust the above command to reflect your particular setup.[/COLOR][/COLOR]
[COLOR=DarkRed]Note:[COLOR=Black] the machine this was tesed on is a Macbook1,1 hence the [/COLOR][/COLOR]bootia32.efi, for 64bit machines the file would be named bootx64.efi.
[COLOR=DarkRed]Note: [COLOR=Black]I'm not using rEFIt, but it shouldn't matter if you are.
    
  [/COLOR][/COLOR]The MSDOS partition holds the iso's. Currently I've been able to boot:

ubuntu-11.10-desktop-i386
ubuntu-rescue-remix-11-10
systemrescuecd-x86-2.4.1

[COLOR=Black]I imagine the ubuntu-11.10-desktop-amd64+m[/COLOR]ac  will work similarly, there may be some hardware specific switches and/or  grub2-efi options you need to pass but these you should be able to work  out from other posts. Again, in my own case (Macbook1,1) it was only a  matter of adding the 'noefi' switch to the examples given previously in  this thread that got 11.10 to boot, so I don't think there is anything  inherently broken (or as pxwpxw stated 'breaks efi') with >9.04  releases.

My grub.cfg:
```
timeout=20
default=0
set F1=ctrl-x

menuentry "Search (and boot) MacOS X" {
 search --set -f /usr/standalone/i386/boot.efi
 chainloader /usr/standalone/i386/boot.efi
}
menuentry "Ubuntu 11.10 Desktop-i386 (Macbook1,1)" {
 fix_video
 fakebios
 search --no-floppy --set -f /ubuntu-11.10-desktop-i386.iso
 loopback loop /ubuntu-11.10-desktop-i386.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/ubuntu-11.10-desktop-i386.iso video=efifb acpi=force noefi quiet splash --
 initrd (loop)/casper/initrd.lz
}
menuentry "Ubuntu Rescue Remix 11.10 (Macbook1,1)" {
 fix_video
 fakebios
 search --no-floppy --set -f /ubuntu-rescue-remix-11-10.iso
 loopback loop /ubuntu-rescue-remix-11-10.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/ubuntu-rescue-remix-11-10.iso video=efifb acpi=force noefi quiet splash --
 initrd (loop)/casper/initrd.gz
}
menuentry "SystemRescueCD-x86 2.4.1 (Macbook1,1)" {
 fix_video
 fakebios
 search --no-floppy --set -f /systemrescuecd-x86-2.4.1.iso
 loopback loop /systemrescuecd-x86-2.4.1.iso
 linux (loop)/isolinux/rescuecd docache setkmap=us isoloop=systemrescuecd-x86-2.4.1.iso --
 initrd (loop)/isolinux/initram.igz
}
menuentry "CD" {
   appleloader CD
}
menuentry "MBR1" {
   appleloader HD
}
menuentry "REBOOT" {
    reboot
}
```[COLOR=DarkRed]Note: [/COLOR]The 'fix_video' grub2-efi option is  for the Macbook1,1 GMA950 (Intel Graphics Chip). I don't think this is  necessary for other chipsets (though pxwpxw will be able to clarify).
[COLOR=DarkRed]Note: [COLOR=Black]Passing the 'toram' option on the Ubuntu entry will load the OS into RAM, which makes operation, access times, etc, considerably faster, also, loading to RAM means the USB stick can be removed once booting is completed [[COLOR=DarkRed]EDIT[COLOR=Black][COLOR=DarkRed] .. I've removed the 'toram' option in the above grub.conf as /isodevice remains mounted, and have read that this can cause a problem with the installer if its not --force umounted[/COLOR]][/COLOR][/COLOR]. The 'docache' option on the SystemRescueCD entry does the same, and I imagine 'toram' could be used with Ubuntu Rescue Remix (untested). These options require that there is enough RAM to load the filesystem in memory, which shouldn't be a problem for most Mactel machines, however, if your limited in that regard you can remove this option and have the OS run from the USB stick. 
    [COLOR=DarkRed]Note: [COLOR=Black]the 'quiet splash'  switches will cause the boot messages to be replaced with a Ubuntu  'splash' logo, you might want to remove these should you want to see boot messages and/or for troubleshooting.
        
Please report success/failure and any specific changes you made for your particular hardware.

mulbrick3: This error sounds like the bootloader can't find vmlinuz (linux kernel), this is most probably to do with how you specify its location in the grub.cfg, but without more details I can't tell.

porg: I'm not familiar with the various Radeon issues, however, try passing 'video=efifb' along with, or in place of, 'fbdev'. This "should" resolve the conflict as the card would be assigned to efifb and so the radeon driver would skip it.

Links:
[System Rescue CD]("http://www.sysresccd.org")
[ Ubuntu Rescue Remix]("http://ubuntu-rescue-remix.org/") 
[/COLOR][/COLOR][/COLOR][/COLOR]

---

### Post by undoIT on 2012-02-25
The easiest way I found to create a bootable USB install disk that works for Mac UEFI is to use dd. I tried several different methods for creating a bootable USB disk for the daily build of Ubuntu 12.04 to use on my MacBook Air 4,2 and none of them worked except for this.

```
sudo dd if=/PathToDownloadedISO/precise-desktop-amd64+mac.iso of=/dev/sd?
```

Of course you need to replace the path and device info in the above snippet. This would also work for Ubuntu 11.10 (if you want to use the current stable version). As an example, if you downloaded Ubuntu 11.10 to your Downloads folder and your USB drive is mounted to /dev/sdc, the command would look like this:

```
sudo dd if=~/Downloads/ubuntu-11.10-desktop-amd64+mac.iso of=/dev/sdc
```

You can find out where your USB drive is mounted by opening Disk Utility, selecting the drive in the left column, and then checking what is listed after "Device:"

---

### Post by undoIT on 2012-03-04
Another thing I discovered is that the amd64+mac does not include true EFI booting. If you install with that image, you'll get a hybrid MBR.

It is best to just download the regular ISO. I was able to successfully boot with EFI (insert USB, hold down option key after power on and then select EFI boot). This installs in a way that Ubuntu is booting with pure EFI using UNetbootin to create the Live USB. You'll know it worked if you get a grub menu after installation. If you want to boot into OS X, just hold down the option key during boot and select the OS X disk. Booting into Ubuntu is much faster with pur EFI and there is no need to use rEFIt either :)

---

### Post by psycato on 2012-03-21
> **Khayyam said:**
> mulbric3, porg, produnis, pxwpxw ..
[COLOR=DarkRed][COLOR=Black][COLOR=DarkRed][COLOR=Black]
Please report success/failure and any specific changes you made for your particular hardware.
  
[/COLOR][/COLOR][/COLOR][/COLOR]

Im having some trouble getting my macbook air, 2010 booting with your setup.
Error msg:

Unknown graphic card: 8a210de (guessing this is because of either fix_video or video=efifb, and not really relevant)
[B]ROM image present.
error: You need to load the kernel first.
[/B]
Press any key to continue...

My grub.conf:

timeout=20
default=0
set F1=ctrl-x

menuentry "Ubuntu" {
 fix_video
 fakebios
 search --no-floppy --set -f /ubuntu-11.10-desktop-i386.iso
 loopback loop /ubuntu-11.10-desktop-i386.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/ubuntu-11.10-desktop-i386.iso video=efifb acpi=force noefi splash --
 initrd (loop)/casper/initrd.lz
}

However, if I "mimic" the loopback.cfg file from boot/grub/
swap out the content of grub.conf with:

 fix_video
 fakebios
linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=${iso_path} video=efifb acpi=force noefi splash --
initrd    /casper/initrd.lz

and run it off of a regular usb, I get to the point where the following error occurs:

no filesystem could mount root, tried: ext3 ext2 ext4 fuseblk
kernel panic not syncing VFS:unable to mount root filesystem on unknownblock (1,0)

Hopefully you'll get a notification that someone posted in this (semi) old thread :)

Any pointers/help would be really appreciated!

cato

---

### Post by ts3 on 2012-04-10
dd seems to be working

Just created a live USB with the 12.04 daily build for macs (it's in beta 2 right now, a few weeks before release) that boots perfectly on a 2011 Macbook Air 11'' using rEFIt.

Created the USB on the MBA rather than on a linux laptop following mostly this [https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick](https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick)

but without the need to convert the iso image that the guide describes.  Basically I put in a disposable USB, then ran, in the MBA terminal

```
diskutil list
```to see where the usb was mounted (/dev/disk1 in my case), then unmounted the USB

```
diskutil unmountDisk /dev/disk1
dd if=path/to/downloaded/iso of=/dev/disk1 bs=1m
```Generally on linux dd requires sudo but for some reason I don't think I actually had to use it on the MBA, the mac terminal seems a bit cavalier in this respect :)

After dd ran, in about 10 minutes, there was some sort of an error pop-up window along the lines that finder couldn't read the USB.  I clicked ignore, rebooted, picked the USB in the rEFIt menu and here I am in a live 12.04 environment.  Have to do some housekeeping (free some space on the hard drive, it's only 128 GB and quite cramped at the moment) and will install ubuntu on the hard drive.

In preparation, I'd installed rEFIt a couple of days ago and, as with some users, it took a couple of reboots for the boot menu to show but it seems to be working without a hitch.  Earlier I tried to boot off an 11.10 USB but that didn't work (boot screen said no bootable device).  I am trying to remember whether I made that USB using dd and I think not.  Later I'll try to boot off an opensuse USB that I definitely made using dd to see what happens.

UPDATE:  For what it's worth, the opensuse USB would not boot on the mba; also I checked and the ubuntu usb that didn't boot previously was the 12.04 beta1 not the 11.10 (the beta1 does not have the +mac bit so I guess that's why).

---

### Post by spawanekar on 2012-12-12
I am not able to download the attachment  :icon_frown:

---

### Post by spawanekar on 2012-12-12
> **pxwpxw said:**
> The grub-efi attacehed bootusb.tar.gz  will do it.

You need a USB stick 2GB or more, partitioned as MSDOS with one full sized FAT32 partiton (most come like that). I use 8GB.
```

Download and extract the 
      /efi folder which has -

      /efi/boot folder with 3 files -

      /efi/boot/ bootx64.efi	bootx64.icns	grub.cfg

```

Copy the /efi folder to the USB fat32 partition.

Copy a ubuntu-9.04-desktop-amd64.iso to the USB (do not extract it just copy the .iso file (see the grub.cfg to match the name).

If your Mac is recent model with 64bit EFI, you should see an EFIBoot icon when starting up with Option key, or with refit.

You will probably have to experiment with the grub.cfg menu choices and config, but they should boot the ubuntu iso kernel. The grub.cfg has other menuentries for Slax also, easy to boot for a start. 

For 32bit EFI Mac models (MB21 or earlier), 
"bootx64.efi" needs to be renamed to "bootia32.efi" in order to see the Apple startup icon without needing refit.

Still needs some tidying up, that should do for a test.

Refer to these posts in grub2 EFI bootloader thread for some more info 
 #919 Booting ubuntu live iso with grub.efi 
 #930 grub2404b.efi (used for bootx64.efi or bootia32.efi )
 #992 UEFI spec reference.
could you please send me this attachment as I am not able to download it.
bootusb.tar.gz. pls send me at
spawanek at mail.usf.edu

---

### Post by fizikz on 2012-12-16
I'm currently stuck at the following errors when trying to 

```

RAMDISK: Couldn't find valid RAM dsik image starting at 0.
List of all partitions:
[bunch of hex values and partition sizes edited out next for ease of reading]
... sda   driver: sd
...     sda1 [UID]
...     sda2 [UID]
... sr0  driver: sr

No filesystem could mount root, tried: ext3 ext4 fuseblk
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(1,0)

```

Any ideas what the problem might be? 

I am using a 32GB Patriot Element USB flash drive, formatted as one FAT partition, with /efi and /efi/boot copied onto it and the Ubuntu 12.04.1 desktop iso copied to the root directory according to the explanations in this thread by pxwpxw. (Thanks for those instructions! Very helpful!)

Now the trouble seems to be in getting the grub.cfg done right. I got the furthest using Khayyam's template. My grub.cfg looks like this: 

```

timeout=20
default=0
set F1=ctrl-x

menuentry "Search (and boot) MacOS X" {
 search --set -f /usr/standalone/i386/boot.efi
 chainloader /usr/standalone/i386/boot.efi
}
menuentry "Ubuntu (Macbook1,1)" {
 #fix_video #not using Intel graphics
 fakebios
 search --no-floppy --set -f /boot.iso
 loopback loop /boot.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot.iso video=efifb fbdev noefi --
 initrd (loop)/casper/initrd.lz
}

...

```

Note: The Ubuntu iso was renamed to "boot.iso" for simplicity.

Basically it looks like I have a very similar problem to that of psycato. Any help would be appreciated!

---

### Post by mfumbesi on 2013-02-28
Came here via google. I have a iEi[SIZE=2] KINO-QM670 that I want to reflash with uBuntu. I ran to the uefi problem. I'll downloand the bootusb.tar.gz file and give it a try.
[/SIZE]

---

