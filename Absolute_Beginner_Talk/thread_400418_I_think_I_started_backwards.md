---
title: "I think I started backwards"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by Netspeed on 2007-04-03
On a new system with no OS, I installed Ubuntu and I love it...almost. I run a business that needs all kinds of .Net and Windows programs. I've tried Wine and now have XP running through Virtualbox (way easy) but some things are problematic with that. I have a USB headphone/telephone system that works flawlessly in XP but has trouble in VirtualBox and I don't have the time to figure it out. I mainly want to use Ubuntu for the internet, Evolution, and OpenOffice....basically all communications with clients. There's no important data on the computer yet so losing it all is no big deal.

Is there anyway I can install XP as the main OS and then run Ubuntu through VirtualBox without having to format the drive? I'd also love to hear from business owners that use Ubuntu exclusively. 

Thanks for any and all help/advice!

---

### Post by thefoolisme on 2007-04-03
I do believe Windows needs to be installed first.  If not, it will write over Grub, and take over the MBR.

---

### Post by Murxidon on 2007-04-03
I don't think that's possible, I suggest you install XP as the main os (formatting the drive) and either running Ubuntu on a seperate partition or through VMware.

Or, you could work out the problem you were having with VirtualBox...

---

### Post by Netspeed on 2007-04-03
> **Murxidon said:**
> I don't think that's possible, I suggest you install XP as the main os (formatting the drive) and either running Ubuntu on a seperate partition or through VMware.

Or, you could work out the problem you were having with VirtualBox...

It always seems as though it's one problem or another which is why I want to have XP as the main OS. USB? Plug it in and away you go unlike VitualBox which had me go through lines of code to change one from 664 to 666. Then I thought, what else will pop up that will have me digging for a solution?

---

### Post by jhenager on 2007-04-03
Yeah, at least you can lose your existing install with not much pain. I'd go ahead and divide the hard disk in two with GParted or other partitioning utility, and then install XP on one partition. Then reinstall Edgy on the other. Grub should pick up both OSes.

---

### Post by Raptor45 on 2007-04-03
Using Linux inside a VM, except for testing purposes, seems to defeat the purpose to me. If you're going to boot into Windows, just use windows and download FF/OOO/etc. If you don't want to use Windows, fix your problems with VirtualBox and stick to Linux.

If you're going to use windows as the host OS, theres not much of a point in using Linux inside the VM except for making new issues for yourself. If you have a windows host, you are already going to have to deal with all the virus problems and other windows issues, so there's little point to linux other than for kicks.

IMO anyway.

EDIT: And dual booting can be annoying if you just want to switch between programs. Having to restart the computer to just do one thing can burn a lot of time.

---

### Post by zvacet on 2007-04-03
Why don´t you try to solve problem with USB?Research forum and Ubuntu documentation or give specific to the forum and I belive somebody will help you.But this is just a option.It´s ip to you what to do.

---

