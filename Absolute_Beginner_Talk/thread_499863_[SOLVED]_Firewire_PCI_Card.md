---
title: "[SOLVED] Firewire PCI Card"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by thebucksstop on 2007-07-13
Hope someone can help me. Mods - this may be in the wrong forum, if so, please punt it across to a more appropriate one, and sorry for occupying your time!!

So, I'm in need of Firewire (ideally 800) on my PC and Laptop. I bought a PCI expansion card and a PCMCIA card from Maplins for this purpose. They're both based on Texas Instruments chipsets, details of the cards are [here]("http://www.avlab.com.tw/1394/1008_0073_000a.htm") and [here]("http://www.avlab.com.tw/1394/1005_0014_000bx.htm"). I checked the chipsets against the linux1394.org hardware list, and TI chipsets seem to be well supported.

So, the PCMCIA card worked fine, plug-n-play, no worries. The PCI card, however, is not proving so easy. I dropped it in, booted up, and plugged in my external hard drive...no response. Tried ExtHDD again, using FW400 wires rather than 800...no response. Ran [FONT="Courier New"]lspci[/FONT] and [FONT="Courier New"]lshw[/FONT] to see whether the PCI card was being picked up or not, and it was listed in the output of both commmands.

In short - PCI card is in the machine, appears compatible, appears to be picked up through the PCI bus, but will not allow an external HDD to connect via any input socket. Does anyone have any pointers where I can go with this, to try and sort it out? I'm at work atm, so I can't try anything immediately, it'll have to wait till I get back tonight...but please don't hold of replying until then, lol!

Cheers for anything you can give me!!

---

### Post by phr0ze on 2007-07-13
I'm not 100% sure but maybe it's not the firewire card but the process responsible for automounting didn't get configured to detect drives on the new PCI device.

---

### Post by thebucksstop on 2007-07-13
phr0ze,

Thanks, I'll look into that when I get home this evening. I did check that the drive was automounting properly, through a backplate USB socket though. I've not (so far as I'm aware) messed around with any automounting properties, but, as I say, I'll check it out when I'm home. 

Thanks for the input!
C

---

### Post by tgalati4 on 2007-07-13
Do a fresh boot, plug the drive in then post:

>dmesg | tail -n 50

If you haven't had any luck, then try moving the PCI cards around.  Sometimes swapping slots will help free up resources.

---

### Post by thebucksstop on 2007-07-13
Cheers, I'll give it a shot in a few hours when I'm back at that box.

Do you mind explaining what that command will do?

I'll post the output later on.

---

### Post by tgalati4 on 2007-07-13
dmesg prints out system messages since last boot.
| is the pipe operator.  It sends the output of dmesg to the next command.
tail prints out the last few lines of a file.  In this case the last 50 lines (-n 50)

When you plug in a firewire drive, several things happen and they are recorded in dmesg.  If there is a conflict or mount error, it will usually show up in dmesg.  A convenient way to fix things in Linux is to check for errors in /var/log and dmesg.

---

### Post by thebucksstop on 2007-07-24
Sorry for such a long delay in getting back to you all. Thanks for your help, but it turns out it wasn't needed. I don't know what happened, but after a few boots (fiddling/faffing with other bits and pieces), the card started working with no problems. Marking the thread as solved...Cheers!

---

