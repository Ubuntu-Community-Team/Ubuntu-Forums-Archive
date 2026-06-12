---
title: "Booting off a thumb drive"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by keval on 2008-03-17
Greetings.
This post is a little different from the usual ones related to booting off a thumb drive, so please bear with me.
Couple of months ago, I dropped my laptop and, in the process jammed the cd drive beyond all hope of repair.  On top of this, my OS has begun acting up, so I'd like to wipe it all clean and install the latest Ubuntu.  Am I correct in assuming that I can simply download the OS into the thumb drive, tell my machine to boot from there, and it'll install?
Thanks,
Kevin

---

### Post by penguinpi.com on 2008-03-17
Yeah, but you will probably have to format the drive as ext3. try gparted

---

### Post by diafygi on 2008-03-17
Sometimes, it depends on how your [BIOS]("http://videos.howstuffworks.com/harvard-extension-schools-computer-science-e-1-understand/2664-changing-pc-bios-settings-video.htm") boot order is set up.

Also, if you can't get the USB drive to work by just copying the LiveCD image to it, you might try the [Pen Drive Linux]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/") tutorial (this one is for Gutsy, but they have similar ones for different distros). USB drives sometimes have cranky [MBR]("http://en.wikipedia.org/wiki/Master_boot_record")s.

---

### Post by wolfen69 on 2008-03-17
installing from usb stick [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by keval on 2008-03-18
After spending about six hours downloading the 7.10 ISO (I'm in a hotel room with about 23 Kbs access), I've succeeded in loading the thumb drive and setting the boot sequence to HDD->lan->CD, then setting the HDD priorities to USB->HDD.  However, when I boot up, I get the following error message:
"Invalid system disk
Replace the disk, then press any key"
Any thoughts?
Thanks,
Kevin

---

### Post by njparton on 2008-03-18
You've probably just stuck the ios file on the usb drive rather than extracting it there and making it bootable?

Booting from USB sticks isn't always straightforward.

---

### Post by keval on 2008-03-18
Dumb, dumb, dumb.
You're right.  How do I extract it on a thumb drive?
Kevin

---

### Post by keval on 2008-03-18
Disregard previous post.  I know how to extract files on a thumb drive and am doing so as we speak.
Kevin

---

### Post by keval on 2008-03-18
I've extracted the files and tried to boot off the stick, but I get the same error message.  Any idea what I might try next?
Thanks,
Kevin

---

### Post by njparton on 2008-03-18
As I said it's not like buring an iso to a CD - making a usb stick bootable is not straightforward.

Google for it and there's lots of info out there - this isn't an ubuntu specific problem and I've never done it myself :)

Good luck.

---

### Post by azimout on 2008-03-18
did you follow the instructions suggested above: [https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick") ???
please don't make us re-explain here the process described in the above guide... but tell us if you had any trouble following the steps described in it...

---

