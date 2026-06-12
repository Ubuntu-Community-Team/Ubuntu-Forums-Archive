---
title: "Is it alright if I use a blank DVD instead of a CD when burning the ISO?"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by thadiusdean on 2007-01-22
Because I can't find any blank CDs. :P

In case I'm not clear enough, I'm referring to the ISO you burn when first starting out, i.e. installing Ubuntu.

---

### Post by wpshooter on 2007-01-22
> **thadiusdean said:**
> Because I can't find any blank CDs. :P

In case I'm not clear enough, I'm referring to the ISO you burn when first starting out, i.e. installing Ubuntu.

What do you mean you can't find any blank CDs ?

Go to Wal-Mart or where ever and get ourself some good brand named (I prefer Imation) CD-RW media 700mb.  If you make a mistake, you can erase them and use them over and over and over again.

---

### Post by thadiusdean on 2007-01-22
All my CD-Rs are used. I'd go get some but well... I have a lot of DVD-Rs right here.

---

### Post by NeoLithium on 2007-01-22
Well, I suppose if you're willing to waste a DVD-R that's ok; I've never tried it though; I always buy RW's aside from the DVD's that I burn...

---

### Post by thadiusdean on 2007-01-22
Alright, I'm going for it. :D

---

### Post by nyinge on 2007-01-22
> **thadiusdean said:**
> Alright, I'm going for it. :D

Don't forget to post back your results :).  I'm interested too.

---

### Post by ardchoille42 on 2007-01-22
> **thadiusdean said:**
> Because I can't find any blank CDs. :P

In case I'm not clear enough, I'm referring to the ISO you burn when first starting out, i.e. installing Ubuntu.

Burning the ISO to a blank DVD5 is fine, I;ve done it a number of times with no ill effects.

---

### Post by thadiusdean on 2007-01-22
Well, I get this:

I/O error
Error reading boot CD.
Reboot

I'll search around and check this thread, and if the problem isn't solved then I'll post a different thread.

EDIT: this popup came up after choosing both "Start or install Ubuntu" and "Check CD for defects" in the preliminary install screen.

EDIT: looks like I found the problem: 

