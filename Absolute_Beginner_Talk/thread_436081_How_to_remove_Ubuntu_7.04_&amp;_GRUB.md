---
title: "How to remove Ubuntu 7.04 &amp; GRUB?"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by SamTyson92 on 2007-05-07
Ubuntu 7.04 has had a error and I need to remove it and GRUB now I have a Windows XP Disc and I need a boot disc are these the same thing and how do I boot it up and it says I need to type
# fixmbr
# exit
is this in cmd.exe of the boot disc?
Please help ASAP

Its a CD not a floppy as I dont have a floppy drive.

---

### Post by billdotson on 2007-05-07
Boot from that Windows CD.  Go to the recovery console and type fixmbr.  Go into the BIOS and change the boot device order so that the CD/DVD drive boots first.  I do not know if you have the actual Windows XP install CD or you have on of those recovery discs that OEM PCs ship with, so it might be different on an OEM restore disc.  I guess that should do what you want.. but I have never actually had to do that so I could be wrong.. although it seems to be a common practice if you screw somethin up.

---

### Post by benfindlay on 2007-05-07
boot off the windows disc and when prompted choose the repair console. When you are in there you will be prompted to log into windows (if it is installed). Then you just type fixmbrand it will re-write the mbr for you. Exit will reboot the computer so remove the cd once you type exit. Then, back in windows(if it is installed) you can right click on My Computer and choose manage. In Disc Manager in there you can sort out the partitioned space so that it is usable in windows again! If you're not using windows, a fresh install of ubuntu, or whatever OS you want to use is on the cards now!

Hope this helps!

---

### Post by SamTyson92 on 2007-05-07
> **billdotson said:**
> don't quote me for truth but I am assuming that you go to the recovery console and type fixmbr.. be warned I **could be wrong** though.  Let me research a bit.

Yes thats correct however Ive never done it before so I need a step by step guide do I remove ubuntu partions first then put the Windows XP Disc in and press F12 like live cds and run it then what?

---

### Post by fakie_flip on 2007-05-07
To remove Ubuntu, you need to format the partition it is on. Then you will have some free space not being used. You can create a new partition there for Windows to use, but it needs to be fat32 or ntfs.

---

### Post by brander on 2007-05-07
I removed it by simply using fdisk from Windows98 boot disk but you need to do two things:

First remove the partition altogether with fdisk.exe or your favourite partition tool(partition magic, paragon, PQDI) .

Then to remove grub, just type this at the command prompt:

fdisk /mbr

Worked for me.

---

### Post by fakie_flip on 2007-05-11
Why did you want to get rid of Ubuntu?

---

### Post by BibbopMania on 2007-06-03
can someone please explain my how to remove it because after i use my recovery dvd i recive a grub error 22 what to do ???

---

### Post by bwallum on 2007-07-16
> **fakie_flip said:**
> Why did you want to get rid of Ubuntu?

Because it takes far too long to get a system running that can be called a productive and fun system to work with. Every time I have come up against a limitation I get the advice to try this and that. I then spend hours recovering when it doesn't work. Ubuntu is for the Linux techies who just love fiddling about. I just want things to work.  I have been trying to get something useful and comprehensive working for a while now. My acid test is would you give it to an eighty year old. Maybe some are out there that can handle it but Windows is a much safer bet if you want to actually use the computer to do something other than computing for computing's sake.

...and I hate Windows! Microsoft are now allowing corporate ("partners") to install rootkits that control my computer. That used to be the preserve of malicious criminals! We all need an open controllable system but Linux has a long way to go before it gets easy to use.

---

### Post by fenixphire07 on 2007-11-19
Unfortunately I too have to agree on this. But it is not the fault of Ubuntu, Linux or anything else. The problem is that all software and hardware manufacturers are ignoring the FOSS Community and so that is why these OS's do not catch on. 

But imagine, an 80 year old who was born and bred on Ubuntu (ubuntu aint that old, but just imagine), would find Windows much more restricting.

Ubuntu can become a lot more user friendly like windows, but at the cost of giving users less control over their work and computer usage. 

Just a thought for you, why not try something like VMWare. There is a HOW-TO in the Tips and Tutorials category. It seems to be the solution to the Windows noose around our necks. (Not tried it out yet, but hopeful)

---

### Post by hyper_ch on 2007-11-19
I tend to think if you have a computer noob (someone who's never used a computer before) and present him a fully linux compatible system and a windows install cd and ubuntu install cd that this person would think ubuntu more intuitive and usable...

---

