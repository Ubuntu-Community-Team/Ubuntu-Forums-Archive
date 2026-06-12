---
title: "Using a Live-USB Distro...."
date: 2009-06-22
forum: Apple Hardware Users
---

### Post by vonlaken on 2009-06-22
I´ve been trying to setup a Live-usb Ubuntu on a stick, but still unable to boot from it:
Progress so far
2mb stick Partitioned in 2
      part 1, HFSPlus, Contains rEFIt 0,13 and grub2 (Version 523 from the othe thread [http://ubuntuforums.org/showpost.php?p=6966036&postcount=523](http://ubuntuforums.org/showpost.php?p=6966036&postcount=523))
      Part 2 FAT32, LiveCD INTREPID....

Booting with (Option) key pressed gets me to EFI, which recognizes grub2, and a GRUB2 cfg file or command line.

Using the following Parameters:

root (hd0,1)
video_fix
linux /casper/vmlinuz XXXXXXXXXXXXXX video=efifb
initrd /casper/initrd.gz
boot


where XXXXXXXX go multiple attempts to set up the linux root device....

I can boot the kernel and mount the initrd image, but it gets me as far as a busybox command line, and I ´ve been unable to mount the squashfs.....

Any ideas?

By the way, if you use JAUNTY, also append acpi=force to the linux kernel line, to get keyboard recognized.

---

### Post by vonlaken on 2009-06-30
Ok.... I got my macbook 2,1 to boot a live usb linux (intrepid) without modifying the OSX install at all. The pendrive will work for both macs and pc´s 

1) partition your USB pendrive (mine is 2MB) in 1 partition FAT and a second Partition HFSPlus, 20MB (the rest of the space goes in the first partition.

2) in the second partition, install rEFIt

3) Using Parallels or a PC, install boot into Intrepid and make a linux luve USB install, leaving free spcae for persistent changes if you want.

4) before exiting linux, in gparted make sure partition 2 is set to be bootable (not quite sure this step is necesary)

5) in OSX, or linux, place GRUB2 (from post 762 of the"grub2 EFI boot loader internal/external booting" thread in your linux partition (the FAT partition)

6) make a grub.cfg file such as thisone and place it in the same directory:
  menuentry "shiva type boot" {
  root (hd0,1)
  fix_video
  linux /casper/vmlinuz ramdisk_size=1048576 boot=casper persistent root=/dev/ram rw  video=efifb acpi=force
  initrd /casper/initrd.gz
}

menuentry "Boot MacOSX from Internal Hard Disk" {
  root (hd1,2)
  chainloader (hd1,2)/usr/standalone/i386/boot.efi
}
menuentry "Boot from CD" {
  appleloader CD
}
menuentry "Boot from USB" {
  appleloader USB
}
menuentry "Reboot" {
  reboot
}

7)Restart holding alt/option key, select rEFIT, then GRUB and boot into linux

Good luck

---

### Post by Richardcavell on 2009-06-30
Hi,

It's a good thing that you've posted clear instructions. Just to note, step 4 (making the partition bootable) is unnecessary - it makes no difference to an EFI-based (Intel) Mac.

Richard

---

### Post by ronaldk on 2009-07-26
Hi vonlaken,  

Thanks for the instructions!  I'm trying to get this working on my macbook with Ubuntu 8.04.  I followed the steps you listed, but it's not working for me.  When I reboot with the option key held down, I can choose rEFIt, and the GRUB.  But when grub loads it doesn't seem to recognize the usb drive.  

It sends me to a command prompt, and if I type 'ls', I can see that there are two hard drives:  hd0 which is my macbook's internal hard drive, and hd1 which is the usb drive.  However, if I do 'ls (hd1,1)' or 'ls (hd1,2) it says 'unknown filesystem'.  The usb drive is partitioned with one HFS+ partition, and one FAT32 partition as you instructed, so I don't know why it is saying unknown filesystem.  Also, for the usb drive I'm using an ipod nano if that makes a difference.  I'm very new to all this, so I could just be missing something simple.

Thanks for any help!

---

### Post by theozzlives on 2009-07-26
You trying to boot Intrepid? Try this:

Format the flash back to original, Boot from your 8.10 CD, go to the terminal:
```
wget pendrivelinux.com/downloads/u810/u810.sh
chmod +x u810.sh && ./u810.sh
```

---

