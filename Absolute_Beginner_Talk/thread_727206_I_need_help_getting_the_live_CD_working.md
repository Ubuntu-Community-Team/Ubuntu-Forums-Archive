---
title: "I need help getting the live CD working"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by msvf on 2008-03-17
I really wanted to tryout linux, but the live cd wouldn't work. I Tried installing ubuntu linux but it got stuck in the partitioning part. I've reinstalled windows xp, and i want to try out linux, but i just don't want to have to reinstall windows again. Is it the cd thats broken?

---

### Post by ShodanjoDM on 2008-03-17
> **msvf said:**
> I really wanted to tryout linux, but the live cd wouldn't work. I Tried installing ubuntu linux but it got stuck in the partitioning part. I've reinstalled windows xp, and i want to try out linux, but i just don't want to have to reinstall windows again. Is it the cd thats broken?

Could be. Did you checked the cd first before booting? There's an option "check the cd for defects" in the welcome screen.

---

### Post by msvf on 2008-03-17
I actually got 3 cds tried every single one, but the live linux thing just wouldn't boot.

---

### Post by scramasax on 2008-03-17
> **msvf said:**
> I actually got 3 cds tried every single one, but the live linux thing just wouldn't boot.

If you can't get the live CD to boot safer to hold off on installing.  (I notice you say in the first post that you tried to install after failing with the live CD.)

If the CD verifies as OK, I wonder about your hardware.  What are you using?  Is it anything very unusual?  If you're really keen to try Linux you could try live CDs for other distros.  How about googling on your PC's model name with the serach term "linux" in there, too?  See if anyone else is successfully running linux on what you've got.

---

### Post by halitech on 2008-03-17
what do you have for a system? The live cd normally requires at least 256 meg to run and install.

---

### Post by spiderbatdad on 2008-03-17
could you post some specs of your computer? Sometimes boot parameters have to be entered at the boot options screen, an example is to press F6 and delete the words ro --quiet splash from the kernel line at the bottom of the screen and replace with ```
noapic nolapic
``` There might also be a bios config that needs to be set, for example set screen display to vga.

---

### Post by prshah on 2008-03-17
> **msvf said:**
> I really wanted to tryout linux, but the live cd wouldn't work. I Tried installing ubuntu linux but it got stuck in the partitioning part. I've reinstalled windows xp, and i want to try out linux, but i just don't want to have to reinstall windows again. Is it the cd thats broken?

Did you disable BIOS virus protection? (You're the third person today to whom I have suggested this... am I getting stuck in a rut?)

---

### Post by msvf on 2008-03-17
it says something like "video out of range" or something like that.  How do i disable bios the anti virus? My computer is an old dell dimension,  but it can still run xp pro without a problem. Would i be able to use software like sony vagas, jetaudio and office in linux?

---

### Post by halitech on 2008-03-17
sounds like an issue with the video card settings. Depending on the amount of RAm, it may or may not run a Live CD. Far as the software you mentioned, no, no and MS office no but you can use open office.

---

### Post by scramasax on 2008-03-17
> **msvf said:**
>  Would i be able to use software like sony vagas, jetaudio and office in linux?

Don't know about the first two programs.  You can run Open Office, which is a kind of Office clone.   OO is fairly compatible with Office files and can also use the new OASIS Open Document format, which is good for future-proofing your data.

---

### Post by weezy8802 on 2008-03-17
if you cant get the live cd to work you may want to try the alternate cd.

---

### Post by msvf on 2008-03-17
> **matmacrus said:**
> I installed 7.10 on an old Dell dimension 4100 (ca 2000 manufactured)- it is looking great except that the sound does not work. When I installed ubuntu  I had no audio devices plugged in. One day I plugged in speakers and it hung up (I rebooted).
If I reboot with speakers plugged there is no soundcard listed when typing lpsci.
If I unplug speakers and reboot I see the soundcard when typing lpsci as Multimedia audio: Olympus Optical Co Ltd unknown device.  There is no listed driver for this on the ALSA matrix page. 

Does anyone know how to get a driver or if something is wrong?
I've seen suggestions for Dell laptops to install linux-backports-modules-generic.

But I am hesitant and curios what this actually does before I do it.
Any help would be greatly appreciated.

Thats the pc i want to install it on, (but without the w) ,  ram is  512mb , put in new hard drive and some other pci cards. graphics card: geforce 2 mx/mx 400.

---

### Post by msvf on 2008-03-17
> **halitech said:**
> sounds like an issue with the video card settings. Depending on the amount of RAm, it may or may not run a Live CD. Far as the software you mentioned, no, no and MS office no but you can use open office.

ahh....so what would i use to listen to music and edit videos?

---

### Post by halitech on 2008-03-17
XMMS, VLC, mplayer, amarock, just to name a few for listening. Far as editing video, cinelerra, DeVeDee, ManDVD, just to name a few.

---

