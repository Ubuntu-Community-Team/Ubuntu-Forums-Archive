---
title: "I have an real hardware modem not Winmodem but Ubuntu doesn't see it"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by ieee488 on 2006-09-01
By luck, I have an internal PCI modem that is a real hardware modem and not a Winmodem. But Ubuntu 5.10 doesn't see it.
I tried autodetecting /dev/modem, and /dev/ttyS0 through /dev/ttyS3.

How do I go about getting it to work in Ubuntu?

---

### Post by szf on 2006-09-01
Have you tried the setserial to determine the ttys* interface for the modem?

---

### Post by szf on 2006-09-01
Thumbing thru old notes here (forgive any absences):

Test modem via: setserial -bg /dev/ttyS*

Symlink that modem via: ln-s /dev/ttySn /dev/modem [where n is the interface]

... maybe run the minicom utility to prove it out before configuring pppd.

---

### Post by JNowka on 2006-09-02
1) Did you install the drivers for it?

2) What type of modem is it?  Brand and Model#

---

### Post by deanlinkous on 2006-09-02
> **ieee488 said:**
> By luck, I have an internal PCI modem that is a real hardware modem and not a Winmodem. But Ubuntu 5.10 doesn't see it.
I tried autodetecting /dev/modem, and /dev/ttyS0 through /dev/ttyS3.

How do I go about getting it to work in Ubuntu?

Might try the command line tool pppconfig and see if it detects it and sets it up, if it comes up to enter it manually then you can systematically go thru the possibilities and see if one gets it working. 

Also gather some info using the **lspci -vv** command and maybe **dmesg**

---

### Post by ieee488 on 2006-09-02
Thanks for all the responses.

It turns out the modem is at ttyS**14**!

I ran   *sudo wvdialconf wvtest*  in a Terminal window and that was what was found.

I followed the instructions at  [www.ticon.net/~tatimmer/tomsmodemtips.html](www.ticon.net/~tatimmer/tomsmodemtips.html)  that was posted in a different thread to dial into my ISP, and it worked. Big thanks to Tom for those instructions.

I think that is all I did.

---