### Post by ronaldk on 2009-07-27
> **theozzlives said:**
> You trying to boot Intrepid? Try this:

Format the flash back to original, Boot from your 8.10 CD, go to the terminal:
```
wget pendrivelinux.com/downloads/u810/u810.sh
chmod +x u810.sh && ./u810.sh
```

Thanks for the link.  I tried it, but unfortunately it didn't work for me.  parted failed when trying to partition the ipod, giving the message 
"Error: Unable to open /dev/sdb - unrecognised disk label.
Warning: Device /dev/sdb has a logical sector size of 2048.  Not all parts of GNU Parted support this at the moment, and the working code is HIGHLY EXPERIMENTAL."
Also, just from reading the script I'm not sure it will work on a mac.  As far as I understand I think you need the grub2 efi bootloader in order to get a mac to boot from a usb drive?  Either way, based on the above message I think maybe it's not possible to do this using an ipod as the usb drive.  I'm going to try to get a hold of another drive and try it.  Thanks anyway.

---

### Post by pxwpxw on 2009-07-27
> **ronaldk said:**
> Hi vonlaken,  

Thanks for the instructions!  I'm trying to get this working on my macbook with Ubuntu 8.04.  I followed the steps you listed, but it's not working for me.  When I reboot with the option key held down, I can choose rEFIt, and the GRUB.  But when grub loads it doesn't seem to recognize the usb drive.  

It sends me to a command prompt, and if I type 'ls', I can see that there are two hard drives:  hd0 which is my macbook's internal hard drive, and hd1 which is the usb drive.  However, if I do 'ls (hd1,1)' or 'ls (hd1,2) it says 'unknown filesystem'.  The usb drive is partitioned with one HFS+ partition, and one FAT32 partition as you instructed, so I don't know why it is saying unknown filesystem.  Also, for the usb drive I'm using an ipod nano if that makes a difference.  I'm very new to all this, so I could just be missing something simple.

Thanks for any help!
> 
However, if I do 'ls (hd1,1)' or 'ls (hd1,2) it says 'unknown filesystem'

Possibly swap or unformatted?

For grub.efi use these commands to find stuff

```

grub> ls -l
grub> search -f /vmlinuz
grub> ls (hd0,2)/

```
with a usb stick plus HD, usb is hd0, HD is hd1.
EDIT: Apparently not for MB1,1 ?
Also see recent post #901 in grub efi thread for some other commands.

---

### Post by ronaldk on 2009-07-28
Alright, so the iPod was definitely the problem.  I tried this again with a kingston usb stick, and this time grub started properly, I got the menu, and it started to boot.  With Ubuntu 8.04 it would start to boot and then freeze quickly after getting to the line:
[initrd, addr=0x7cc00000, size=0x77c696]
I tried it again with Ubuntu 9.04, and it seems to get through most of the boot process alright, but then the screen flickers and then goes black.  Are there any other options in the grub.cfg file I could try?  I'm just using the one given above.  

Oh, and one other question:  is grub supposed to go on the hfs+ partition with rEFIt, or on the fat32 partition with ubutnu?  The first two posts are contradictory, though it seems to make no difference when I try either.  

Thanks again for the help.

---

### Post by pxwpxw on 2009-07-29
> **ronaldk said:**
> Alright, so the iPod was definitely the problem.  I tried this again with a kingston usb stick, and this time grub started properly, I got the menu, and it started to boot.  With Ubuntu 8.04 it would start to boot and then freeze quickly after getting to the line:
[initrd, addr=0x7cc00000, size=0x77c696]
I tried it again with Ubuntu 9.04, and it seems to get through most of the boot process alright, but then the screen flickers and then goes black.  Are there any other options in the grub.cfg file I could try?  I'm just using the one given above.  

Oh, and one other question:  is grub supposed to go on the hfs+ partition with rEFIt, or on the fat32 partition with ubutnu?  The first two posts are contradictory, though it seems to make no difference when I try either.  

Thanks again for the help.

Could you recap on your situation here.

Is it the live  CD ubuntu, amd64 or i386, can we stay with U904, or u810 because 804 is too old for grub.efi. 

What is your MacBook model and graphic chip.

Probably just need tweaking the boot menuentry (assuming you got the grub drive names sorted out). Please post your menuentry.

/efi/grub/grub.efi can go on fat32, ext3, or hfsplus, but hfsplus allows it to be blessed so that it can be booted without using rEFIT. Whatever suits you.

