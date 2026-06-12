---
title: "Worth resurrecting a iBook G4 PowerPC?"
date: 2010-11-01
forum: Apple Hardware Users
---

### Post by darrelljon on 2010-11-01
I have come into possession of a PowerPC iBook G4. I installed Kubuntu 8.04 with much difficulty but there's not even an office suite let alone much modern useful software. I could only boot live because when installed the b43 wireless hangs the boot.

Is it worth getting all the repo discs and installing everything (only have 40Gb HDD) or should I just get Mac OS X 10.5 Leopard and be done with it?

---

### Post by linuxopjemac on 2010-11-01
Have a look at [MintPPC]("http://mintppc.org"). It will run fine on your iBook G4.

---

### Post by darrelljon on 2010-11-01
Does it have any decent software? I'd be tempted to just install Debian instead. What are the advantages.

---

### Post by linuxopjemac on 2010-11-01
It is Debian Squeeze, with some extra themes and packages of Linux Mint. You will have the complete repository of Debian (30.000 packages, hope that's enough for you).

---

### Post by darrelljon on 2010-11-01
Can't find the link for Mint PPC anywhere?

---

### Post by linuxopjemac on 2010-11-02
[http://mintppc.org](http://mintppc.org)
Make an account and read the installation instructions.

---

### Post by darrelljon on 2010-11-02
> **linuxopjemac said:**
> [http://mintppc.org](http://mintppc.org)
Make an account and read the installation instructions.

Seriously? Register just for a link to the ISO, that's ridiculous.

---

### Post by linuxopjemac on 2010-11-02
have fun with Ubuntu then.

---

### Post by dsandbeck on 2010-11-02
I'm running Ubuntu 10.10 on my iBook G4 with no difficulty. Runs very nicely, and in fact I think the battery life is improved under Ubuntu from OSX (10.5). So yeah, I think it's worth it. However, I don't know your specs. I've got 1.5GB RAM and the 1.33Ghz G4.

---

### Post by el_heffe on 2010-11-02
I have a PB G4 1ghz with 1.25G Ram.  It ran ubuntu with all sorts of sexiness.  It was faster, battery lasted 15 minutes vs. 5 in OS X, and everything pretty much worked(except sleep- 12" :( )
BUT, the HD took a dump and it just isn't worth it to me to open the damned thing up just to replace the HD.

I *REALLY* wanted to try Mint based on what I have seen, but two things happened.  One, I couldn't get the Debian CD I had burned to work, and two- the HD crashed...  When it worked- it worked GREAT!

---

### Post by linuxopjemac on 2010-11-08
I have bad experience with CD's too. That's why I advise to install via a USB stick. It's very easy.

---

### Post by darrelljon on 2010-11-08
Installed Debian 5.01 from CD, it works great except for broadcom wifi.

---

### Post by Nonmouse on 2010-11-09
> **linuxopjemac said:**
> I have bad experience with CD's too. That's why I advise to install via a USB stick. It's very easy.
 
 
And how did you get the USB install to work on a PPC?  Can you explain, I would like to install on my MacMini 1.5GHz G4.

---

### Post by linuxopjemac on 2010-11-09
See the installation instructions of MintPPC.

---

### Post by Dukenukemx on 2010-11-10
> **dsandbeck said:**
> I'm running Ubuntu 10.10 on my iBook G4 with no difficulty. Runs very nicely, and in fact I think the battery life is improved under Ubuntu from OSX (10.5). So yeah, I think it's worth it. However, I don't know your specs. I've got 1.5GB RAM and the 1.33Ghz G4.
How's flash support?  Does flash content on websites work better now?

---

### Post by shawnhcorey on 2010-11-10
FYI: the Desktop CD does not fit onto a standard CD; use the Alternative CD instead.  The only difference between them is that the Desktop version uses the GUI installer and the Alternative uses a text-based one.  The software each installs is exactly the same.  (The text-based installer is smaller than the GUI one, so everything can fit on a standard CD.)

> **Nonmouse said:**
> And how did you get the USB install to work on a PPC?  Can you explain, I would like to install on my MacMini 1.5GHz G4.

Those instructions are for the mini.iso; you need an internet connection for a complete install.

To create a USB you can boot from (without the internet), see:

[HOWTO Create A Bootable USB Drive From An ISO Image For Apple PowerPCs In Linux]("http://sites.google.com/site/shawnhcorey/howto-create-a-bootable-usb-drive-from-an-iso-image-for-apple-powerpcs-in-linux")


And to boot, see:

[HOWTO Boot Apple PowerPCs From A USB Drive In Open Firmware]("http://sites.google.com/site/shawnhcorey/howto-boot-apple-powerpcs-from-a-usb-drive-in-open-firmware")

It is recommended that you print out the boot instructions since it's the only way to read them during boot.  (That's if you don't have another computer to look them up on.  :))

---

