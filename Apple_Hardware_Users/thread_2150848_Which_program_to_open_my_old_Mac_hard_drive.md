---
title: "Which program to open my old Mac hard drive?"
date: 2013-06-02
forum: Apple Hardware Users
---

### Post by TNFrank on 2013-06-02
I have the hard drive out of my dead iMac and I'd like to get an enclosure for it so I can hook it up to the 2.0 USB and get some files off of it. I installed VirtualBox but it's saying that I need to insert the Op System CD to run the Op System(OS X 10.3) and since there's 3 disks that's just not a practical way to go about it.
 Is there a program I can install under Ubuntu 12.04 that'd let me download the files to my desktop so that I can save them? Thanks in advance.

---

### Post by ajgreeny on 2013-06-02
I think you need to install the package **hfsplus** (and maybe other packages in the hfs* family) in order to be able to mount and read a mac formatted system disk.

---

### Post by rkmugen on 2013-06-02
You don't mention what architecture your new host system is... but for just accessing stuff from your old hard drive, I believe hfsplus should work fine.

As a side-project/experiment though (if you have extra time), you could consider installing QEMU on Ubuntu, which emulates PPC hardware (to some degree).  Afterwords, you can attempt to install OSX 10.3.x on top of that... granted, I don't know if this would work for a System-specific OSX installation disk.  I'd imagine that you'd probably get less of a headache if you had the full-retail version of OSX instead of, let's say, an OS restore disk that's designed specifically for an iMac G3/G4, a Mac Mini G4, an eMac, or a Power Mac G3 or G4.

---

### Post by tgalati4 on 2013-06-02
You will only be able to read from HFS+ drives.  To be able to write to them from linux, you need to turn Journaling off (going from HFS+ to HFS) and this (as far as I know) can only be safely done using OS X's Disk Utility and unchecking Journaling.  There is also a command-line utility for use with iTerm on the Mac that will do the same thing.  Once Journaling is turned of on the drive, linux should be able to read and write to the drive.

tgalati4@Mint14-Extensa ~ $ apt-cache search hfs

.
.
.
hfsplus - Tools to access HFS+ formatted volumes
hfsutils - Tools for reading and writing Macintosh volumes
dmg2img - Tool for converting compress dmg files to hfsplus images
hfsprogs - mkfs and fsck for HFS and HFS+ file systems
hfsutils-tcltk - Tcl/Tk interfaces for reading and writing Macintosh volumes

---

### Post by TNFrank on 2013-06-03
The iMac is dead, the hard drive is out of the machine and will get an enclosurs soon as funds allow.  My new 'puter is a HP nc8230 w/ 1.86GHz processor, 2GB RAM, 60GB hard drive and I'm running Ubuntu 12.04.2 on it. 
 I think somehow I can boot to the old hard drive using VirtualBox maybe since the OS is still on the hard drive and VBox can use that as it's virtual OS but I'd just like to get my ducks in a row before I do anything so things will go smoothly. 
Mainly just want to pull stuff off of the old drive and save it in my new system, not looking to write to it right now. Eventually when everything I want is off of it I'll format it and use it for extra storage space or I might put a different OS on it to boot to from USB so it'll be like having to different computers.

---

