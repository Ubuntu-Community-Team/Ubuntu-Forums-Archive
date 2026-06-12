---
title: "Remote desktop on pc with no vga"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by ProteinPappa on 2007-12-29
Hello

My scenario is this: I have an old P3 500 MHz computer with the hard drives I've collected during the years which I use as a kind of data storage box. Until recently it ran WinXP, but after I started to use Ubuntu on my laptop a few months back I looked into changing to a more resource-modest OS. I have used the windows remote desktop method from another Windows computer to administer it when needed and otherwise used ftp to transfer files back and forth. I basically want the same functionality as before, but with Linux.

Because Ubuntu is the only Linux distro I am somewhat familiar with, I went with Xubuntu on the server machine. Now I have gotten a long way - I can log on with VNC from the Ubuntu machine. The tricky part is this: I currently have a nVidia AGP graphics adapter in the server machine, but for seveal reasons, it cannot stay. The problem is that I can't start a remote session when the server boots without the card. I assume this is because X isn't started or something similar. 

My initial idea is to install some sort of bogus vga driver that makes X set up a desktop manager, but I have not succeeded in finding this.

Thanks for any help!

---

### Post by blueridgedog on 2007-12-29
Based on my experience, you will not be able to boot without a graphics device of some type.  That said, there is nothing you can't administer via an SSH connection, so a cheap/used PCI card would work.

---

### Post by ProteinPappa on 2007-12-29
> **blueridgedog said:**
> Based on my experience, you will not be able to boot without a graphics device of some type.  That said, there is nothing you can't administer via an SSH connection, so a cheap/used PCI card would work.

I have actually booted - I can log on with ssh and ping and all that. The trouble is that the startup command I added to run the vnc connection doesn't seem to work. For some reason, I can't start vnc with ssh even though the display is connected - the exact same command typed in a terminal on the server itself however works.

Anyway, I'll start searching the basement for that good old voodoo 3 card.

---

### Post by blueridgedog on 2007-12-29
I am impressed.  I have not seen a system that would boot with out an output device...I must be behind the times.

---

### Post by ProteinPappa on 2007-12-29
> **blueridgedog said:**
> I am impressed.  I have not seen a system that would boot with out an output device...I must be behind the times.

Earlier when I used XP the only devices in the machine was disks and network card plus the mobo with cpu and memory. It only has 2 wires connected - network and power.

Speaking of behind the times, when I booted with Linux I was told the BIOS was of to old and age - the cutoff was 2000, and it's from 1999. Oh well.

---

### Post by Furat on 2007-12-29
Did you try to use ssh X forwarding feature ?? ie "ssh -X serverIP"

---

### Post by ProteinPappa on 2007-12-29
> **Furat said:**
> Did you try to use ssh X forwarding feature ?? ie "ssh -X serverIP"

Yes, that's the command I use for ssh access. It gives me a terminal, but I can't use any graphical programs. In other words, I can edit files with nano, but not gedit, which gives some error message.

---

### Post by dim_hyder on 2007-12-29
Try logging in via ssh and entering:

sudo dpkg -reconfigure xserver-xfree86

X is probably still expectng the old VGA card.

Cheers,

Dim Hyder

---

### Post by Maxtorm on 2007-12-30
> **ProteinPappa said:**
> ...
I basically want the same functionality as before, but with Linux.
What is it that you need a local graphic interface to configure/administer that you couldn't otherwise administer via the command line interface or a remote GUI?

---

### Post by lswest on 2007-12-30
also if there is no xserver running then vnc cannot connect to the display, so without having an xserver running you can basically just use ssh, however that should be fine for admining a server.

---

### Post by ProteinPappa on 2007-12-30
I guess you're right. It's just that I'm quite the noob when it comes to Linux and the place where I set the computer tower makes it a job to get it out and put in a card if something is needed. I guess as a future Linux-only user having to learn to use the terminal properly isn't a bad thing.

Thanks for all your help, people, it's apreciated.

---

