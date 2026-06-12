---
title: "G3 Tower, 3 different downloads, HELP!"
date: 2007-02-02
forum: Apple PPC Users
---

### Post by dsqmoore on 2007-02-02
Hello world. That is what I would like my Mac G3 Tower (blue, 768 MB ram, dvd drive, ATI Rage 128 MB Video) to say. I have tried a bunch of the scripts/ commands scattered through the forums, yet still after getting the cd to load, trying "startx", and another longer command line (sorry have not been taking accurate notes, starting now I am). I have not had success as of yet, and am wondering if there needs to be an IDE drive in the box to at least get the live cd to fully load? Is there SATA PCI card support? 

I have tried Ubuntu Server 6.10 (need server version, file server that will have 1TB+ after completion and 2xGB Nics), desktop 6.10, and about to burn the "xubuntu-6.06.1-alternate-powerpc.iso" at 4x speed to see if this helps (this also did not work). I am new to PowerPc Linux installs, any pointers, URL's with load/ boot commands would be much appreciated. :guitar:

---

### Post by bodycoach2 on 2007-02-04
Is your Mac G3 the Yosemite style, like this:

[http://lowendmac.com/ppc/g3c.shtml]("http://lowendmac.com/ppc/g3c.shtml")

---

### Post by dsqmoore on 2007-02-04
It actually looks like this. [Mac G3 Tower (BLUE)]("http://www.everymac.com/systems/apple/powermac_g3/stats/powermac_g3_400_bl.html") Basically, editing a config file trying to boot from a CD does not seem right to me. Right now, I have removed the BIOS battery, put it back in place, I have a DVD rom drive on IDE 0:0, and a Sonnet PCI SATA card with 2 ports. I have 1 new 300 GB WD SATA drive. When you boot from the CD, it seems to want another IDE interface? Is SATA supported? Or do I need to install osx 10.4, then run this CD?

---

### Post by dsqmoore on 2007-02-05
Can anyone walk me through installing on a Mac G3? Payment is available. I need to get this up and running tonight@!

---

### Post by grazie on 2007-02-05
I don't know, but it's unlikely your machine will support that massive 300G HD (and SATA is doubtful), without modification in some way, if at all. However, it should still be able to boot your Live CD without a HD. If not, can you describe what you are doing and what's happening.

---

### Post by bodycoach2 on 2007-02-06
I have to agree. I don't think SATA is supported. I'm willing to bet that if you stick an IDE harddrive in the machine, you'll load up just fine. Put that 300G HD in an external case, and connect it with firewire or USB. 

In the long run, you want to keep only your OS and programs on the primary harddrive, and most of your personal files on something external. You can even use offline containment, like XDrive.com or mediamax.com

An 80G HD is all you really need. Get a fast one, and use that.

---

### Post by samden on 2007-02-07
> **dsqmoore said:**
> Can anyone walk me through installing on a Mac G3? Payment is available. I need to get this up and running tonight@!
How does the paid support from Canonical work? Have you looked into that?

---

### Post by phersotty on 2007-02-07
> **samden said:**
> How does the paid support from Canonical work? Have you looked into that?

I don't mean to deter you from Ubuntu, but have you tried any other PPC distros to see if they will boot up?  I have Yellow Dog running on my old G3 and works fairly well.

---

