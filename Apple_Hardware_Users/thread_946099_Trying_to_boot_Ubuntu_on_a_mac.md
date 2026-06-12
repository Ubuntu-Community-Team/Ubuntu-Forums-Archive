---
title: "Trying to boot Ubuntu on a mac"
date: 2008-10-13
forum: Apple Hardware Users
---

### Post by Gigidy5 on 2008-10-13
The Computer doesn't have a hard drive. I have the Ubuntu disk in the disk drive.

Holding C won't work.
Hitting Command Option Shift Delete won't work.
and Holding Option won't work.

So I booted the computer like normal and got a screen flashing the finder icon then a question mark, then repeating.

So I randomly hit buttons on the keyboard and got this.
[IMG]http://i202.photobucket.com/albums/aa315/gigidy5/IMGP8976.jpg[/IMG]


What do I do?

---

### Post by ppc_guy on 2008-10-13
just a guess here, but type: mac-boot

Pretty much tells you that on screen, but things can be confusing @ times..

hth,
ppc_guy

---

### Post by Gigidy5 on 2008-10-13
already tried that. It restarts and boots to a blue screen with the same Icon you see on the picture.

---

### Post by cyberdork33 on 2008-10-13
> **Gigidy5 said:**
> So I randomly hit buttons on the keyboard and got this.
What do I do?
That is the open firmware prompt. You get to it on bootup by using CMD+OPT+O+F

---

### Post by tiresia on 2008-10-13
What are you trying to do? Do you want to start your Mac from a Live CD?
Which kind of Mac do you have? Open Firmware has similar functions as BIOS in PC.
The command 'mac-boot' works to start a Mac OS on the HD.
If you don't have any HD installed, of course Open Firmware can't boot the system.

---