---

### Post by ronaldk on 2009-07-29
> **pxwpxw said:**
> Could you recap on your situation here.

Is it the live  CD ubuntu, amd64 or i386, can we stay with U904, or u810 because 804 is too old for grub.efi. 

What is your MacBook model and graphic chip.

Probably just need tweaking the boot menuentry (assuming you got the grub drive names sorted out). Please post your menuentry.

It is the Ubuntu 9.04 i386, currently on the ubuntu.com website.  My macbook is model 1,1; for the graphics chip, in system profiler it says "Chipset Model: GMA 950".   Here is the menuentry (for some reason the usb drive shows up as hd1, and the internal as hd0 instead of the other way around):

```
menuentry "shiva type boot" {
root (hd1,2)
fix_video
linux /casper/vmlinuz ramdisk_size=1048576 boot=casper persistent root=/dev/ram rw video=efifb acpi=force
initrd /casper/initrd.gz
}

```

Is there a list somewhere of what the possible options are? I'm confused about what they are supposed to do (not that I'd necessarily be less confused if I saw a list :) )

> /efi/grub/grub.efi can go on fat32, ext3, or hfsplus, but hfsplus allows it to be blessed so that it can be booted without using rEFIT. Whatever suits you.
Ah, good to know, thanks.

---

### Post by pxwpxw on 2009-07-29
MacBook1,1 might be a bit different, being the early model, perhaps accounts for usb = hd1 and not hd0, intel GMA950 is fine.

I have a u904 live usb  but it is x86_64 and I don't have mb1,1 to try it, however you can try this menuentry, (the linux commands are based on the text.cfg file in the /isolinux/ dircetory on the Live CD, plus options for grub.efi). I have added fix_video and fakebios for your MB1,1

```
 
menuentry "ubuntu904 Live USB" {
	fix_video
	fakebios
	search --set /casper/vmlinuz
	linux /casper/vmlinuz boot=casper persistent video=efifb acpi=force single
	initrd /casper/initrd.gz
}

```

The 'single' option should get you to a root console if you need to change anything for xorg.conf before the desktop, but you can also try without it.

