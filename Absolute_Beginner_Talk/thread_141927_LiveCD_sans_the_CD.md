---
title: "LiveCD sans the CD?"
date: 2006-03-09
forum: Absolute Beginner Talk
---

### Post by datenshi on 2006-03-09
Okay, I have a stupid question for you here, but I figured it wouldn't hurt to ask...

I'm really new to Linux and although I can use Windows decently well, I'm not exactly what you'd call a tech-savvy person.  But I would love to play around with Ubuntu a bit and see if I like it.  Here's my problem, though: I can't just download the iso and burn a LiveCD for myself because my CD-RW drive is completely busted.  This hasn't been a big hurdle for me thus far, but as far as trying out Ubuntu or any Linux distro it leaves me stumped.  Is there any way to run something like a LiveCD without actually using a CD?

---

### Post by cilynx on 2006-03-09
VMWare is your friend.

[http://www.vmware.com/vmtn/appliances/ubuntu.html](http://www.vmware.com/vmtn/appliances/ubuntu.html)

---

### Post by arathorn2nd on 2006-03-09
If you have a working CD-ROM, you can ask a friend to burn a LiveCD or just ask for it on [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

If you don't, that can be quite difficult. There's a Brazillian distro named Kurumin, based on Knoppix, that can boot from a LiveCD image on the hard disk if it's in a FAT32 partition. But you'll need a floppy or USB Drive with the boot image.

I'm not sure if that's possible in Ubuntu.

---

### Post by aysiu on 2006-03-09
I don't know about Ubuntu, but you can download Damn Small Linux as [an embedded OS](http://dsl.thegeekery.com/current/dsl-embedded.zip) and run it straight within Windows.

There are also ways to run a Ubuntu .ISO within Windows using Qemu, but I haven't been able to do it (I can use Qemu in Ubuntu, though).

---

### Post by datenshi on 2006-03-09
thank you for the suggestions!  I tried out DSL and was pleasantly surprised with how well it worked (well, it was pretty slow, of course, but I wasn't expecting lightning speed on an emulator).  I don't have a working CD drive at all, so unfortunately even asking a friend to burn me a disc is out of the question at present.

Once I can get everything downloaded I'll try VMWare next...  DSL works pretty well, but honestly I'd like to try Ubuntu half because this place has such a great support community.

---

### Post by Sutekh on 2006-03-09
Try arathorn2nd's suggestion

[https://shipit.ubuntu.com/]("https://shipit.ubuntu.com/")

It could take a while for the CDs to get to you.  Get someone else to download the ISO and burn it for you?

---

### Post by datenshi on 2006-03-09
Like I said, 

> I don't have a working CD drive at all, so unfortunately even asking a friend to burn me a disc is out of the question at present.

Thank you though :)

---

### Post by Sutekh on 2006-03-09
No I don't mean you *give* them the ISO to burn, I mean get someone to *download* it for you and burn it for you.

---

### Post by aurifex on 2006-03-09
Do you have another drive that can at least **read** CDs? Some people have more than one disc drive in their computers, as I did when I had a CD-RW and a DVD drive back a few years ago.

---

### Post by datenshi on 2006-03-09
Uhh...  like I've said twice now, I don't have a working CD drive in my computer at all.  I'm using a laptop, so there's only the one drive, and it is completely physically broken.  I don't have the money to get it replaced at the moment, unfortunately.

---

### Post by Qrk on 2006-03-09
Try Debian... it can install from a floppy. Once you've booted from the floppy you can do a standard install over the network.

Their instructions are here:
[http://www.debian.org/releases/stable/i386/](http://www.debian.org/releases/stable/i386/)

---

### Post by datenshi on 2006-03-09
Well, I got Ubuntu running on VMware, and I'm very impressed so far!  I haven't gotten to try all my hardware yet, but it recognized my iPod immediately.  However, when trying to install new applications or change the system clock, it keeps asking me for a password...  I don't know what to put in, since the system never asked me for one to begin with when I first started it up...  what should I do?

---

### Post by aysiu on 2006-03-09
The live CD (if that's what you're running in VMWare) doesn't have a password--or it has one, but I've never known what it is.

---

### Post by datenshi on 2006-03-09
I'm not honestly sure what version I have... I downloaded the installer from the VMware website that was preconfigured to work with VMware.

So will I not be able to install new applications at all...?

---

### Post by Sutekh on 2006-03-09
[QUOTE=aysiu]The live CD (if that's what you're running in VMWare) doesn't have a password--or it has one, but I've never known what it is.[/QUOTE]
I'm using the LiveCD right now, there is no password for using sudo

But the VMWare website just won't work here so I cna't find out if there is a password for the Ubuntu environment on VMWare.  I'm pretty sure that they are not LiveCD sessions.

---

### Post by datenshi on 2006-03-09
I was able to find the answer on the VMware forums :D  The password for their version is "ubuntu".  Haha, I feel a little silly for not guessing it.

---

