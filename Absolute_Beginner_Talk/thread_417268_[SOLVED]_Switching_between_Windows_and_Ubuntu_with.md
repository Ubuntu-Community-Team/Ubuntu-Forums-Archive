---
title: "[SOLVED] Switching between Windows and Ubuntu with Alt+Tab"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by the8thstar on 2007-04-21
Hello,

Is there a way to load Ubuntu AND Windows at the same time and switch between the OS with a command like Alt + Tab? All these virtualizations solutions out there look like a royal pain in the ***. Is there any simpler way?

---

### Post by Biscuitpie on 2007-04-21
Probably not, and I'd imagine your computer would move REALLY slow.

---

### Post by markl187ld on 2007-04-21
No, you'll have to go the virtualization route. It really isn't that complicated to set up and use VMWare. There is a great guide [here]("http://ubuntuforums.org/showthread.php?t=183209").

---

### Post by amo-ej1 on 2007-04-21
Well doesn't something like vmware solve your problem ? Basicly anything that offers x86 emulation 'in a window' will satisfy this need ... I have a dual head setup at home and when needed I run a windows in vmware player on one screen and ubuntu on the other screen and i find it extremely easy to work like this.

---

### Post by the8thstar on 2007-04-21
Hey guys, I have a few questions before I take the deep plunge:

1. With the virtualization solution, will I be able to use DirectX?

2. Can I update Windows and the programs running in it through Windows Update and custom program-run updates or is the system fixed forever?

3. Can I use drag-and-drop function for files and documents between Ubuntu and the virtual machine?

4. Can I use my system restore partition as a source file instead of a Windows CD, which I don't have since my install was OEM?

5. Can I install the Vista Upgrade on top of Windows XP running in a virtual machine in Ubuntu?

---

### Post by zerosystem on 2007-04-21
1. AFAIK, 3d isn't working well in VM.
2. Yes, you can update Windows and any other program you have running there. It's just like as if it were a Windows machine.
3. No.
4. I doubt you can.
5. That's not recommended, considering that it's best to install Vista on a clean slate.

---

### Post by freebird54 on 2007-04-21
Just a note here.  If you install your Win, then make an image file from that, it can be 'restored' in to the virtual session.  Only workaround I know... :)

so

1 3d no go
2. Yes
3. VM no - Virtual box not sure - Xen maybe?
4. See first note
5. Not sure - but bound to be tricky at a minimum! :)

---

### Post by Iceni on 2007-04-21
Just a note about Vista. It is _really_ slow in vmware. I run it in vmware server (latest) with vmware tools, and it is pretty much useless. WinXP is nice, tho.

Sharing have to be done via network, I belive. That means Samba. You probably want that anyway, so no biggie:)

---

### Post by the8thstar on 2007-04-21
Thanks for the feedback. I think I'll stick to dual booting with GRUB for now, until the day comes when a program that works is released. Occasionally, I'll use Wine for some programs.

To answer my own questions, here is what I can do better with dual boot than with a virtual machine:


*1.With the virtualization solution, will I be able to use DirectX?*

Yes! Native mode, full support, here we come!!!


*2. Can I update Windows and the programs running in it through Windows Update and custom program-run updates or is the system fixed forever?*
No problemo.


*3. Can I use drag-and-drop function for files and documents between Ubuntu and Windows?*

Yep, both OS recognize each other with their contents too in EXT3 and NTFS.


*4. Can I use my system restore partition as a source file instead of a Windows CD, which I don't have since my install was OEM?*

N/A

*5. Can I install the Vista Upgrade on top of Windows XP?*

Yes, although I'm afraid it's going to slow down programs running in Windows and will wack the hell out of GRUB during the install process.

---

### Post by Eclipse. on 2007-04-21
You could use Parallels Workstation it would run alot faster than vmware.Its not free but I do have some links for it.

Its proabley against the rules to post warez so PM me.If you want it.;)

---

### Post by the8thstar on 2007-04-21
What about qemu with the new kernel? Has anyone tried this solution?

What about an hypervisor program?

---

### Post by mdknaebel on 2007-04-21
can you run it from windows and have ubuntu virtually?

---

### Post by freebird54 on 2007-04-21
The things I have tried have been slower that way around - but you never know.  Anyone tried any of those solutions (besides the MS Freebie and VMPlayer?)

---

