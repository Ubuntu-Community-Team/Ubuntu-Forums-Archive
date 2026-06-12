---
title: "booting from usb"
date: 2013-05-29
forum: Apple Hardware Users
---

### Post by sacarde on 2013-05-29
hi,   
   I try to install ubuntu13-ppc in my mini-G4 from usb
in openfirmware I view (dev / ls) :

/pci@f2000000/usb@1b/hub@1/disk@4

how can I boot it?

p.s.I make usb-pendrive with unetbootin


thank you

---

### Post by GhettoMrBob on 2013-05-31
PPC's cannot boot to USB. They **can** boot to either a CD/DVD or a FireWire external (if you have one).

The FireWire option will definitely provide faster boot/install if you have one available. Otherwise, the CD/DVD method should work.

---

### Post by rkmugen on 2013-05-31
That's not entirely true... i know for a fact that at least the iMac G3 (slot-loading) can boot from USB.  I installed Debian, MintPPC, and even Ubuntu 12.04 using this method.... no CD/DVD involved.

It's simply a matter of burning the ISO image to the USB flash drive using 'dd', booting into the Open Firmware prompt (white screen), and using the appropriate command(s) to tell Open Firmware to boot from the USB device.

Simply inserting the USB device at boot and not doing anything else won't work.  Neither will holding the Option key on the keyboard nor selecting the USB device from OSX or even OS9's Startup Disk control panel.

---

### Post by sacarde on 2013-05-31
I view alias:

usb0   /pci@f2000000/usb@1b,1

usb1   /pci@f2000000/usb@1b


and I try:

> boot usb1/disk@1,\install\yaboot

but dont works




p.s.
I have to make usb with unetbootin or dd ?

---

### Post by rkmugen on 2013-05-31
Don't use UNetbootin.  In fact, if you visit their webpage, it says that USB sticks made with UNetbootin won't be bootable with PPC computers.  Despite what Unetbootin says, and despite the fact that it runs on OSX/PPC, it's designed to burn Intel/AMD ISO's for use on Intel/AMD machines.

So, just use 'dd'.  But be real certain that you downloaded the appropriate ISO for PPC G4, and that you know how to use 'dd' from the terminal.

If you're using Windows to burn the ISO to USB, I created a tutorial here.  Though it refers to MintPPC and uses the Debian ISO, you can also use your choice of Ubuntu ISO's.  [http://www.mintppc.org/forums/viewtopic.php?f=20&t=1163](http://www.mintppc.org/forums/viewtopic.php?f=20&t=1163)

If you're using Mac OS X to burn the ISO to USB, you might want to refer to this guide:  [https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F)

If you're using Linux on a different computer (regardless of whether it's a Linux/Intel, Linux/AMD, or Linux/PPC), you can still use 'dd' to burn your choice of ISO to the USB device.

After you've successfully burned your ISO to the USB device, be sure you are telling OpenFirmware to boot from the appropriate device tree...


Why don't you try either one of these in the OpenFirmware prompt (white screen):
```
boot usb0/disk@1:2,\\yaboot
``` or ```
boot usb1/disk@1:2,\\yaboot 
```

---

### Post by GhettoMrBob on 2013-05-31
Sorry for being a bit misleading...I know that PPC can technically boot to USB but the process is much more difficult for those less savvy in that area. That being said, that's why I recommended the CD method as it's easily the most straight forward and foolproof. 

As for writing the image to the USB, I agree with rkmugen in using the 'dd' command and making sure you have the right PPC compatible image.

---

### Post by sacarde on 2013-05-31
> **rkmugen said:**
> 

Why don't you try either one of these in the OpenFirmware prompt (white screen):
```
boot usb0/disk@1:2,\\yaboot
``` or ```
boot usb1/disk@1:2,\\yaboot 
```


I try but boot is stopped



p.s.
iso contains: /install/yaboot

---

### Post by rkmugen on 2013-05-31
If you insist on booting from USB, I recommend you take things step-by-step and do not skip anything.

