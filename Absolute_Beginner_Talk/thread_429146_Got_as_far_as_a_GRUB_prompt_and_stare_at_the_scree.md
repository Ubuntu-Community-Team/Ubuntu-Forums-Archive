---
title: "Got as far as a GRUB prompt and stare at the screen"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by Relztrah on 2007-04-30
I downloaded and installed (or attempted to install) Ubuntu 7.04 and after some error messages and several reboots I now only get a GRUB prompt. I hit TAB and get a list of commands, none of which seems to do anything.  Obviously I don't know the GRUB command syntax. Is there a tutorial for using GRUB? 

I was hoping to boot to a GUI but I guess it wasn't meant to be. Is that what GNOME is? 

It took me several years to learn DOS and several more to learn Windows, so I realize that I'm not going to master Ubuntu in a week. Doggone it. If I didn't have to work, eat or sleep I could really make some progress.

---

### Post by rmt on 2007-04-30
did you try it to run just the Ubuntu-live CD to see if your hardware was detected fine?

---

### Post by jimrz on 2007-04-30
> **Relztrah said:**
> I downloaded and installed (or attempted to install) Ubuntu 7.04 and after some error messages and several reboots I now only get a GRUB prompt. I hit TAB and get a list of commands, none of which seems to do anything.  Obviously I don't know the GRUB command syntax. Is there a tutorial for using GRUB? 

I was hoping to boot to a GUI but I guess it wasn't meant to be. Is that what GNOME is? 

It took me several years to learn DOS and several more to learn Windows, so I realize that I'm not going to master Ubuntu in a week. Doggone it. If I didn't have to work, eat or sleep I could really make some progress.

Gnome is the gui. seems something went awry here, please post the error msg's you are getting so we will have an idea of what needs to be corrected. you might also post the type equipment you are using - make/model/cpu/amount of ram/vid card/whatever and if you have any usb devices connected to the box.

---

### Post by Relztrah on 2007-05-01
Here is the error message I *was* getting:

**Failed to start the X server (your graphical interface). It is likely...**

When given the option to Diagnose I select Yes

I will only list the apparent errors which I believe are designated with (EE):

[B](EE) Unable to locate/open config file
(EE) open /dev/fb0: No such file or directory
(EE) I810(0) Given bpp (32) is not supported by i810 driver
(EE) Screen(s) found, but none have a usable configuration

Fatal server error: no screens found[/B]

But for whatever reason I no longer reach that point in the boot process. When I boot with the Ubuntu CD in the drive I get a normal BIOS screen, hit F1 to cointinue when prompted, and get:

[B]GRUB version 0.93  (~~~~~)

[ minimal BASH-like line editing is supported...]

grub >[/B]

And that's when the screen-staring begins. I am running an old Dell Optiplex with an Intel Celeron processor, 256MB of RAM. The video is on the mobo; there is no separate video card. I can stick a video card in there--an old one with only 4 or 8 MB of video RAM--if that will make a difference.

For what it's worth, I'm not trying to do a dual-boot or anything like that. I was hoping to load Linux exclusively on this box.

Any coaching will be greatly appreciated.

Relztrah

---

### Post by johnc4510 on 2007-05-01
Ctrl+Alt+F1  at the start of boot will get you to command line.
Type in:   sudo dpkg-reconfigure xserver.xorg at flashing cursor
It will take into a graphical interface, read and answer question 
This will reconfigure your x server
Then at end reboot

---

### Post by Relztrah on 2007-05-01
Unfortunately I have about a nanosecond from the time I hit F1 to continue to when my GRUB prompt appears. But apparently I have other issues as well. Just to see what would happen I put in my Knoppix Live CD and booted. I get the same exact result. 

[B]GRUB version 0.93 (~~~~~)

[ minimal BASH-like line editing is supported...]

grub >[/B]

I can still get an A> prompt if I boot with a Windows boot floppy so I could run fdisk if that will help. (Is there a way to make a Linux boot floppy?)  I suspect that I'm running out of options here.

Thanks for any help you can provide.

---

### Post by confused57 on 2007-05-01
You might be able to investigate your computer using the CLI:
[http://users.bigpond.net.au/hermanzone/p15.htm#cli](http://users.bigpond.net.au/hermanzone/p15.htm#cli)

worth a try...

---

### Post by Coucouf on 2007-05-02
Are you sure you are really booting from the CD-ROM ?
Don't you get the exact same error if you put no CD in the drive when booting ? This may indicate that you are still booting from the GRUB that was setup on your hard disk on your the first install try.

Maybe you can check your BIOS for the boot order option.

Also the grub menu on the live isn't just black&white text in my experience. There should be an Ubuntu logo and the boot options text is 'Ubuntu-brown'. :)

---

