---
title: "Ubuntu hangs after install on Asus motherboard"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by arava on 2006-09-29
Hi everyone:

I am trying to install the Ubuntu 6.06 LAMP server and cannot get past Ubuntu hanging after the first reboot.

I'm using an old Asus P2B motherboard. I've tried another machine (similar motherboard) with the same results. Various versions of Red Hat, Fedora and Windows work quite happily on these machines. So it is not the hardware and has to be something that I have not configured correctly in Ubuntu.

I've tried installing the same Ubuntu server disk on a P4 (Intel motherboard) and it does not have this problem.
```
Sep 25 04:13:59 ubuntu kernel: [ 46.513268] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
Sep 25 04:13:59 ubuntu kernel: [ 46.513300] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
Sep 25 04:13:59 ubuntu kernel: [ 46.513320] ide: failed opcode was: unknown
Sep 25 04:13:59 ubuntu kernel: [ 46.513337] end_request: I/O error, dev hdc, sector 1430336
Sep 25 04:13:59 ubuntu kernel: [ 46.513358] Buffer I/O error on device hdc, logical block 178792
```
I'm guessing from the error messages that there is a problem with the IDE driver not working with something on this family of ASUS motherboards.

As I was trying to install a web server, I posted this question with detailed information and a screen photograph on the 'Server talk' forum.
[http://www.ubuntuforums.org/showthread.php?t=264705](http://www.ubuntuforums.org/showthread.php?t=264705)

This question may have been too simple for the experts there to respond. I am retrying here because I am a beginner to Ubuntu. Hopefully someone here can be kind enough to point me in the right direction as to where I should look to find the solution for this problem. It doesn't seem right to me that Ubuntu cannot work on an Asus motherboard.

I was hoping to use Ubuntu as a LAMP server because I was impressed with the how good the desktop version looked and ran off the Live CD.

Any help is appreciated.

---

### Post by nealon on 2006-09-30
I have the exact same error message.
I have a ASUS MB as well.

---

### Post by arava on 2006-10-01
> **nealon said:**
> I have the exact same error message.

I'm glad that I'm not the only one with this problem.
My second machine with the same problem has a P2L97 motherboard. Both the P2B and P2L97 have PIIX4 chips.

Can someone please explain what the following errors mean.
```
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05
hda: dma_intr: status=0x51 {DriveReady SeekComplete Error}
hda: dma_intr: status=0x84 {DriveStatusError BadCRC}
```

I think that hda is my IDE hard disk and hdc is the CD drive.
Where can I find some information on these error codes and how do I fix them?

---

### Post by nealon on 2006-10-03
I would suggest trying novel Suse 10.1

This worked great for me and seems to be second most poplular distro on [www.distrowatch.com](www.distrowatch.com)

I gave up. I posted that error message in a few forums.. no one replys... 

No wonder why people are turned off my linux.....  :-)

---

### Post by nealon on 2006-10-03
As a side note, I downlaod the 6.10 beta... and It gets past that error message but just hangs on a orange screen..

Guess Im O for 2....

---

### Post by arava on 2006-10-07
> **nealon said:**
> 
I gave up. I posted that error message in a few forums.. no one replys... 

It is sad that the Ubuntu community does not seem to care about our planet. I really do not like seeing perfectly good machines go to waste and pollute our environment. Besides the latest/greatest machines use more power every minute of every day. When you consider that a server is on 24x7, it add up to the slow destruction of our world.

> I would suggest trying novel Suse 10.1
This worked great for me and seems to be second most poplular distro on [www.distrowatch.com](www.distrowatch.com)


I'll try one last time in the Installation and Upgrade Help forum.
[http://ubuntuforums.org/showthread.php?t=273015](http://ubuntuforums.org/showthread.php?t=273015)

Then I'll have no choice but to say goodbye to Ubuntu and try another distribution. I have a spare P4, but it consumes a lot more power than the rescued P2's...

---

