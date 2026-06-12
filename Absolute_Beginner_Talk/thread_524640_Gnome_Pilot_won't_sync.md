---
title: "Gnome Pilot won't sync"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-08-13
I'm trying to use Gnome Pilot to sync up to my Palm M505 but for some reason
it won't get passed the Setup Pilot Sync stage.  It throws up an error
that I don't understand.  If anyone has any experience with this, I
would greatly appreciate some help in solving this.

[IMG]http://img124.imageshack.us/img124/9274/screenshotkb0.jpg[/IMG]

---

### Post by yorkie on 2007-08-13
found a howto its 2004 still might help
[http://www.redbug.uklinux.net/palm/pc-connect.html#pc-connect-usb](http://www.redbug.uklinux.net/palm/pc-connect.html#pc-connect-usb)

---

### Post by Orbital75 on 2007-08-13
I tried
 **sudo modprobe visor** and **sudo modprobe usbserial **
 both didn't give me any output back
it just went back to name@computer:~$

I have never used my Palm with Linux before so I may be
choosing the wrong option here. I was afraid it meant ever and
would erase my Palm.

[IMG]http://img260.imageshack.us/img260/226/00screenshotsg4.jpg[/IMG]

What selection should I choose?

[IMG]http://img252.imageshack.us/img252/6670/00screenshotnm6.jpg[/IMG]

Humm........ :confused:

---

### Post by lemmy999 on 2007-08-13
Try changing device to "usb:" It worked for me!

---

### Post by Orbital75 on 2007-08-13
Tried that as well..... For some reason the m505 just won't
sync.  I'm thinking it may be because I'm in a Virtual Machine.
I'm using Ubuntu in Virtual Box.  I've got my HP LaserJet 1020,
Memorex 1 gig USB thumbDrive, and iPod to all work under USB.
Not sure why Gnome Pilot won't sync with it. I know that Virtual
Box sees it, because it's in the Active USB list.

I've tried all the options

 /dev/pilot
 USB
 /dev/tty/usb0
 /dev/tty/usb1

---

### Post by yorkie on 2007-08-14
still no luck maybe this is someuse
[https://help.ubuntu.com/community/PalmDeviceSetup](https://help.ubuntu.com/community/PalmDeviceSetup)

---

### Post by Orbital75 on 2007-08-14
Thank you for the link..... I'll try that later when I get home and see how that does.
I'll post my finding either way.  

Thanks again.

---

### Post by Orbital75 on 2007-08-14
I wouldn't recimmend anyone to try this.
It ruined my whole Ubuntu installation and now it
states it can't find USB port and won't boot.  

I'm running in a VM but some how the Virtual Box program
got corrupted. Virtual Box locked up and I had to stop the
program with Control Alt Delete. Now when I run virtual
box, it locks up and causes windows XP to crash.

Yeah, I wouldn't try this method.

---