[http://grub.enbug.org/TestingOnMacbook](http://grub.enbug.org/TestingOnMacbook)

---

### Post by ronaldk on 2009-07-29
Yessss! It worked using the menuentry you gave, and after editing xorg.conf to include this
```
Section "Device"
    Identifier    "fbdev driver"
    Driver        "fbdev"
EndSection
```as described in this thread a few times:
[http://ubuntuforums.org/showthread.php?t=995704](http://ubuntuforums.org/showthread.php?t=995704)

It booted into 9.04 with no problems: keyboard, trackpad, sound and wireless are all working.  Thanks so much for your help!

Edit:  Hey, it even mounted my internal OS X drive! :)

---

### Post by Macbook on 2009-09-14
Hello [pxwpxw]("http://ubuntuforums.org/member.php?u=85693") 				!

I also own a Macbook 1.1 and I try to boot Ubunto from USB. I want to do it the other way as described here: [http://ubuntuforums.org/showthread.php?p=7926848](http://ubuntuforums.org/showthread.php?p=7926848) 

I copied the efi folder and the ubuntu-9.04-desktop-i386.iso to the stick. I changed the names in grub.cfg to "ubuntu-9.04-desktop-i386.iso", renamed "bootx64.efi" to "bootia32.efi", installed the EFI bootloader and added your code to grub.cfg as well:

menuentry "ubuntu904 Live USB" {
	fix_video
	fakebios
	search --set /casper/vmlinuz
	linux /casper/vmlinuz boot=casper persistent video=efifb acpi=force single
	initrd /casper/initrd.gz
}
Now I have the EFI Bootmenü where I choose the stick and "ubuntu904 Live USB". The graphics card ist now recognized but the text says: "the kernel has to be loaded first". Mh.

I would appreciate any help that lets me finishing the last steps that need to be done so that I can start Ubuntu from USB on my Macbook 1.1

Thank you! 

PS: There is a "grub2" mentioned where do I find it? Do I need it?

---

### Post by pxwpxw on 2009-09-14
> **Macbook said:**
> Hello [pxwpxw]("http://ubuntuforums.org/member.php?u=85693") 				!

I also own a Macbook 1.1 and I try to boot Ubunto from USB. I want to do it the other way as described here: [http://ubuntuforums.org/showthread.php?p=7926848](http://ubuntuforums.org/showthread.php?p=7926848) 

I copied the efi folder and the ubuntu-9.04-desktop-i386.iso to the stick. I changed the names in grub.cfg to "ubuntu-9.04-desktop-i386.iso", renamed "bootx64.efi" to "bootia32.efi", installed the EFI bootloader and added your code to grub.cfg as well:

menuentry "ubuntu904 Live USB" {
	fix_video
	fakebios
	search --set /casper/vmlinuz
	linux /casper/vmlinuz boot=casper persistent video=efifb acpi=force single
	initrd /casper/initrd.gz
}
Now I have the EFI Bootmenü where I choose the stick and "ubuntu904 Live USB". The graphics card ist now recognized but the text says: "the kernel has to be loaded first". Mh.

I would appreciate any help that lets me finishing the last steps that need to be done so that I can start Ubuntu from USB on my Macbook 1.1

Thank you! 

PS: There is a "grub2" mentioned where do I find it? Do I need it?

The bootusb.tar.gz package in the other thread has grub.cfg menuentry's for booting from a loop-mounted ubuntu desktop-amd64.iso, so it uses loop mounting commands to find the kernel and tell initrd to load from the iso.

But your menuentry is for booting /casper files extracted and installed from an iso.

On the MB1,1 I assume you do need to use the -i386 version (I don't know).

So when booting from the ubuntu-9.04-desktop-i386.iso you should try this change to your menuentry.

```
 
menuentry "MB1,1 ubuntu-9.04-desktop-i386.iso " {
 fix_video
 fakebios
 search --set -f /ubuntu-9.04-desktop-i386.iso
 loopback loop /ubuntu-9.04-desktop-i386.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/ubuntu-9.04-desktop-i386.iso video=efifb acpi=force single
 initrd (loop)/casper/initrd.gz
}

```

From report above, that should get you to a root console, and you can edit xorg.conf as above.
I am not sure about the MB1,1 - but with intel graphics it may get to a desktop without needing to edit xorg.conf, try that also.

Please post on the other thread if you need more about the bootusb.tar.gz package from there and the loop mounted iso boot method, note that you will need to create a casper-rw file when using the loopback iso boot if you want persistent mode.

[http://ubuntuforums.org/showthread.php?p=7926848](http://ubuntuforums.org/showthread.php?p=7926848) 

( PS grub2 was about grub-pc booting, grub2-efi is what you have ).

---

### Post by Macbook on 2009-09-14
Hey! Thanks for answering!

At first I have to say, that I only have little knowledge in getting along with command line or shell interpreters. But I saw a new screen (another menu with a lightblue background) on my Mac after including your Code into grub.ifg:

```
menuentry "MB1,1 ubuntu-9.04-desktop-i386.iso " {
 fix_video
 fakebios
 search --set -f /ubuntu-9.04-desktop-i386.iso
 loopback loop /ubuntu-9.04-desktop-i386.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/ubuntu-9.04-desktop-i386.iso video=efifb acpi=force single
 initrd (loop)/casper/initrd.gz
}
```
I am happy so far. Unfortunately I don't know how to edit xorg.conf because this might be the last step before really booting my Mac into Ubuntu. What I found using Google is this: "use an editor like nano then just type as root: # nano /etc/X11/xorg.conf". 

I don't know where xorg.conf is located because "/ect/X11/" seems to be related to an Ubuntu installation on a harddrive - whereas I have the ubuntu-9.04-desktop-i386.iso as a "zipped" file on my USB-Stick. If it is possible editing xorg.conf that itself is contained in ubuntu-9.04-desktop-i386.iso it can be done while it is loaded in the RAM. (?) I don't think that the ubuntu-9.04-desktop-i386.iso is altered. Am I right? 

I really don't know how to use a root console to edit xorg.conf. And if I did once do I have to do it every time I want to boot from USB-based Ubuntu? 

Really challenging... I hope to get some advice. Thanks again!

---

### Post by pxwpxw on 2009-09-14
> **Macbook said:**
> Hey! Thanks for answering!

At first I have to say, that I only have little knowledge in getting along with command line or shell interpreters. But I saw a new screen (another menu with a lightblue background) on my Mac after including your Code into grub.ifg:

```
menuentry "MB1,1 ubuntu-9.04-desktop-i386.iso " {
 fix_video
 fakebios
 search --set -f /ubuntu-9.04-desktop-i386.iso
 loopback loop /ubuntu-9.04-desktop-i386.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/ubuntu-9.04-desktop-i386.iso video=efifb acpi=force single
 initrd (loop)/casper/initrd.gz
}
```
I am happy so far. Unfortunately I don't know how to edit xorg.conf because this might be the last step before really booting my Mac into Ubuntu. What I found using Google is this: "use an editor like nano then just type as root: # nano /etc/X11/xorg.conf". 

I don't know where xorg.conf is located because "/ect/X11/" seems to be related to an Ubuntu installation on a harddrive - whereas I have the ubuntu-9.04-desktop-i386.iso as a "zipped" file on my USB-Stick. If it is possible editing xorg.conf that itself is contained in ubuntu-9.04-desktop-i386.iso it can be done while it is loaded in the RAM. (?) I don't think that the ubuntu-9.04-desktop-i386.iso is altered. Am I right? 

I really don't know how to use a root console to edit xorg.conf. And if I did once do I have to do it every time I want to boot from USB-based Ubuntu? 

Really challenging... I hope to get some advice. Thanks again!

I think what you are seeing is the blue screen with the grey menu box -
        
--- Recovery Menu 
---- resume Resume normal boot
---- (and some more lines )

That is where the 'single' option gets to.

Just try the down/up arrow keys to see all the options, the box does not show them all. There is also
----root Drop to root shell prompt' 

But go back to the top option 'Resume normal boot', hit the enter key, and wait to see what happens.
You might be lucky and get to the desktop, which means you don't need to edit xorg.conf.

Or if it drops you back to a text login after a few tries, (maybe a minute or so) that means you will need to edit /etc/X11/xorg.conf. 

In that case just shut down and restart, this time at the Recovery menu, scroll down and select the line for ' root Drop to root shell prompt ' and Enter.
At the bottom of the screen you should see -

root@ubuntu:~#

Then if you type 

 nano /etc/X11/xorg.conf

It should bring up the existing xorg.conf if there is one, the startup writes these files using the iso.

If you need to find how to work 'nano', try it out on a testfile and check it by 

# ls -l 

or reading it back again with nano.

You might need a bit of practice and reading.

---

### Post by Macbook on 2009-09-15
Hey. 

I dont stop trying :-)

I edited xorg.conf as you said. 
I changed the device section to the following:

Section "Device"
    Identifier    "fbdev driver"
    Driver        "fbdev"
EndSection
Then I choosed "exit", said "yes" when i was asked if I want to save changes and hit enter.
I did a reboot and when I was at the second menu I choosed "resume normal boot". 

What happened was the same as ever: I saw a black screen with only one blue - horizontally centered - dot in the lower part of the screen.

That's it.

Maybe I should try the other method - installing Ubuntu on the Stick.

---

### Post by pxwpxw on 2009-09-15
> **Macbook said:**
> Hey. 

I dont stop trying :-)

I edited xorg.conf as you said. 
I changed the device section to the following:

Section "Device"
    Identifier    "fbdev driver"
    Driver        "fbdev"
EndSection
Then I choosed "exit", said "yes" when i was asked if I want to save changes and hit enter.
I did a reboot and when I was at the second menu I choosed "resume normal boot". 

What happened was the same as ever: I saw a black screen with only one blue - horizontally centered - dot in the lower part of the screen.

That's it.

Maybe I should try the other method - installing Ubuntu on the Stick.

You don't seem to have read the other thread.

When you just install the iso, you must create casper-rw for persistence to work, and add "persistent" to the linux commandline. All explained in the other thread.

[B]How to create a Live-USB-Stick, that is able to boot a Mac
[/B][COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1261747
posts 7,15,22,24[/COLOR]

About casper-rw
[http://ubuntuforums.org/showpost.php?p=7935961&postcount=24](http://ubuntuforums.org/showpost.php?p=7935961&postcount=24)

If you use the other method in this current thread (Using a Live-USB Distro....) and install with Usb Startup Disk Creator, it creates casper-rw for you, and you use the simpler menu without the iso stuff.

You can also just copy the casper/ folder and the .disk/ folder from the iso to the usb stick.
and create casper-rw.

They are just 3 different methods.

In any case, to keep the changes, you need to create casper-rw and restart with "persistent" in the linux command line.

---

