---
title: "Having trouble installing Ubuntu"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by jkelly888 on 2007-11-27
first off, i have built my own computer, have some basic (not the programming language.) programming experience and know what im doing around computers but i am completely new to Linux. I also have heard that Linux and ATI  hardware dont like to work together and i am aware that my motherboard has an ATI graphics card onboard. I would like to know if theres a work around for this so i can install Linux. Ive been looking into Ubuntu, PCLinuxOS and Mepis as for the type of Linux that im going to install. When I put in my Ubuntu CD (7.10) the menu came up and i selected Start/install Ubuntu. It loaded the Linux Kernal and went to a screen that show a string thats later in my post. When i burned a Mepis live CD, it booted, did the same thing as The Ubuntu CD, displayed the string then about 10 min later, it went to a black screen and showed nothing on the screen for about 30 min until i shut my computer. Here is the string that displays on the screen: 
[17179569.656000] PCI: Cannot allocate resource region 1 of device 0000:00:14.0


Heres the stats of my computer:
2x G.SKILL 1GB 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Desktop Memory
200gig 7200rpm hard drive by seagate
AMD Athlon 64 X2 4200+ Windsor 2.2GHz 2 x 512KB L2 Cache Socket AM2 65W Processor
EVGA 256-P2-N755-TR GeForce 8600GT Superclocked 256MB 128-bit GDDR3 PCI Express x16 SLI Supported Video Card
ASUS M2A-VM AM2 AMD 690G Micro ATX AMD Motherboard

---

### Post by phr0ze on 2007-11-27
Before starting Ubuntu, try to select other video modes on the menu. (F2 I think.)  Also do you have any other PCI devices in the computer? Can you disable the onboard video via BIOS/Jumper? etc.

Thanks,

---

### Post by jkelly888 on 2007-11-27
The only PCI devices i have in my computer is The PCI express x16 nvidia video card. Im not 100% sure but i think i disabled it when i got the Video card.

---

### Post by scrooge_74 on 2007-11-27
You are suffering from the same black window users are reporting with ATI in version 7.10, check for threads about black windows, there are a couple of work around for it

---

### Post by candtalan on 2007-11-27
In slightly different circumstances I found that by choosing  the boot menu option of 'use safe graphics'  I was given a command line at the stage when otherwise I would have seen a hang. The command line (ctrl alt F1 from some screens) then allowed me to manage the video driver nominated (incorrectly) inside the file xorg.conf

hth

---

### Post by jkelly888 on 2007-11-27
ok, ill look at black window threads. as for the command line thing, my knowledge of programming isnt enough for me to do stuff in the command line like you said.
oh, also, is there a stable version of ubuntu that would work well for me and not have the same problem im having right now?

---

### Post by scrooge_74 on 2007-11-27
The stable version is 6.06, 7.10 is the latest one with all the whistles and bells. For my part I go even more stable since I am using Debian (first Etch now Lenny).

As for going into safe mode the idea is you can change the driver either by hand by editing  the file /etc/X11/xorg.conf  Then you look for the driver section.

The other way to do it is to type sudo dpkg-reconfigure xserver-xorg (I think you can omit the sudo part since you are already working as root)  then give answers to questions, when it comes to video driver you can choose the ati (open source driver) or a VESA driver then when you finish type startx to see if it works.  If it doesnt then you have to try another driver.  If it gives you a GUI then reboot

---

### Post by crjackson on 2007-11-27
Insert the Ubuntu 7.10 CD, Boot to 1st menu, hit the F6 key and find the word splash in the option line at the bottom of the screen.  Delete the word splash and nothing else.  Continue the the boot process...

If it boots with no other issues and you want to install, come back to the forums and learn how to make it permanant NOSPLASH.

---

### Post by jkelly888 on 2007-11-27
thanks, ill try that later. (i have finals tommarrow and the rest of the week) what im planning on doing is, since im currently dual booting xp and vista. (i hate vista) When i get the time, im going to reformat all my drives, install some form of Linux and mabye install xp on a back up drive just in case. i was told, Linux is very secure when it comes to visuses and the like and it looks really cool. i dont really play much windows games except occasionally, supreme commander, starcraft and rollercoaster tycoon. so ill just use Wine to play them

edit: well i tried your suggestion of deleteing the word splash but it did the same thing. should i have deleted the spaces by it too? also should i have tried starting it in safe graphics mode after deleteing the word splash?

---

### Post by be4truth on 2007-12-08
Asus M2a-VM with Ubuntu 7.10 32bit

There are issues with this board:
First issue: When installing an error like this occurs 'cannot allocate resource region .....'
Solution: go into the BIOS and disable the HPET option. Use the 'Alternate Install CD 7.10'. Before installing pass the boot option 'acpi=off'. Make sure you floppy drive is either connected or disabled in the BIOS as the installation routine hangs looking for it.
After complete installation install the restricted ATI driver via restricted driver module. Resolution up to 1280x1024 is ok. Sound ok. Didn't had much time to test video. Will do soon.

---

### Post by jkelly888 on 2007-12-08
ok, what if i have a seperate video card that i want to use? (its an nvidia) is there anything else  or different that i need to do?

also, is there anyway i could get a live cd going so i could try it out before actually installing?

---

### Post by be4truth on 2007-12-08
Don't know exactly about nvidia but nvidea seems to be no problem under Linux/Ubuntu. Just install first in default graphics driver.That might even work with the Live CD. Then either go to the restricted driver module or come back to the forum.

---

