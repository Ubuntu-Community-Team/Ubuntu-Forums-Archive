---
title: "iPod Touch not mounting"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by mhiggins on 2007-10-20
I am unable to mount my iPod Touch on 7.10.

dmesg fragment:

[ 3832.941609] usb 1-5.4: new high speed USB device using ehci_hcd and address 57
[ 3833.052071] usb 1-5.4: configuration #1 chosen from 3 choices

But no mount of the device occurs.

Pop-up box says "A Camera has been Detected".

Have read threads about newer iPods not syncing, but unclear if they even mount ?

---

### Post by kidders on 2007-10-21
Hi there,

They don't, I'm afraid ... at least not without significant modification. They don't even mount on a Mac. The iPod Touch seems to be quite a different beast than its brothers. The "camera" your box is detecting is the Touch's PTP interface, which presumably only exists because of the iPhone.

---

### Post by mhiggins on 2007-10-22
Many thnks for taking the time on this. I do love my iTouch, but I do so also hate Windows - was hoping.....

---

### Post by kidders on 2007-10-22
No worries. :-)

Well, without wanting to go into too much detail about legally dubious or warranty-voiding tweaks, you *can* get access to your iPod's filesystem if you really want it, with a variety of protocols & techniques, via the USB interface, or its WLAN adapter. Personally, I've found SFTP the most useful option, since Linux's UIs handle it quite well.

Depending on how much trouble you're willing to go to, some googling will point you in the right direction. The iPod Touch is specifically designed *not* to be "mounted" in the way an iPod Nano is, for example, so if you're not happy to hack your pretty, new gizmo, it would be better to just bow to Apple's will, for the moment.

Sorry for being cryptic, but this forum isn't really the place for iPod hacks, I'd say.

---

### Post by hherb on 2007-11-02
Sadly, the iPod touch does not seem to behave like a standard USB mass storage device.
However, you can "jailbreak" it quite easily (but first make sure you have updated it's firmware to 1.1.1) and then log in via wireless and ssh. Default root ssh password is "alpine" I think - change it right away after jailbreaking your ipod.

In order to jailbreak it, visit the web page [http://www.slovix.com/touchfree/](http://www.slovix.com/touchfree/) for instructions.
Basically, all you have to do is connect your ipod to a wifi internet access, use Safari to access the url [http://dn.vc/jb/](http://dn.vc/jb/) and patiently wait a few minutes.

After that, you can install lots of applications, enable calendar input, and enable ssh access - and use the fish protocol (eg in Konqueror, enter the url fish://root@your.ipod.ip.address) to move files to and from your ipod touch or iphone. Good luck! Works for me.

---

### Post by zmjjmz on 2007-12-05
The slovix link seems to be dead...

---

### Post by hherb on 2007-12-05
Indeed. But things have much improved since!
Just follow the excellent instructions at [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

Good luck!

---