[http://www.ubuntuforums.org/showthread.php?t=192689&highlight=error+reading+boot+cd](http://www.ubuntuforums.org/showthread.php?t=192689&highlight=error+reading+boot+cd)

I'll post back with results.

EDIT: Updated the DVD drive firmware... didn't help. Back to the research.

---

### Post by tonyr1988 on 2007-01-22
What program did you use to burn the DVD?

What speed did it burn at? Try at the lowest possible speed (if you didn't before) to ensure there were no errors during burning?

---

### Post by thadiusdean on 2007-01-22
> **tonyr1988 said:**
> What program did you use to burn the DVD?

What speed did it burn at? Try at the lowest possible speed (if you didn't before) to ensure there were no errors during burning?
I used the one the site recommends: Infra Recorder. I've also tried burning it at the lowest speed, and it still doesn't work. :(

EDIT: This thread seems to say that the problem is with the actual disks:

[http://www.ubuntuforums.org/showthread.php?t=328391&highlight=error+reading+boot+cd](http://www.ubuntuforums.org/showthread.php?t=328391&highlight=error+reading+boot+cd)

I guess I'll go buy some CD-Rs tomorrow. Could knowing my specs help?

EDIT: also I'm trying to use the AMD Athlon 64-bit version of Ubuntu--I have an Athlon 64 4000+.

---

### Post by thadiusdean on 2007-01-23
I have come to the conclusion that my computer just refuses to install Ubuntu. This is probably due to my hardware:

```
--------[ Summary ]-----------------------------------------------------------------------------------------------------

    Computer:
      Operating System                                  Microsoft Windows XP Home Edition
      OS Service Pack                                   Service Pack 2
      DirectX                                           4.09.00.0904 (DirectX 9.0c)
      Computer Name                                     HAL-9000 (Travis' Computer)
      User Name                                         **********

    Motherboard:
      CPU Type                                          AMD Athlon 64, 2400 MHz (12 x 200) 4000+
      Motherboard Name                                  Asus A8N-SLI Premium
      Motherboard Chipset                               nVIDIA nForce4, AMD Hammer
      System Memory                                     1024 MB  (DDR SDRAM)
      BIOS Type                                         Award (05/30/05)
      Communication Port                                Communications Port (COM1)
      Communication Port                                ECP Printer Port (LPT1)

    Display:
      Video Adapter                                     RADEON X850 Series - Secondary  (256 MB)
      Video Adapter                                     RADEON X850 Series  (256 MB)
      3D Accelerator                                    ATI Radeon X850 XT (R480)
      Monitor                                           Plug and Play Monitor [NoDB]  (PEH051400964)

    Multimedia:
      Audio Adapter                                     Creative SB0410 SB Live! 24-bit Sound Card
      Audio Adapter                                     nVIDIA MCP04 - Audio Codec Interface

    Storage:
      IDE Controller                                    NVIDIA nForce4 Parallel ATA Controller
      IDE Controller                                    NVIDIA nForce4 Serial ATA Controller
      IDE Controller                                    NVIDIA nForce4 Serial ATA Controller
      SCSI/RAID Controller                              SCSI/RAID Host Controller
      Floppy Drive                                      Floppy disk drive
      Disk Drive                                        ST3250823AS  (250 GB, 7200 RPM, SATA)
      Disk Drive                                        HP Photosmart C4150 USB Device
      Disk Drive                                        Apple iPod USB Device  (1945 MB, USB)
      Optical Drive                                     PLEXTOR DVDR   PX-712A  (DVD+RW:12x/4x, DVD-RW:8x/4x, DVD-ROM:16x, CD:48x/24x/48x DVD+RW/DVD-RW)
      Optical Drive                                     ZN7314R LRJ861I SCSI CdRom Device
      Optical Drive                                     ZN7314R LRJ861I SCSI CdRom Device
      Optical Drive                                     ZN7314R LRJ861I SCSI CdRom Device
      SMART Hard Disks Status                           OK

    Partitions:
      C: (NTFS)                                         238464 MB (109875 MB free)

    Input:
      Keyboard                                          PS/2 Keyboard
      Mouse                                             PS/2 Compatible Mouse

    Network:
      Network Adapter                                   Realtek RTL8139 Family PCI Fast Ethernet NIC  (192.168.1.5)

    Peripherals:
      Printer                                           Auto HP DeskJet 820C Series v8.5 on REID
      Printer                                           Auto HP DeskJet 820Cse on REID
      Printer                                           HP DeskJet 820Cse
      Printer                                           HP Photosmart C4100 series
      Printer                                           Microsoft Office Document Image Writer
      USB1 Controller                                   nVIDIA MCP04 - OHCI USB Controller
      USB2 Controller                                   nVIDIA MCP04 - EHCI USB 2.0 Controller
      USB Device                                        HP Photosmart C4100 series (DOT4USB)
      USB Device                                        HP Photosmart C4100
      USB Device                                        USB Composite Device
      USB Device                                        USB Mass Storage Device
      USB Device                                        USB Mass Storage Device
      USB Device                                        USB Printing Support



```
Tell me if this all looks alright or not.

EDIT: I came to this conclusion after trying Instalinux, and it giving me the same "Error 17: File not found" thing as when I tried the windows install prototype. I have a feeling using CD-RWs won't help either. :( I'm going to try them anyway because I'm desperate (this community is too good to try another distro.)

---

### Post by Happy_Man on 2007-01-23
The 64-bit version of Ubuntu is not nearly as stable as the 32-bit version. I suggest you install that version, because it may just be an install conflict easily remedied. I had the same problem, and that was how I fixed it. Post back with results-I'm intrigued! (This also means I'm the biggest nerd alive :biggrin:)

---

### Post by thadiusdean on 2007-01-23
> **Happy_Man said:**
> The 64-bit version of Ubuntu is not nearly as stable as the 32-bit version. I suggest you install that version, because it may just be an install conflict easily remedied. I had the same problem, and that was how I fixed it. Post back with results-I'm intrigued! (This also means I'm the biggest nerd alive :biggrin:)
You got it.

EDIT: Same as before. :(

---

### Post by thadiusdean on 2007-01-23
Bump. Can someone look over my computer, or can you not really tell if Ubuntu is compatible by just looking at it?

---

### Post by Icemanyurt on 2007-01-23
I have installed and ran both the 64 and 32 bit version of Ubuntu (I think Dapper Drake) on a machine with that same processor and motherboard.  So I think it should work.

Try putting the ISO on a cd, hell if you still don't want to go by CD-Rs I'll mail you a copy that is how much I like this thing...

---

### Post by Happy_Man on 2007-01-23
Wow...this is really odd...

I know this may sound really drastic, but have you considered that your writer may be having problems? I mean, if NOTHING works... have you gotten them CD-Rs yet? If they don't work, I seriously think your hardware may be the problem.

---

### Post by thadiusdean on 2007-01-23
I'll probably... well... damn, I have a busy week and weekend ahead of me. I'll hopefully have some time this weekend to buy some CD-R/RWs and try those out. If I'm crazy enough I may try pulling out a drive from my other computer and installing it using that...

I guess not much can happen until then...

---

### Post by thadiusdean on 2007-01-24
Alright, bought some CD-RWs, tried it again and it worked. But a new problem has come up. See my new thread to see what's going down.

EDIT: I mean new thread after I have looked around for an answer first.

---

