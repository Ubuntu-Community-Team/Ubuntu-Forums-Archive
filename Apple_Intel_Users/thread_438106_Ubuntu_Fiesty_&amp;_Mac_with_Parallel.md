---
title: "Ubuntu Fiesty &amp; Mac with Parallel"
date: 2007-05-09
forum: Apple Intel Users
---

### Post by Sabon on 2007-05-09
I have a 24" Apple iMac (Intel Core2Duo) with the current version of Parallel and OS X 10.4.9.

I would like to install Ubuntu on this iMac inside of Parallels --without-- having to create and install a partition for it. I did this for Windows XP (for work - ugh) by importing XP off my other work computer.

Can I download Ubuntu and run the install inside of Parallel? Has anyone does this?

---

### Post by rockhoppr on 2007-05-09
Yes you can! 


There's one trick you need to do though...in Parallels set your system time to "Solaris" while you do the install then change it to "Linux 2.6" after. Otherwise, you'll stare at a black screen when it tries to install.

---

### Post by Chrisj303 on 2007-05-09
VMwares Fusion Beta 3 is a MUCH better soloution for a feisty virtual machine.

---

### Post by wimds on 2007-05-09
> **Chrisj303 said:**
> VMwares Fusion Beta 3 is a MUCH better soloution for a feisty virtual machine.

Indeed!

---

### Post by rockhoppr on 2007-05-09
I agree for reasons of the "linux tools" that vmware has (allowing easier mouse usage etc).

My only concern with Fusion is that it's still beta and I don't believe they've announced a price yet. I already own Parallels.

Any other reason Fusion is better for Feisty?

---

### Post by Chrisj303 on 2007-05-09
Well the fact that it's still in beta, and is already a parallels beater, a very good sign of things to come!

For me the presense of the Tools IS the deal breaker, and the fact that parallels have pretty much forgotten about the LinuxVM (windows on a Mac appears to be more profitable).

As for price, well VMware are a long established company in the world of virtualization, and are very aware of the competition - i'm certain they would not price themselves out of the game.

I will be buying Fusion the moment it comes out!

---

### Post by entangled on 2007-05-09
I have found vmware 5 works; parallels *doesn't* work for a feisty install (for me anyway).

Check out reports of vmware version 6 too. This promises to make some direct use of hardware. I hear kernel 2.6.21 has support for 'paravirtualization' which is what vmware 6 is moving towards.

---

### Post by Sabon on 2007-05-09
Thanks for all the responses. 

I will try choose Solaris and see if that works.

As for VMWare and Fusion. These look good but I'm not a professional developer and $180 or so is more than I wanted to have to spend. I may ended up doing so though.

Then end result I am looking for is to have my Mac OS X (on my iMac) with the following running in virtual machines. Windows XP (for work), OS/2, BeOS (later Haiku), and Ubuntu. Not necessarily in that order. 

Why? Because I'm an OS geek. If there was one OS I wouldn't do it would be Windows. But I need it for work so I kind of have to.

Thanks again.

---

### Post by Sabon on 2007-05-09
Question about VMWare and Fusion.

Do you need to create a partition on the Mac first or can you do an install from the download like you can with Parallel?

---

### Post by entangled on 2007-05-10
It's just like parallels' install.

---

### Post by Ian-OG on 2007-05-16
> **rockhoppr said:**
> Yes you can! 

There's one trick you need to do though...in Parallels set your system time to "Solaris" while you do the install then change it to "Linux 2.6" after. Otherwise, you'll stare at a black screen when it tries to install.

\\:D/ Cheers rockhoppr, that's been doing my head in! I got an older CD for edubuntu installed (6.10i3) no problem just by following the usual Parallels route, but that black screen was annoying me. I'm comparing the different versions, so went for the latest release for Kubuntu. Must be some of the hardware virtualisation that is enabled in Linux 2.6 support that kicks it off - I noticed that the 'Other Solaris' config list is about half the length.

Just for the record, the MS VirtualPC (which is way worse than Parallels IMHO for Linux - they seem to think I want *another* copy of Windows on - odd) gave the same error when I tried it on an old Compaq Evo N800c w XP Pro, but on that I could at least get a stage further by forcing VGA graphics on the installation, just to get to the desktop.iso start screen. There's also an error when the live system boots up, with a dialogue box on both the Mac Parallels and Windows VirtualPC - it's at that point on the MS VM that things "failed to proceed"; the Parallels version let me install using the live desktop icon. It's totally okay when booting either laptop straight from the CD without using a VM, so looks like the installation method for 7.x has trouble with VMs.

Not tried VMware though - is it just a straightforward install w/o any black screens on that platform?

---

