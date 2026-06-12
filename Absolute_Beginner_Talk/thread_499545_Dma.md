---
title: "Dma?"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by SPRL on 2007-07-12
How can I tell if DMA is on for my DVD RW.? :confused:
-Running 7.04.
-External Drives

Im a noob so if it has to do with the terminal, please be as detailed as possible.

 Thanks :-D

---

### Post by yabbadabbadont on 2007-07-12
Open a terminal window.  Run ```
dmesg | grep -i dvd
```  Please post the output.  Just as an example, here is the output for my internal drive (yours will be different) ```
/home/daffy $ dmesg | grep -i dvd
[   27.938978] hdb: CD-RW 48X16, ATAPI CD/DVD-ROM drive
[   28.877096] hdc: PLEXTOR DVDR PX-708A, ATAPI CD/DVD-ROM drive
[   29.297986] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)

```
As you can see, /dev/hdc is my dvd drive and it is using UDMA-33 mode (ultra dma 33).

---

### Post by SPRL on 2007-07-12
I think its this...

[  588.642980] scsi 5:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-4163B A106 PQ: 0 ANSI: 0
[  588.670659] sr1: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[ 4049.120214] scsi 6:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-H10N  JL10 PQ: 0 ANSI: 0
[ 4049.156388] sr2: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[16137.288134] scsi 7:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-4163B A106 PQ: 0 ANSI: 0
[16137.330530] sr2: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray

---

### Post by yabbadabbadont on 2007-07-12
Since it is being handled by the SCSI layer of the kernel, I don't think that DMA applies to it.  I assume they are USB or FireWire drives.  The same holds true for internal SATA drives.  Are you having trouble with your drives working correctly?

---

### Post by Hendrixski on 2007-07-12
Hey, I noticed your bean count showed you're pretty new, so I thought I'd write a quick welcome... hope you get your question answered.  :-)

---
WELCOME TO THE COMMUNITY!
We're all here to help new Ubuntu users because we love ubuntu, and we want to share our joy with others. 

If you prefer chatrooms then you should totally check out the channel #ubuntu on IRC.  Installing IRC is easy and fun.  Just go to applications-->Add/Remove and pick XChat from the list, click OK and you're done.

You can meet other Ubuntu users in your area too!  Just check out the Ubuntu LoCo teams for your city or state.

There is plenty of GREAT documentation written about Ubuntu, just ask google and you'll find it.  A lot of it is written by the same people who answer questions on these forums.  If dry manuals aren't your thing then relax and watch some videos.  [http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/) is a great website to get started, how to install, how to customize, how to set up your mail. etc.  Also check out [www.ubuntuvideo.com](www.ubuntuvideo.com) and [www.ubuntuclips.org](www.ubuntuclips.org).

I hope I'll see you around some more.  :-)

---

### Post by SPRL on 2007-07-12
yabbadabbadont... I was copying a movie with K9copy and it seems to take a long time to process. So I read if DMA wasn't enabled this might be the problem. Yes they are USB. If this is normal I will just leave it as is.


Hendrixski... Thank you.

---

### Post by yabbadabbadont on 2007-07-12
A full length movie can take quite a while to process, so it may not be a drive issue.  It could be, but copying a movie is a slow process normally.  Are they slow when you burn ISO files that you have downloaded?  (CD or DVD images)  The only thing left to check is to see if the USB 2.0 module has been loaded and is being used.  In a terminal window, run: ```
dmesg | grep -i usb
```  Look for "USB 2.0" and "EHCI" in the output.  If you like, go ahead and post the output and I will look it over too.

---

### Post by Hendrixski on 2007-07-12
> **SPRL said:**
> 
Hendrixski... Thank you.

No, thank YOU for trying out Ubuntu.  I've started to program stuff for Ubuntu lately, and I'm very happy to see new members who will be using the stuff I contribute.  It's the warm feeling a volunteer gets from helping people.  :-)

:-)  see you around.

---

### Post by SPRL on 2007-07-13
Thanks for all the help...:)

```
steve@steve-desktop:~$ dmesg | grep -i usb
[   10.921639] usbcore: registered new interface driver usbfs
[   10.921661] usbcore: registered new interface driver hub
[   10.921683] usbcore: registered new device driver usb
[   10.922548] USB Universal Host Controller Interface driver v3.0
[   10.922739] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   10.922874] usb usb1: configuration #1 chosen from 1 choice
[   10.922901] hub 1-0:1.0: USB hub found
[   11.029104] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   11.029228] usb usb2: configuration #1 chosen from 1 choice
[   11.029253] hub 2-0:1.0: USB hub found
[   11.139026] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   11.139141] usb usb3: configuration #1 chosen from 1 choice
[   11.139166] hub 3-0:1.0: USB hub found
[   11.244721] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   11.244837] usb usb4: configuration #1 chosen from 1 choice
[   11.244863] hub 4-0:1.0: USB hub found
[   11.354610] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   11.358542] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   11.358627] usb usb5: configuration #1 chosen from 1 choice
[   11.358656] hub 5-0:1.0: USB hub found
```

---

