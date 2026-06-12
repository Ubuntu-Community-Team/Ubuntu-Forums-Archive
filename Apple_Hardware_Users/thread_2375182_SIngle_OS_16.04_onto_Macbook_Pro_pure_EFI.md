---
title: "SIngle OS 16.04 onto Macbook Pro pure EFI"
date: 2017-10-22
forum: Apple Hardware Users
---

### Post by TBerk on 2017-10-22
OK, so this has been done before, in fact I had this system running a single partition (OS & Home) but it was 17.10 beta/developer's.  
In my attempts to reload a single install of LTS 16.04 with a partitioning scheme of:

- EFI (500M+)
- '/' (16G)
- '/Home' ("all the rest of the HD; 400G+)

I've bumped my head over and over with Internet searches that propose"[SOLVED]" but don't resolve my situation.

The main struggle to overcome is the failure, right at the end of a clean install of "grub-efi-amd64-signed failed to install&#8221; [duplicate] stuff that seems everywhere but cant get me anywhere.

I'm currently trying boot-repair-disk, but there are a few things there I'm contending with: 

a) The MacbookPro (8,1) has a broken CD/DVD drive so it's all USB drives in terms of utils and installs.
b) The system isn't close to an Internet Connection based on Ethernet, and the built in wifi requires the Broadcom Drivers be installed to activate the default (wifi) Networking as I use the computer. So I make LiveCDs onto flash drives.

Boot-Repair-Disk, booting from a USB flash drive, asks for Repositories to be appended/edited but I'm doing so (It's finding my internal HD's /dev/SDA3 as the location where the active 'sources.list' is located.) I've been able to successfully run Leafpad in sudo mode and edit this file but it wont enable the 'CD = 16.04 on USB' in that first line, even finding and trying a seemingly backed up copy on the util's drive itself. 

I've been trying to get it to see the second USB flash drive ( LiveCD 16.04x64) I've installed the OS with, with .... (drum roll) repositories on it.

The URL to the main thread here has been closed after some 100 pages of "hey!, Great!, Thx..." type replies, so my 'Searching Before Asking/Posting is a bit bogged down.

Even if boot-repair-disk turns out not to be my solution, what I'm hoping to end up with is:

16.04 64bit, all by itself, booting pure EFI if possible, on a multi-partitioned Apple Macbook Pro. (And having to 'Sneaker-Net' via USB any utils, patches, info, and so on from a second PC nearby...)

Thx,
TBerk

---

### Post by TBerk on 2017-10-22
PS- I meant to mention the actual flavor I default to is Ubuntu Studio 16.04.3...

---

### Post by oldfred on 2017-10-23
Moved to the Apple sub-forum where those who know Mac may be able to help.
Do not know Mac.

Usually the error on not installing to the ESP with PC, is that it is not seen as ESP on sda (or first drive if NVMe) or need a dosfsck. With a Mac not sure as I do not know Mac.

---

### Post by ratell on 2017-10-23
If you are doing single boot why not just go with the installer's partitioning? I used the LVM option which has worked well and offers some flexibility after the install. I'm very much a newbie but a lot of guides seem to be down on the using a home partition. Maybe that's what's causing your difficulties.

---

