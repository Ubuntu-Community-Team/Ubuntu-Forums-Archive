---
title: "Old Laptop...Can't get Linux on it..."
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by JT673 on 2007-05-20
I've got this old laptop that has no:
[LIST]
[*]working CD drive
[*]networking capabilities (Windows NT)
[*]USB-bootable BIOS
[/LIST]

I've tried several floppy-based Linuxes, and Wubi (no networking), but I can't seem to install Linux permanently on it.  Is my laptop doomed to a lifetime of Windows NT?

---

### Post by nerdman978 on 2007-05-20
NO! Stay away from NT, its probably the worst version of Windows. Have you tried using alternate CDs? What are your laptop's specs?

---

### Post by JT673 on 2007-05-20
I know, I'm writing this thread in my 2004 VAIO Feisty Fawn desktop.  But my laptop:

Presario 1900T-433
Intel(r) Celeron(r) Processor - 433 MHz
64MB SyncDRAM
4.8GB Ultra DMA Hard Drive
6x DVD Drive & 3.5" Diskette Drive
12.1" SVGA TFT Active Matrix
Microsoft Featured Home Collection + Word

And, no working CD drive (my desktop can burn CDs, but my laptop can't read it).

---

### Post by jfinkels on 2007-05-20
> **JT673 said:**
> I know, I'm writing this thread in my 2004 VAIO Feisty Fawn desktop.  But my laptop:

Presario 1900T-433
Intel(r) Celeron(r) Processor - 433 MHz
64MB SyncDRAM
4.8GB Ultra DMA Hard Drive
6x DVD Drive & 3.5" Diskette Drive
12.1" SVGA TFT Active Matrix
Microsoft Featured Home Collection + Word

And, no working CD drive (my desktop can burn CDs, but my laptop can't read it).

With only 64MB of RAM, you probably won't be able to get Ubuntu to work. Take a look at Damn Small Linux or Puppy Linux.

---

### Post by ugm6hr on 2007-05-20
Agree - Puppy Linux is a good choice for this hardware.  LitePup2.14 is even lighter (cut down version) and is easy to add extra bits to as required, although the new Puppy2.16 looks like a big improvement.

As for how to get it on the harddrive - I think Puppy has a facility to put a boot floppy in that will then access and load from the USB port.  And given the whole distro is under 100MB, shouldn't be a problem finding a USB memory stick to put it on!  Just search the Puppy documentation / forum for info.  Other option is to transfer the hard drive to your VAIO, install it with minimal video resolution, then transfer the drive back.  Obviously that requires a bit of dismantling of both laptops though.

---

