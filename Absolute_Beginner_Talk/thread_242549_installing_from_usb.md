---
title: "installing from usb"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by ultraelite on 2006-08-23
okay I have a question regarding installing using usb.  I followed the directions from [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) and it doesn't boot.  I am running from an thinkpad x60 so I can't use a cd.  When I try to boot I get to a point and it says linux not found boot: or something to that extent.  Can anyone help me?  I have all of the files that are on the cd on the thumb drive and ldlinux.sys I renamed isolinux.cfg to syslinux.cfg I am pretty sure my laptop supports usb booting and so does my thumb drive it is formatted fat16 and is about a gig.  thanks

---

### Post by robins_web on 2006-08-23
Does your BIOS allow you to boot from the USB device? If so, have you made a change to the boot order in your BIOS setup? You should be able to go into your BIOS setup and (1) see if it will allow you to boot from the device, and (2) change the boot order.

To enter your BIOS setup...well, that varies from machine to machine. On some  of them, you have to press <ESC> before it boots, on others CTRL-S, F1, etc. Your best bet would be to look in your owners manual (yeah...I know: we *all* hate 'em! But "sometimes a man's gotta do what man's gotta do").

As an example, my Toshiba defaults to this boot order:

HDD, FDD, CD, LAN (hard disk drive, floppy disk drive, CD, Local Area Network). To boot from the CD I had to change my BIOS settings to this:

CD, HDD, FD

Unfortunately, my bios is old enough that it doesn't give me an option to boot from USB.

---

### Post by ultraelite on 2006-08-23
yes my bios does support usb booting and I am able to boot usig usb (I get to the syslinux stuff) I have usb set to primary and it shows my thumb drive in the menu of devices, thanks any other suggestions?  

BTW I am not a total n00b I am A+ certified and have some expirience with slackware not that I think it wil make much of a difference here just thought I would let you know so that you can drop some heavier stuff on me if you like.

---

### Post by ultraelite on 2006-08-24
I'm glad I posted in the absolute beginer forum I misread the directions 

> Copy (or move) all the files from the following directories to your USB flash drive's root directory:

    *

      isolinux
    *

      install

I read that as copy or move all files and directories to your usb flash drive's root directory:

How ever it still does not boot I get a little further there is now an ubuntu logo on boot but I get a message that says 


> could not find kernelimage: /casper/.vml


any suggestios?

---

### Post by ultraelite on 2006-08-24
I copied the entire casper directory to the root of my thumb drive and removed any /casper/ refrences from syslinux.cfg and it gets a little further.  It starts to boot and gets to mounting root filesystem and then goes back to the screen I was at before which says decompressing linux kernel... booting linux kernel... (or something like that).  It doesn't respond to anythin I type except ctrl+alt+del which goes into restart sequence and restarts my computer.

Any suggestions?

---

### Post by ultraelite on 2006-08-25
okay so I didn't see anything against this in the rules and hope you guys don't flame me sorry if it is against the rules but I am desperate

BUMP

---

### Post by newYim on 2006-11-28
i got same problem as you guy got
after error msg like cannot find casper/.vml
boot :
just type live after boot:
then it run fine
good luck!

---

### Post by rdelfin on 2007-04-20
I'm experiencing the very same problem:

boot: could not find kernel image: /casper/.vml

I also typed "live" as suggested but nothing, it still doesn't do the work.

Any advise guys?

Thanks,
Rafa.

---

### Post by Kurdy on 2007-07-01
Use this site to setup Ubuntu 6.10 on a USB stick

[http://www.pendrivelinux.com/2007/02/12/usb-ubuntu-tutorial-for-linux-users/](http://www.pendrivelinux.com/2007/02/12/usb-ubuntu-tutorial-for-linux-users/)

after that copy on the same way 7.04 over the 6.10 stick.
By me it works.

Succes.

Kurdy

---

