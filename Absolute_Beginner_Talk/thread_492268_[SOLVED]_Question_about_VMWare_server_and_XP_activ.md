---
title: "[SOLVED] Question about VMWare server and XP activation"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by aldonova65 on 2007-07-04
I currently dual boot my PC between Feisty and XP. I want to stop having to boot back and forth and get XP running in a virtual machine. A week or two ago, I spent some time and configured VMWare Server to boot my physical XP installation. It actually worked fairly well with the exception of requiring me to re-activate my XP installation. I ran this way for about 2 days but just didn't have time to verify everything in XP would work the way I needed it to as a VM so I booted back to my physical XP partition and re-activated before time ran out so I would be able to continue dual booting.

What I'd like to do now is use VMWare's converter software and boot XP as a virtual disk inside VMWare Server in Ubuntu. I fully expect the virtual XP to want me to re-activate. However, does anyone know if my physical XP installation will then require activation as well? That would assume the the virtual XP is sending information back to Microsoft on boot up that the physical hardware changed. If it doesn't send any information, then I would think that my physical XP would continue to function correctly. I could make a backup of my virtual XP and test as long as I wanted until I felt comfortable enough to activate the virtual installation and wipe the physical partition.

Thoughts?

---

### Post by kyphi on 2007-07-05
Dual booting gets to be a bit of a chore if you have to do it often.

Like you, I have a dual boot system with my operating systems on separate drives.  I use VirtualBox and have XP installed as a guest on Ubuntu for just one programme.  Any other windows-based programme I have working via CrossOver.

XP on the hard drive only gets used for my infrequently used scanner and for playing games such as Oblivion, etc.  The XP installation is not connected to the internet so does not require anti-spyware, anti-virus nor a firewall.  Yes, it required activation originally.

XP on Virtual Box also required activation.  While there was no problem with that, if I had copied the activation file (Windows\System32\wpa.dbl) from the hard drive and installed it to the VirtualBox installation of XP that may have worked too.  The Windows copy is still on the same physical machine.

You can also mount your XP installation in Ubuntu so that you can access the XP files.

It is a pity that Microsoft insists on playing it alone.  Some of their programmes are not that bad even if they are dreadfully expensive.

Cheers

---

### Post by aldonova65 on 2007-07-06
Thanks for the reply. So far, I've found 3 programs I haven't been able to get working using WINE and I have to have them working (Well, I have to have 2 of the 3) so being able to run XP somehow is going to be a necessity for a while. 

I've got read and write access to my XP partition so that's not a problem. I'm just still trying to figure out how to get some things done running XP as a virtual machine. Once I'm confident everything is working as I need it to, I'll activate the VM version of XP and vaporize my physical XP partition. 

Anyway, I threw caution to the wind and decided to answer my own question by just going for it. I'm happy to report that although the VM version of XP is wanting me to validate (and only seems to want to give me 3 days, not the 30 I've seen reported elsewhere), it has not affected my physical installation of XP. Therefore, I should be able to restore my virtual XP system from a saved copy as many times as I need to until I figure out how to configure it properly. I'm still having some issues with sound and also figuring out how to let it see my USB drive and USB digital voice recorder (that's one of the must haves). However, if I can't figure out on my own, I'll post a new thread asking for help.

I suppose I could also try the same thing with Virtual Box if I just can't get VMWare to do what I want it to do.

---