### Post by schauerlich on 2008-10-14
If you don't have a hard disk, that means that you don't have EFI available (which is why c and option didn't work). I'm not sure you'll be able to do much without a HD.

---

### Post by cyberdork33 on 2008-10-14
> **EDavidBurg said:**
> If you don't have a hard disk, that means that you don't have EFI available (which is why c and option didn't work). I'm not sure you'll be able to do much without a HD.
It is a PowerPC Mac. I don't think any of them have EFI...

---

### Post by schauerlich on 2008-10-14
> **cyberdork33 said:**
> It is a PowerPC Mac. I don't think any of them have EFI...

Wouldn't whatever they had on there doing the same stuff as EFI still be on the HD, though?

---

### Post by pxwpxw on 2008-10-14
> **EDavidBurg said:**
> Wouldn't whatever they had on there doing the same stuff as EFI still be on the HD, though?
New World Powerpcs (most g3, all g4 and g5) run on Openfirmware.
OF resides in the BootRom and does not need a hard drive.

This is OF on an iBookg4, run as a telnet server seen from a MacBook Macosx10.4.11  telnet client.
The ... are deleted garbage
OFW returns results on the same line sometimes.
There are some variations between  openfirmware versions.
The CD was an Alternate install I had at the time.

```

0 > **dev / .properties** 
model                   PowerBook6,5
compatible              PowerBook6,5
                        MacRISC3
                        Power Macintosh                        
...
 ok
0 > **dev /openprom .properties** 
name                    openprom
device_type             BootROM
model                   OpenFirmware 3
relative-addressing     
supports-bootinfo       
boot-syntax             00000001 

 ok
0 > **dev rom/bootrom** can't find device rom/bootrom ok
0 > **dev /rom ls** 
ff88f348: /boot-rom@fff00000
More [<space>,<cr>,q,a] ? 
Quitting
 ok
0 > **dev /rom/boot-rom .properties** 
name                    boot-rom
reg                     fff00000  00100000 
write-characteristic    flash
model                   Apple PowerBook6,5 4.8.5f0 BootROM built on 04/06/04 at 16:22:09
BootROM-version         $0004.85f0
BootROM-build-date      04/06/04 at 16:22:09
...
 ok
0 > **dir cd:,\** 

Xubuntu_PowerPC_feisty
     Size/        GMT                     File/Dir
     bytes   date     time   TYPE CRTR    Name
            1/ 1/ 4  0: 0: 0             .disk
      1026  1/15/ 7 14: 7:11  ???? ????  cdromupgrade
            1/ 1/ 4  0: 0: 0             dists
            1/ 1/ 4  0: 0: 0             doc
            1/ 1/ 4  0: 0: 0             etc
            1/ 1/ 4  0: 0: 0            *install
    126488  4/15/ 7 20:27:38  ???? ????  md5sum.txt
            1/ 1/ 4  0: 0: 0             pics
            1/ 1/ 4  0: 0: 0             pool
            1/ 1/ 4  0: 0: 0             ppc
            1/ 1/ 4  0: 0: 0             preseed
       231  4/15/ 7 20:26:50  ???? ????  README.diskdefines
 ok
0 >** dir cd:,\\** 

     Size/        GMT                     File/Dir
     bytes   date     time   TYPE CRTR    Name
       566  4/15/ 7 20:27:35  ???? ????  boot.msg
      1855  4/15/ 7 20:27:35  tbxi UNIX  ofboot.b
      2243  4/15/ 7 20:27:36  ???? ????  pegasos
            1/ 1/ 4  0: 0: 0             powerpc
            1/ 1/ 4  0: 0: 0             powerpc64
      5111  4/15/ 7 14: 3:18  ???? ????  udeb.list
    153124  3/13/ 7 15:46:54  boot UNIX  yaboot
      4626  4/15/ 7 20:27:35  conf UNIX  yaboot.conf
 ok
0 > **boot cd:,\\yaboot** load-size=25624 adler32=a5196a68 

Loading ELF


Config file read, 4626 bytes

Welcome to Xubuntu 7.04 (Feisty Fawn)!

This is an Xubuntu installation CDROM,
built on 20070415.

The default option is 'install'. For maximum
control, you can use the 'expert' option.

If the system fails to boot at all (the typical
symptom is a white screen which doesn't go away),
use 'install video=ofonly' or 'expert video=ofonly'.

Press the tab key for a list of options, or type
'help' for help.

************************************
If in doubt, just press Enter, and if that
doesn't work, type 'install video=ofonly'.
************************************
Welcome to yaboot version 1.3.13
Enter "help" to get some basic usage information
boot: 
* install                    install-powerpc            expert                   
  expert-powerpc             install-powerpc64          expert-powerpc64         
  oem                        oem-powerpc                oem-powerpc64            
  cli                        cli-powerpc                cli-expert               
  cli-expert-powerpc         cli-powerpc64              cli-expert-powerpc64     
  ltsp-server                ltsp-server-powerpc        ltsp-server-powerpc64    
  check                      check-powerpc              rescue                   
  rescue-powerpc             check-powerpc64            rescue-powerpc64         
boot: 
...

```

---

### Post by Gigidy5 on 2008-10-18
> **tiresia said:**
> What are you trying to do? Do you want to start your Mac from a Live CD?
Yes, that is what I am trying to do.
> **tiresia said:**
> Which kind of Mac do you have?
I think it is a g4. It is a tower.

---

### Post by tiresia on 2008-10-18
As you were told, what you see is just the Open Firmware prompt. And you get it because you don't have any HD

1. Download the right Live-CD iso-image for PPC (and may be read the FAQ) here:
[Where to download Ubuntu for PowerPC and other frequently asked questions]("http://ubuntuforums.org/showthread.php?t=427714")

2. It is a .iso image, so burn it at very slow speed as image 

3. Boot holding C down.

4. If you get a black screen, start the computer again and at the yaboot prompt (yaboot is the bootloader for PPC) type:
```
live-nosplash-powerpc video=ofonly
```

---

### Post by imana86 on 2008-10-18
You have an outstanding good and well structured site. I enjoyed browsing through it.  ------ Tony ([Retro Jordans](http://www.2345kicks.com)).

---

### Post by Gigidy5 on 2008-10-18
Oh, ya the easiest of things. The disc that is in there doesn't support PPC.

Ok cool thanks.


I'll try this soon.

---

### Post by ppc_guy on 2008-10-22
Sorry I didn't get back for a bit.. Do yourself and us a favor. go to [www.lowendmac.com](www.lowendmac.com) , click on profiles and find out what mac you have.. That will make things a lot easier when asking for help.

As always, your mileage may vary.

ppc_guy

-----------------------------------------------------------------------
When you are Sierra-Oscar-Lima. I'm Hotel-Tango-Hotel
-----------------------------------------------------------------------

---

### Post by n00b0.5 on 2008-11-08
I tried out different versions of Ubuntu to get it to boot from CD on a G4 mac mini (I haven't installed it yet because I'm figuring out how to do the partitioning), and the only version that actually booted correctly is 7.04, the desktop version for powerpc only, the powerpc+ps3 one does not work, neither does 7.10 for ppc. I haven't tried 8.04 and higher for ppc, but those are user modified like the 7.10, in other words not official versions.

Non-working versions just show that folder like in the first post without the text.

---

