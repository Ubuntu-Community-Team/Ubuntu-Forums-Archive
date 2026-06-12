---
title: "EFI boot issues on MacBook 3,1"
date: 2012-01-17
forum: Any Other OS
---

### Post by goodgestreet on 2012-01-17
Hello all,


I am a writer who is impressed with the longevity (believe it) of my MacBook 3,1.   I recently gave up on OS X however and run Linux Mint 12 (64 Bit Gnome) to great pleasure. . .something like euphoric.  I am annoyed at the classic EFI boot delay, and am interested in any advice on the cause and solution.  I am still a noob at computers after all these years, and am a bit intimidated by Terminal despite recognizing the elegance of it.

In case you are wondering, I have tried booting from my OS X install disc and entering this:

```
sudo bless --device /dev/disc0s2 --setBoot --legacy --verbose
```I have tried blessing the two partitions where the GRUB and the Linux Basic Data are, to no effect.  

If there is any software that can alleviate my wows in one install, I am happy to hear any suggestions!  I am limited to open-source due to being broke (writer). 

This may be of use:

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             34         1987  GRUB2 BIOS Boot
 2           1988    310552769  Basic Data
 3      310552770    312581758  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1           33  ee  EFI Protective
 2             34         1987  ef  EFI System (FAT)
 3 *         1988    310552769  83  Linux
 4      310552770    312581758  82  Linux swap / Solaris

MBR contents:
 Boot Code: GRUB

Partition at LBA 34:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 1, type GRUB2 BIOS Boot
 Listed in MBR as partition 2, type ef  EFI System (FAT)

Partition at LBA 1988:
 Boot Code: None
 File System: ext4
 Listed in GPT as partition 2, type Basic Data
 Listed in MBR as partition 3, type 83  Linux, active

Partition at LBA 310552770:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 3, type Linux Swap
 Listed in MBR as partition 4, type 82  Linux swap / Solaris


Is this a sync issue, or a name issue?  Seems something is wrong from the report that OS X gave me, but Linux Mint runs great despite the 10-30 second delay.  I want to ensure that I can boot up with a USB drive I keep Mac OS X Snow Leopard on, and install EFI Firmware updates (something I read is necessary on an Ubuntu wiki).   At the same time, I want to keep may disk capable of reliable Linux booting.  Is there a way to completely "Linux-ify" my Mac?  To reliably boot quickly from an EFI based computer?
   
Apart from this, find Linux on a Mac to be as fresh as when I first got steady with Mac OS.  

Cheers,

gs

---

### Post by Perfect Storm on 2012-01-17
Moved to Other OS/Distro Talk.

---

### Post by Double.J on 2012-01-17
Hi there - I can't attest to the macbook, but I use rEFIt to handle the booting... may be worth a look? home page [here.]("http://refit.sourceforge.net/")

Here's hoping your macbook keeps going for much longer! My old emac is still ticking away niceley 8 years on.. Even if it got left behind at leopard!

---

### Post by goodgestreet on 2012-01-18
Sorry for my lack of knowledge, but how could I use refit as a bootloader without having Mac OS on my machine?

---

### Post by Double.J on 2012-01-18
Hi there, Sorry I thought you were referring to a dual boot set up - my bad!

have you come across this thread that may be of use?

[Veiho's how to]("http://ubuntuforums.org/showpost.php?p=5166788&postcount=21")

Hope it's useful :)

---

### Post by goodgestreet on 2012-01-18
Ahh.  I see that I should make a bootable refit CD, and THEN try the terminal command from the Mac OS disc.  Can I make the refit CD in Linux?

---

### Post by Double.J on 2012-01-18
Hi there!

It should just be a case of downloading the cd image from the [rEFIt site]("http://refit.sourceforge.net/") (select the "6.5M ISO disk image") and burn the image with brasero in ubuntu.

Best of luck :)

---

### Post by goodgestreet on 2012-01-19
Well, I got a bootable refit CD, and started up the machine holding down ALT.  Went to the partition tool in refit and the sync tool gave me this:

Analysis inconclusive, will not touch this disk.

Even to my untrained eye, it was obvious that the GUID and MBR do not match because the EFI partition is listed twice on one and once on the other.  I am guessing that this is why my previous attempts to bless Linux from my Mac OS install disk did not work.  

I am wondering, is it okay to run Linux like this?  There is a delay on startup that is annoying, but otherwise Linux runs amazing on the MacBook.  I have no desire to go back to Crap-Os.

Cheers,

C.

---