First, which ISO are you using?[INDENT]Are you using the mini 29MB iso?
[http://ports.ubuntu.com/ubuntu-ports/dists/raring/main/installer-powerpc/current/images/powerpc/netboot/mini.iso](http://ports.ubuntu.com/ubuntu-ports/dists/raring/main/installer-powerpc/current/images/powerpc/netboot/mini.iso)

Or are you using the full 806MB iso?
[http://cdimage.ubuntu.com/releases/13.04/release/ubuntu-13.04-desktop-powerpc.iso](http://cdimage.ubuntu.com/releases/13.04/release/ubuntu-13.04-desktop-powerpc.iso)

I recommend that you use the 29MB mini iso so that you don't have to wait for the entire 806MB to load on a slow USB 2.0 port... if you have an even OLDER iMac G4, you'd have an even slower USB 1.1 port!  So that's my rationale for sticking with the smaller ISO.

Also, please keep in mind that if you use the mini ISO, you will NOT get to try/demo the Live desktop.  Instead, the mini ISO will take you straight into the installation screens.  If you insist on trying the Live desktop (with the GUI), then I recommend that you simply burn the 806MB ISO to a blank DVD.  You can burn the DVD in a Windows or Linux machine and it should still be bootable on your G4..... but again, please be sure that you use the PPC-compatible ISO.
[/INDENT]

Second, which system are you using to burn the ISO?  Are you using Windows, Mac OS X, or Linux?[INDENT]PLEASE TELL US, so we can be absolutely certain which method to recommend to you.
[/INDENT]

Third, can you please tell us exactly HOW you burned the ISO to your USB disk (most recently).[INDENT]The USB disk/flash drive won't work if you typed the wrong commands into 'dd', or if you failed to properly mount/dismount the usb drive (in OSX or Linux).  _[COLOR=#ff0000]**If you have a Windows machine, you DO NOT have to worry about mounting or unmounting the flash drive before burning the ISO to it.**[/COLOR]_
[/INDENT]

Fourth, please describe to use your USB device tree EXACTLY as displayed in OpenFirmware.[INDENT]I realize that this can be difficult, since all the entries race by real fast... but pay particular attention to USB, as those are the ones we care about.

[/INDENT]
[INDENT]For simplicity's sake, I recommend that you DISCONNECT any other USB devices from your computer.  The only things you really need to have connected to your iMac G4 (for now) is just your Keyboard, your Mouse, and your USB flash drive.  This will make it very easy to visually keep track of what device you're looking at in the OpenFirmware screens.
[/INDENT]

Fifth, please follow these instructions:[INDENT]> Boot in open firmware by holding option+command+o+f. Then find out which is the device:
```
dev / ls
```
You should  see somewhere usb with an extra entry disk.  Write that number down.  In my case, it's usb19. Then look at the devalias:
 
    ```
devalias
```
In my case, ther are two entries usb0 and usb1.  The one that is associated with usb19 is the boot device.  In my case, it is usb1.

So, I type this in the OpenFirmware prompt to boot from the flash drive on usb1:
         ```
boot usb1/disk@1:2,\\yaboot
```

If devalias told me something other than usb1, then I'd have to use some other USB alias....
```
boot usb0/disk@1:2,\\yaboot
```
[/INDENT]
 
I assure you that I just downloaded the 29MB mini.iso for Ubuntu 13.04 32-bit for PPC.  I was able to burn it onto my USB flash drive using a port of 'dd' for Windows.  I was also able to boot off of it using the above instructions.  So if I can do it on my iMac G3, the process should at least be somewhat similar on your G4.

---

### Post by GhettoMrBob on 2013-05-31
rkmugen,

Out of curiosity, how's 13.04 run on that G3?

---

### Post by rkmugen on 2013-05-31
EXTREMELY slow.  Even after downgrading MESA (to get graphics hardware acceleration to work), and using an appropriately tweaked xorg.conf file, the performance is still nowhere near as fast as an LXDE or XFCE-based distro.  So, I went back to MintPPC 11 (which is basically Debian 7.0 with LXDE, and some custom compiled packages from Linux Mint).  I even tried Lubuntu and Xubuntu 13.04.... but they were still nowhere near as fast as MintPPC11.  I believe it has something to do with the newer 3.8.x kernel...  In contrast, we're still using the 3.2.x kernel in MintPPC11 (or Debian 7.0).

---

### Post by GhettoMrBob on 2013-05-31
I see. I had some of the same issues albeit with 12.04 on an old IBM ThinkPad. It's only got a single core Pentium M. It wouldn't run 13.04 because there isn't a non-pae version so I upgraded my 10.04 to 12.04 and kept the classic shell. Doesn't run great but it gets the job done for simple web browsing or text editing.

---

### Post by sacarde on 2013-06-01
@rkmugen

-1- I try mini and desktop lubuntu from: [http://cdimage.ubuntu.com/lubuntu/releases/13.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/13.04/release/)

-2- I am running archlinux64

-3- I make usb with: sudo dd if=/home/sacarde/lubuntu-13.04-desktop-powerpc.iso of=/dev/sdc

-4- I view device:
[COLOR=#000000]...
/pci@f2000000/usb@1b,1[/COLOR]
[COLOR=#000000]/pci@f2000000/usb@1b/disk@1[/COLOR]
...

-5- when I try: [COLOR=#000000][FONT=Ubuntu Mono]boot usb1/disk@1:2,\\yaboot or on usb0/......
system stop there, and I have to reboot





thanks

p.s.
I clean cd/dvd lens, and now I can boot fron cd/dvd too

[/FONT][/COLOR]

---

### Post by GhettoMrBob on 2013-06-01
If you cleaned off that lens why not just install via CD? It'll clear up the not booting issue and you can keep the CD for future use if you ever need it. I always find myself formatting the USB and then needing it again in the future...just food for though.

---

### Post by sacarde on 2013-06-01
I try to install from cd

but when live start I dont view well

can I use vesa or rescue-mode in lubuntu?


thanks

---

### Post by rkmugen on 2013-06-01
So, you mean to say that you have a video problem?  Well... as far as the G4 Mac Mini goes, I guess it's a common issue, particularly whenever the ATI Radeon chipset is involved.  Have you looked at [https://wiki.ubuntu.com/PowerPCFAQ#Radeon_cards](https://wiki.ubuntu.com/PowerPCFAQ#Radeon_cards)?

Actually... in my opinion, don't even bother with the Live session or the Desktop ISO image.  Instead, I recommend that you just use the Alternate installation ISO and just perform the installation straight-away.
[http://cdimage.ubuntu.com/lubuntu/releases/13.04/release/lubuntu-13.04-alternate-powerpc.iso](http://cdimage.ubuntu.com/lubuntu/releases/13.04/release/lubuntu-13.04-alternate-powerpc.iso)

Then, have a look at this forum posting about a guy who installed Lubuntu 13.04 on his Mac Mini G4...
[http://ubuntuforums.org/showthread.php?t=2142419](http://ubuntuforums.org/showthread.php?t=2142419)

---

### Post by sacarde on 2013-06-02
oooh great !!

solved with param:   [B] live video=radeonfb:1440x900-16@60


thank you very very much 

[/B]

---

### Post by rkmugen on 2013-06-02
You're welcome!  Have fun w/ Lubuntu!

---

