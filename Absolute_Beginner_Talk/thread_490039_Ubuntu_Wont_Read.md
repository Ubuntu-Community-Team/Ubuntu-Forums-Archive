---
title: "Ubuntu Wont Read"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by Dexter1337 on 2007-07-02
I put it in ym Cd drive and restart and it wont do anything help plz

---

### Post by benanzo on 2007-07-02
Are you trying to boot the Ubuntu LiveCD?  If so you most likely have your BIOS set to boot from hard disk first.  You need to press F2 or Delete (on an ASUS board) at the BIOS screen and change your boot settings to CD as first choice.

---

### Post by KIAaze on 2007-07-02
If that doesn't solve your problem, check that your .iso download isn't corrupted by doing a checksum.
Here's a tutorial of how to do it:
[http://www.psychocats.net/ubuntu/iso#checksum]("http://www.psychocats.net/ubuntu/iso#checksum")

The download link for the used program is at the top of the page.

---

### Post by Dexter1337 on 2007-07-02
Um i need help with the Bios
I go to it by F1 Then I go to BooT Priorities and I make it Cd on top then I restart and nothing happens

---

### Post by Megaqwerty on 2007-07-02
1. Did you remember to choose "Save and Quit" in the BIOS, not just "Quit"
2. Try KIAaze's suggestion, if you downloaded a corrupted .iso file, there is no chance of it working, you will need to re-download it, and check again to make sure it isn't corrupted this time.
3. If your checksum is in fact correct, make sure the CD you are using isn't scratched
4. If it isn't scratched, try re-burning it at 1x

---

### Post by Dexter1337 on 2007-07-02
I have the livecd I order from Shipit

---

### Post by Megaqwerty on 2007-07-02
Hmm...well, nevertheless check that it's not scratched, and make sure your changes to the BIOS were saved.

---

### Post by KIAaze on 2007-07-02
And if you have access to another PC, try it on that one to see if it works there.

---

### Post by Dexter1337 on 2007-07-02
This is how I have my Bio's Set
[IMG]http://i109.photobucket.com/albums/n73/DeXUserBarMaker/Picture066.jpg[/IMG]

---

### Post by Dexter1337 on 2007-07-02
Also do I need the 256 Mb Of Ram to Run the LiveCd?Cause right now I onyl have 128Mb.

---

### Post by Megaqwerty on 2007-07-02
From the Ubuntu Desktop Edition Page:

> System Requirements

Ubuntu is available for PC, 64-Bit and Mac architectures. CDs require at least 256 MB of RAM. Install requires at least 4 GB of disk space.

---

### Post by dptxp on 2007-07-02
You will need alternate CD to install and use XUBUNTU.

The CD should have booted though, at least gone to first screen.

---

### Post by KIAaze on 2007-07-02
And make sure you get the correct version: 32bit or 64bit depending on your processor.
And amd64, i386 or PowerPC.

---

### Post by enopepsoo on 2007-07-02
nice screen shot.  top notch.

---

### Post by Dexter1337 on 2007-07-02
> **KIAaze said:**
> And make sure you get the correct version: 32bit or 64bit depending on your processor.
And amd64, i386 or PowerPC.
I have intel and when I got te Cd's they are Red did I get the right kind?

---

### Post by Golyadkin on 2007-07-02
It depends on which Intel you have, whether it is a 32 bits (op to Pentium 4 roughly) or a Core 2 Duo, which is 64 bits.

---

### Post by benanzo on 2007-07-02
If you've only got 128 mb ram I suspect you've got a really old Intel or AMD processor.  You need to use the Alternate install for 32bit i386.  [Here's the download page.]("http://releases.ubuntu.com/7.04/")

Scroll down until you see **Alternate install CD** and select this one:
> 
_PC (Intel x86) alternate install CD_

For almost all PCs. This includes most machines with Intel/AMD/etc type processors and almost all computers that run Microsoft Windows, as well as newer Apple Macintosh systems based on Intel processors.        Choose this if you are at all unsure.

Good luck!

---

### Post by tcoffeep on 2007-07-02
On my laptop I had to set it up specifically to boot.

There should be an option for booting. Then you press, well for me, F12, and choose your CD/DVD drive.

---

### Post by dptxp on 2007-07-02
Red one is 32 bit.
If you want to use it to install, make a SWAP partition of 1-2 GB first at end of your disk using GPARTED (download GPARTED iso, Download and install Infrarecorder to burn, burn to CD using BURN IMAGE command in ACTIONS MENU , run live, and make your partitions).
You shall retain the SWAP partition when you install from Live Ubuntu, the Live CD shall use it and refuse to change.

But Ubuntu is not recommended with 128 bit RAM even if are able to run it with SWAP.
Use alternate CD, install XFCE (Xubuntu). I suggest a SWAP first anyway.

---

