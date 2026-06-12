---
title: "SATA II DISKS and LINUX"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by diyar on 2006-09-23
Some body must have an idea about SATA II hard disk recognition in linux system!


thanks

---

### Post by bulldog on 2006-09-23
Try the live cd and see if your hdd is seen at all.

---

### Post by diyar on 2006-09-23
&#305; have tried live various cds including ubuntu with no avail!

---

### Post by bulldog on 2006-09-23
Then it's not supported I'm afraid.

But is it possible [I think it can] you can set your Sata2 to Sata1 at the back of the hdd?

Maybe you can try that but I have not much knowing about sata2.

---

### Post by spockrock on 2006-09-23
Ummm.... I have 2 sata II harddrives, both have worked since breezy.... It maybe an issue with your sata controller.  What motherboard are you using, and what versions/distros are you trying to use?

---

### Post by ReaderRat on 2006-09-23
> **bulldog said:**
> Try the live cd and see if your hdd is seen at all.
I'm having the same problem. I have 2-320Gig SATA II drives and Linux shows only one. I tried the Ubuntu Live CD and the gparted Live CD and the second drive is not recognised. There are 3 settings for drives in the BIOS: 1)RAID,2)AHCI,and 3)IDE. I did not want to fool around with RAID, and I did not know what AHCI was (I googled & still did not understand.), so I picked IDE. I have an Intel D945GPM motherboard.
What next?:confused:

---

### Post by spockrock on 2006-09-23
have you tried installing from the alternate disc??

---

### Post by ReaderRat on 2006-09-23
What is the alternate disc? I got Ubuntu-64 from a third party & there was only one (DVD) disc.

---

### Post by crokett on 2006-09-23
> **ReaderRat said:**
>  so I picked IDE. 

For regular IDE you need configure a master drive and a slave drive if they are both on the same controller. This is done with jumpers on the drive. I have no idea if this still applies for a SATA drive that is configured for IDE.

---

### Post by spockrock on 2006-09-24
> **ReaderRat said:**
> What is the alternate disc? I got Ubuntu-64 from a third party & there was only one (DVD) disc.

Ok, there are two discs that you can get alternate which is a non graphical text based installer, or the desktop disc, which is a live disc with an installer.  

On another note, can I suggest that you dont install 64 bit Ubuntu.  As of right now, there is no advantage in both windows or linux using 64 bit.  The speed boost like little to none, and in some cases 32-bit operations are faster.  I have an AMD X2, and use 32 bit with the k7 kernel, 64 bit really isnt mature enough, for both windows and linux.  

[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

download the alternate disc, or try the 386 desktop version again if you like, but hopefully this will work.

---

### Post by diyar on 2006-09-24
the chipset is ATI 1150+SB600. could this be the problem?

---

### Post by fragos on 2006-09-24
Not all mobo's support SATA II.  Many new SATA drives are type II but should have a strap on the back to select SATA I.  See if you can find your mobo on [www.pcclub.com](www.pcclub.com).  If not in the mobo specs user's will frequently comment on issues and how they worked around them.  If a mobo only says its SATA, it's probably only SATA I.

---

### Post by spockrock on 2006-09-24
yes, it is it seems that ATI's SB600's pata, sata and audio were added in 2.6.17 RC3 kernel.  Hmm...I think edgy might have the right kernel but dapper I believe is on 2.6.16, but edgy is on kernel 2.6.17-7 you could try the edgy knot 3 live disc, however remember its about to go beta, and isnt really recommended except for testers.

sorry I know that prolly isnt what you wanted to hear but I hope that helps.

---

### Post by spockrock on 2006-09-24
> **fragos said:**
> Not all mobo's support SATA II.  Many new SATA drives are type II but should have a strap on the back to select SATA I.  See if you can find your mobo on [www.pcclub.com](www.pcclub.com).  If not in the mobo specs user's will frequently comment on issues and how they worked around them.  If a mobo only says its SATA, it's probably only SATA I.

no his board definatly supports sata 2, and sata 2 is backwards compatiable, so if its plugged into a sata 1 port it should just work, but at sata 1 speeds.

---

### Post by fragos on 2006-09-24
Thanks for expanding my horizon -- It makes perfectly good sense that a SATA II drive would automatically adjust to a type I interface.  Perhaps the type I/II strapping I saw was design overkill.

---

### Post by ReaderRat on 2006-09-24
> **spockrock said:**
> 
On another note, can I suggest that you dont install 64 bit Ubuntu.  As of right now, there is no advantage in both windows or linux using 64 bit.  The speed boost like little to none, and in some cases 32-bit operations are faster.  I have an AMD X2, and use 32 bit with the k7 kernel, 64 bit really isnt mature enough, for both windows and linux.
Wish I had known this before I re-installed. I will live with 64-bit until I screw up again and have to re-install. I installed with "IDE" ticked in the BIOS again, and I will live with one HDD for now. It seems I have to have a "native Windows driver" (or the equivalent in Linux) to get the second drive to appear to partioioning software. (Even though the BIOS recognises it.)
Thank you for your help spockrock.:)

---

### Post by diyar on 2006-09-25
thank you spockrock...

---