### Post by Lars Noodén on 2013-06-03
You cannot boot PPC systems with VirtualBox, it is limited to the i386 and AMD64 architectures which still plague us today.  You might have better luck with Qemu, which can act as [PPC](https://en.wikipedia.org/wiki/QEMU#PowerPC).

---

### Post by TNFrank on 2013-06-03
So there's no way in VirtualBox to make my computer think it's a Mac so I can get into the hard drive and recorver files? I'm running an Intel i386 processor in my laptop, Intel Pentium "M" Centrino so I CAN use VB to emulate a Mac for the purpose of data recovery from the old Mac hard drive, Right?

---

### Post by rkmugen on 2013-06-03
> **TNFrank said:**
> So there's no way in VirtualBox to make my computer think it's a Mac so I can get into the hard drive and recorver files? I'm running an Intel i386 processor in my laptop, Intel Pentium "M" Centrino so I CAN use VB to emulate a Mac for the purpose of data recovery from the old Mac hard drive, Right?

Though VirtualBox can theoretically emulate the INTEL version of OSX (i've never tried it, nor have I did any research to see if anyone else was able to pull it off), I'll reiterate that _**VirtualBox will NOT emulate a PPC machine and CANNOT boot/emulate the PPC version of OSX.**_

To be clear, your only options (to my best knowledge) are:[INDENT]*hfsplus (to attempt to access the files on the hard drive... just access/copy/download/transfer... not run)
*qemu (to attempt to emulate the PPC version of OSX.... provided your Pentium M/Centrino is really capable and up to the task)[/INDENT]

There may actually be a third option... though I doubt you'd want to get another PPC machine.
[INDENT]*You could buy a used PPC iMac G3 for under $50 on eBay or even Craigslist (if you live in the USA).  Or perhaps find one for free locally (garage sales) and use it to boot your hard drive.  Heh... then after you've salvaged your files, slap Linux on it! lol.
[/INDENT]

---

### Post by Lars Noodén on 2013-06-03
> **TNFrank said:**
> So there's no way in VirtualBox to make my computer think it's a Mac so I can get into the hard drive and recorver files? I'm running an Intel i386 processor in my laptop, Intel Pentium "M" Centrino so I CAN use VB to emulate a Mac for the purpose of data recovery from the old Mac hard drive, Right?

If you can add the hard drive to an existing Linux machine, you can access it read only as HFS.  You'll need to add the package hfsplus and maybe also hfsprogs and hfsutils.

---

### Post by TNFrank on 2013-06-03
Why is it then that VirtualBox lists an option for "Mac OS X" under OS types?

---

### Post by Lars Noodén on 2013-06-03
I'm not up on the names of the old models, but the old iMacs use the superior powerpc architecture instead of the archaic x86.  OS X 10.3 was powerpc.  With that, you might be able to use Qemu, but I'm not sure it will be mac-like enough to fool the install DVD.  Was it iMac G3 or iMac G4, that will tell.  However, the file system is independent of hardware architecture and should be readable on any Ubuntu system with the help of the package hfsplus.

The new Macs all run x86.  You can see it in the power adapters for the notebooks, they about doubled in size and weight when they made the transition.  I don't know the politics behind the change, but it was not a technical consideration IMHO.  

I have VirtualBox but hadn't noticed the OS X option before.  I'll have to try that.

---

### Post by rkmugen on 2013-06-03
> **TNFrank said:**
> Why is it then that VirtualBox lists an option for "Mac OS X" under OS types?

It can only use the INTEL version of OSX... not the PowerPC version of OSX.  I'm not going to insult your intelligence, and forgive me if this comes across as offensive (I don't think it is), but I honestly don't know how else to make it less ambiguous.

To be fair, it would've been helpful if the authors/developers of VirtualBox made the distinction more clear in that list of options.  I suppose that sometimes programmers have in their mindset that they're programing solely for other programmers...

---

### Post by TNFrank on 2013-06-03
My iMac had the older G3, 800MHz processor in it.  I'm not trying to start an argument with ya'll but isn't the entire point of a software emulator(i.e. VirtualBox, et al) to allow software from an operating system run on hardware that it's not suppose to be able to run on?
 To tell you the truth I've been out of the "Tech Game" for quite a while because my ol' iMac didn't need much coaxing in order to run properly so I got lazy but since it died I've been watching everything I can on Revision3, C/Net and other tech shows on my Roku2 XD.  I've picked up a lot over the last couple three weeks but I know that I don't know it all,LOL.
 I basically just want to pull off my .jpg and .mpg/.mov files from my hard drive. There pics and movies of my kids and grandkids and I'd hate to lose them.

---

### Post by Lars Noodén on 2013-06-03
Mac used to have superior hardware to Wintel.  The G3 is [powerpc](https://en.wikipedia.org/wiki/Powerpc) which Qemu can do and Virtualbox can't.  PPC is superior in many ways to x86.  Compare and contrast the PPC to [ARM](https://en.wikipedia.org/wiki/ARM_architecture) , [MIPS](https://en.wikipedia.org/wiki/MIPS_architecture) and [Sparc](https://en.wikipedia.org/wiki/Sparc).  VirtualBox can't do those either.  Each is much better than x86 in certain ways.  What x86 has is basically volume discount, the others specialize in some areas of superior performance.  

If you just want the files, the fastest way is to add HFS support to your Linux system and then grab them from the disk. Linux reads HFS just fine once the package hfsplus has been added.  

The very next thing you should do after recovering the files is to make backup copies.  If you don't have a spare USB disk handy at the moment, get one when you go out shopping.  They are inexpensive and can save your bacon.

---

### Post by tgalati4 on 2013-06-03
Apple had heat problems trying to make a thin laptop with a G5 processor.  IBM (the sole maker of the PPC chips--G4 and G5 at the time) was making a healthy profit and Apple wanted cheaper chips and Intel was willing to make low-power, thin-form-factor chips that allowed the Macbook Air and they got a price break on higher-performance chips for the MacBook Pro's.  I agree, the old G4 chips at 1 GHz seemed to perform as well as a 2 GHz Pentium 4.  

It's good to remember the politics.  Apple threw all the ppc users under the bus in pursuit of profit.  They did it before in the late 80's when they went from the 6500 series chips to Motorola 68000 series. And then again when they dropped Motorola for the PPC series by IBM.  Users couldn't upgrade because the OS wouldn't run on the new architecture.

It's interesting that some form of linux runs on all of those architectures.

---

### Post by TNFrank on 2013-06-03
I recently picked up a 32GB USB at Office Max on sale. Got it for just shy of $20 bucks out the door, can't beat that deal.  Back in '05 when I took my CAD/Detailed Drafting course I needed something to store drawing files on and got a 256MB USB and it was a whopping $30 bucks. Now I don't even think they make em' that small anymore,LOL.
I'll have to do a sudo apt-get install hfsplus when I get ready to read the old hard drive so I can pull files off of it. Anyway, thanks for all the info and help. Talk to ya'll later.

---

### Post by TNFrank on 2013-06-08
So, has anyone come up with a good idea as to how I can get my files off of the old Mac hard drive once I get an enclosure for it?

---

### Post by Lars Noodén on 2013-06-09
The answers given above are what you should try.  Start with adding HFS support to your linux system and then mounting the hard drives that way.

---

