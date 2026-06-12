---
title: "Possible Issue - B&amp;W G3"
date: 2007-05-04
forum: Apple PPC Users
---

### Post by mbain on 2007-05-04
I've come across a bit of a snag with my G3.  I had originally set it up where I'd swap drives completely between an OSX dedicated drive and an Ubuntu dedicated drive (I figured this was easier than trying to make them share space).

On installing the newest version of Ubuntu, I've hit on a snag.  I can no longer boot from a CD, I can no longer boot the MacOSX drive...but the Linux drive works fine.  I no longer have the grey screen at startup, no longer get a startup sound, and no key sequence (command-option P R or F O) will cause anything to happen.  If I hit C to boot from the CD, it seems to attempt to read the CD, then just freezes...and this is the case no matter if the CD is the Ubuntu CD that I installed with or any MacOS install disk.

I'm hoping someone out there might have encountered this at one point and know how to fix this issue.

---

### Post by prince_alfie on 2007-05-04
I think that it's time to replace your PRAM battery... you can figure it out by looking at the motherboard and then getting a new one for it.

---

### Post by mbain on 2007-05-04
Checked the battery, tested the voltage on it.  Battery is a 3.6V ER3S and is testing at the proper voltage.  I do thank you for the idea though.

---

### Post by stmiller on 2007-05-05
Try booting and holding down the 'Alt' key. See if that gets to a menu to let you choose OS X. Sounds like the boot partition may need to be repaired.

---

### Post by mbain on 2007-05-05
Attempted holding down Alt on boot.  Nothing happened.  It does what it has been doing all along.  It holds at a black screen as it boots, then goes right into Linux.  No grey screen, no boot noise.

---

### Post by gwoodard on 2007-05-07
How much ram do you have?  Depending on how much you have you may need to use an alternate cd (text-based) and try to reinstall ubuntu from there

---

### Post by mbain on 2007-05-08
My memory isn't really an issue.  The system runs Ubuntu fine.  I've got 4 128MB sticks in there.  The problem is, the system refuses to boot any CDs now, Ubuntu or otherwise, and also does not give the normal grey screen on boot, nor the boot noise normally associated with the box.  None of the control codes work to reset or access the PRAM or any other of the functions you'd expect it to have.

---

### Post by stmiller on 2007-05-09
I don't know the hardware of this machine. But have you tried any sort of SMU (?) or PMU reset button?

And also, if there is a battery on the motherboard, you can unplug the computer from power, then remove that battery for about 10 seconds. Then replace the battery. That might reset it and get things going again.
EDIT: woops, I see you have already removed the battery.

---

### Post by mbain on 2007-05-10
Yes...attempted that as well...(recessed button on the front, pressed to get the beeps) no change in its boot behavior.

---

### Post by gwoodard on 2007-05-10
Have you tried other cd drives? maybe your cd drive is broken or messed up

---

### Post by odelay on 2007-05-10
Just out of curiosity, how are your drives connected?

I too have a B&W G3 Powermac (First Gen).  The first gen had a problem where you had to use a PCI ATA card to add larger, non-apple drives.  I was unable to install Feisty on either of drives attached to the PCI card (see well-documented yaboot bug), so I had to dig up the original 8 GB drive.  Installation went fine.

Did any yaboot errors come up during installation?  I know you said you're able to boot into Ubuntu, so probably not.  I remember reading that there's another problem with the bootloader and having multiple internal drives hooked up during installation...but seemed to have gotten things working fine once, so this would negate that.

Sorry my post isn't exactly helpful to you...but since there are so few B&W G3 users, and so many problems with it, it's nice to get an idea of how everyone's scraping by.  Oh, and if you don't mind me asking, what graphics card are you using (ATI 7000 over here--no luck with xserver).

Best of luck

---

### Post by RU-In? on 2007-05-15
Hi, I have just aquired a mac g3 b&w yosimite. I got it at a garage sale for $16, no memory and no hard drive. I got it up and running with a 20g hard drive and 128m of ram and an ubunu 6.06 LTS install (very qwerky at this time). I am unable to boot into the open-firmware, and none of the norm. mac boot options work, ie: hold down 'c' or hold down 't' for target mode. I don't know if this will help, but I have been poking around the web looking at open-firmware. I believe what is going on is that open-firmware handles the boot process, and how it does that is it writes a small (32k) file to the hard drive. Mac OS installs one, of course but I think when we install another OS, that file is different now. Maybe, big maybe,...you might want to use the same boot file on both drives, and I also read a previouse post and it mentioned the troubles that the b&w g3 had with two drives on its onboard ide controller. I have also read somewhere that it will not support large partitions (i think over 128g though). anyhow, if I find more solutions i will post...again, I might be way off track too. My advantage is that I don't need mac os, and I seem to have a good install going right now...for like 20hrs or so...

---

### Post by gwoodard on 2007-05-15
Have you tried the alternate installer of Ubuntu? It is made for your memory amount and is text based (I had about the same problems except a smaller HD (6.5 GB) and had to use 6.10 and then upgraded to 7.04)

---

