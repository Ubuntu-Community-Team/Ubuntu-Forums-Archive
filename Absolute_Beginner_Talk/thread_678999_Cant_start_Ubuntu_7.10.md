---
title: "Cant start Ubuntu 7.10"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by quqdk on 2008-01-26
Hi everyone,

I downloaded Ubuntu 7.10 a few days ago. 
However my cd-drive didnt work propper, so I installed the OS, on my Harddrive, on my dads computer, and moved it to my own computer afterwards.

Now I get some strange error (which I have searched the forums for, without luck), telling me that  "/dev/sda1 was not clearly unmounted, check forced" and on the next line theres a statusbar "|==== xx,x%"
when the check reaches 100%, I get this error: "fsek died with status 3" and that the system will be rebooted in 5 sec.
When the ram is beeing counted, and master/slaves are found, I get the message pres Esc to enter Menu (2 sec). If I do so, I can choose Ubuntu 7.10 kernel 2.6.22-14-generic, and same (recovery mode). besides I can choose the memtest86+. 

the recovery mode takes me samewhere as mentioned above, and the normal mode gives me the monitor message "not supported", as in the monitor isnt supported by the system (?)... (its not "no signal", just "not supported" :D)..

Can anyone help me here:
- to get the monitor working with ubuntu
- to get the boot sequence working, and letting me get into ubuntu :D


Cheers, 
quqdk (if there are spelling errors... so be it :D)

---

### Post by dstew on 2008-01-26
> However my cd-drive didnt work propper, so I installed the OS, on my Harddrive, on my dads computer, and moved it to my own computer afterwards.How did you do this?

---

### Post by quqdk on 2008-01-26
I fysically moved my HD1 from my own computer to my dads computer. Disabled all other HD-Drives, and installed Ubuntu. Afterward I tested it, and it worked perfectly :D
When I had shut down the system, I fysically moved the HD-Drive back to my own computer, and then started it up.. which resulted in all the mentioned...

---

### Post by quqdk on 2008-01-26
anyone who knows, what I can do?

---

### Post by dstew on 2008-01-26
You cannot install an Ubuntu system that way. Your two computers would have to be identical to have any hope of that working (same motherboard, same motherboard version, same chipset, same bios, same bios version etc.)

My suggestion: get your CD drive to work, and install using the Alternate Install CD.

Note: It is possible to clone an Ubuntu system, but you need to use a special program like [clonezilla]("http://clonezilla.sourceforge.net/"). Just moving the hard disk is bound to fail.

---

### Post by shad0w_walker on 2008-01-26
Sorry to the above but you are wrong wrong wrong. I have done this myself many times. Even did it on my media centre which works perfectly. Ubuntu and most linux distros detect hardware at boot and load the appropriate modules.

---

### Post by quqdk on 2008-01-26
yah.. I agree with shadow_walker.. I have done it a couple of times with both windows and OSX, without having errors... so I's say it should be possible with ubuntu aswell..

---

### Post by dstew on 2008-01-26
Well, I am surprised! And I stand corrected. But, doesn't moving a system like that at least carry with it the chance that it might not work?

---

### Post by shad0w_walker on 2008-01-26
The odds are very slim. The way it is setup tends not to rely upon specific hardware configurations. The biggest issue you encounter with these moves is specific drivers and their cards changing. For example ATI to Nvidia changes or 64bit installed then moved to a 32bit processor.  But if you stick to generic drivers (Vesa, 32bit kernel, etc) then you should be pretty safe.

---

### Post by JohnnyBoy022 on 2008-01-26
I have Ubuntu installed on an external hard drive and I can move it from system to system. It boots fine but the only reason it doesn't work is that compiz tries to run and I dont have the drivers installed for the graphics card on other systems.

As for your problem, that error message for me at least happens when I don't shut down my Windows partition properly, for example if I just shut off the power to the computer then I can't mount it. To fix it I just boot into windows and shut down properly.

---

### Post by quqdk on 2008-01-26
Well... theoreticaly there could occure some minor problems with drivers. 
However, when using common hardware, there should be a very big chance that the operating system has the drivers included in the drivers folder.
Therefor, after booting the first time, on a new system, the drivers are all loaded, which takes some minutes (depending on your systems speed), and afterwards it should be able to run at normal speed the next times, the system is powered on.

---

### Post by quqdk on 2008-01-26
> **JohnnyBoy022 said:**
> As for your problem, that error message for me at least happens when I don't shut down my Windows partition properly, for example if I just shut off the power to the computer then I can't mount it. To fix it I just boot into windows and shut down properly.
I wish I had a windows partition.. heh. However I only have this partition (119gb ext2 + 1gb swap), so I dont know how to correctly unmount the drives... 
I have tried to enter Unbuntu via the live CD, and manually unmount the harddrives, and then reboot... but apparently it wont change anything..

---

### Post by quqdk on 2008-01-26
Right now, I think my main problem, is to power up my computer, with monitor support.. (afterwards, I can actually read wots going on :D

So basicaly.. are there any way (after the BIOS check), to, when gained access to the GRUB menu, tell the booting sequence, to just boot my computer with support for my monitor? 
(btw, its a Samsung 32" LCD-TV, connected via the VGA cable)..

---

### Post by quqdk on 2008-01-29
anyone?

---

### Post by Cute Poison on 2008-01-29
If your still messing aorund with this "installed elsewhere" version of ubuntu then I can see why.

Instead of moving your hard drive out of your computer and into another. would it not be a much simpler task to remove the CDROM from "dad's" computer and put it into your own.. 
At least then you would have no problems with the install or it's operation. 
after the install you can then put the CDROM back into the other system. your will run perfect.

---

