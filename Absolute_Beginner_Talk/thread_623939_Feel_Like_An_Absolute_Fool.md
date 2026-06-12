---
title: "Feel Like An Absolute Fool"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by tlcmd on 2007-11-26
Y'all,
  I feel like an absolute fool since I cannot install Ubuntu. Help, please!!!
Given a computer with:
1) 550MHz Pentium III
2) 18.6 Gig hard drive
3) Completly re-formated hard drive. Other than BIOS, there is nothing else there.


The computer does not recognize my cd-rom  as a bootable file from the CD-ROM drive.

it is a 700 MB CD-ROM with ubuntu-7.10-desktop-i386 burned as an Easy Creator Image File 712,508 KB

What did I do wrong? How do I fix it?

Thanks,
tlcmd

---

### Post by FuturePilot on 2007-11-26
Is your BIOS set to boot from the CDROM first?

---

### Post by erfahren on 2007-11-26
you may have gotten a bad burn, for best results it needs to be burned at the lowest speed possible.

Your computer specs might not be enough for Ubuntu anyway. There are distros available that work better on older computers (Xubuntu or PuppyLinux to name a couple).

Have you tried booting from that CD on another computer.

---

### Post by umattu on 2007-11-26
Well first lets look at the obvious:

   Is the CD-Rom set to boot in the BIOS?

When you burned the iso, did it burn the iso file to the disc or did it burn the image, put the cd in a working machine. Open the cd and if you see the .iso file, then the disc was not burned properly. 

Check it out and post back.

---

### Post by dasunst3r on 2007-11-26
In Windows, pop in your CD and browse it.  If you see only one file, you've burnt the CD incorrectly.  Otherwise, I would agree that you should have a look at your BIOS settings.  Rest assured that I've seen Xubuntu work on a P3-550 system perfectly fine (not too fast, but it works pretty nicely).

---

### Post by philinux on 2007-11-26
Once you've checked the bios boot order, ie cdrom first.

How much ram is in the pc.

---

### Post by jimmj43 on 2007-11-26
I'm faced with a similar roadblock on an even older machine: 1GHD, 64M RAM & 100MHz Pentium. I'm learning the older machines, as well as 'clean' HDs, won't recognize the Linux software. It seems a boot floppy has to be created to enable the older, Windows-hobbled machines to 'see' & communicate with the install disk. Which, not entirely by coincidence, leads to my question: Howinhell does one go about making a floppy using Fiesty?

Step-by-step and in English please. Here types an old fart noob.

---

### Post by tlcmd on 2007-11-27
Thanks to all.
256 of RAM. My BIOS were set properly, but I had burned the iso. Reburned Ubuntu  it installed....partly (several times and froze at different places, just like Windows). . The further I get into this, the more I think i've got hard drive failure. Locked up on the "memory check" also. Will reformat hard drive, clean computer and try once more. Then very probably junk it and wait for someone in the family toreplace their old one and give it to me to play with. My youngest son is in college, and has some "guru" friends. Maybe one of them can find an old hard drive to drop into this thing. 

Thanks again.
tlcmd

---

### Post by philinux on 2007-11-27
when you get back to the live cd pick the option to check out the live cd, just to make sure it burned well.

256mb should be enough.

---

### Post by gn2 on 2007-11-27
If it's 7.10 you need 384mb RAM to run the desktop CD, which is an increase from earlier versions which required 256mb.

All is not lost, at the splash screen, press F6 and type "only-ubiquity" (without the quotes) and that should just run the installer.

[http://www.ubuntu.com/getubuntu/releasenotes/710](http://www.ubuntu.com/getubuntu/releasenotes/710)

If that doesn't work, download the Xubuntu 7.04 Alternate CD, it's more likely to give you an easier time.

---

### Post by oldos2er on 2007-11-27
> **jimmj43 said:**
> I'm faced with a similar roadblock on an even older machine: 1GHD, 64M RAM & 100MHz Pentium. I'm learning the older machines, as well as 'clean' HDs, won't recognize the Linux software. It seems a boot floppy has to be created to enable the older, Windows-hobbled machines to 'see' & communicate with the install disk. Which, not entirely by coincidence, leads to my question: Howinhell does one go about making a floppy using Fiesty? 

 Your system specs are way too low to run the *buntus.

---

### Post by tlcmd on 2007-11-27
I did run the "live CD check" and it was ok. I'm now in the middle of "memory check" just to see if I can figure out what's wrong with this *&^%^&* computer. 
Again,
Thanks,
tlcmd

---

