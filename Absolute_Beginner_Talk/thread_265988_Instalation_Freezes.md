---
title: "Instalation Freezes"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by W2UOS on 2006-09-26
So, i have wasted a shiz load of CD's trying to get Ubuntu and end up downloading the server instead of the desktop. anyways, so now i tried downloading the desktop ontop of the server so it will be wiped out(the server will be whiped out)but when i say "Start or Install Ubuntu" it goes fine until it comes to "preparing restricted files" and so on. after that, the black screen shows a underscore that usually blinks on and off but now it just freezes and i cant even open my cd-drive....

get what i mean? if you do PLEASE help lol. i need a load of it.](*,)

edit: i downloaded the desktop. i386 version.....if that helps:-|

---

### Post by Dinerty on 2006-09-26
Some people do have major problems with the LiveCD, have you tried the alternate CD installation?, many people who have issues with LiveCD use this alternate CD and have better luck

[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

---

### Post by W2UOS on 2006-09-26
what is the difference between the Desktop and Alternate download? im tryign to download the Alternate CD right now but whats the difference

edit: oh yeah, is the Alternate download a ISO file? or do i have to make it an ISO myself or at all?](*,)

---

### Post by crazedgremlin on 2006-09-26
The alternate CD doesn't include the "try-out" mode.  Just the barebones installer.  The live-cd is a fully-functional desktop that runs off of the cd.
Make sure you have the right architecture too, like if you have an AMD-64 chip don't install the 32-bit version.
The alternate install IS an iso.  Just download it from [http://www.ubuntu.com/download](http://www.ubuntu.com/download) .

Good Luck!

---

### Post by Dinerty on 2006-09-26
> **W2UOS said:**
> what is the difference between the Desktop and Alternate download? im tryign to download the Alternate CD right now but whats the difference

edit: oh yeah, is the Alternate download a ISO file? or do i have to make it an ISO myself or at all?](*,)

The alternate CD is more text based and may help you out, the format is .iso and can be burnt immediately after downloaded, try to check the burn for errors to.

---

### Post by whizbaby on 2006-09-26
No, it comes as .iso. Main difference is that you have more power over what is installed in which way (e.g. at cd boot menu type F6 and you can select *expert_mode*). Another difference: desktop installer loads an x-window-system, alternate installer doesn't.

---

### Post by W2UOS on 2006-09-26
okay, thanks. im downloading alternate i386 right now. lets hope this is the last time i have instalation problems

---

### Post by W2UOS on 2006-09-26
> **whizbaby said:**
> No, it comes as .iso. Main difference is that you have more power over what is installed in which way (e.g. at cd boot menu type F6 and you can select *expert_mode*). Another difference: desktop installer loads an x-window-system, alternate installer doesn't.

what happens in expert mode? im to scared to try since im a a total Ubuntu newbie

---

### Post by whizbaby on 2006-09-26
Basically it was an example for a special feature (can precise a lot of configuration including arguments passed to the kernel) you don't have on desktop install, but you can happen to need it in the near future. What is your hardware?

---

### Post by W2UOS on 2006-09-26
Im not sure, i kidna forgot, and if i want to check it out i will have to change hardrives manually lol, i have 3 computers and 2 monitors....all i know is that my comptuer cant suport the 64 bit version

---

### Post by whizbaby on 2006-09-26
I think the BIOS of each computer will tell you about the mainboard,CPU and RAM (BIOS is accessed by pressing a special key printed on screen at bootup). Starting the live CD and typing *lspci* into a terminal will show all connected PCI cards.

---

### Post by Al_Vampyre on 2006-09-27
I had terrible trouble with installation freezes at random parts of the 'preparing' phase, suddenly occured to me that this stuff was probably being extracted into RAM and that may be the problem.

I'm running an overclocked Opteron 165 so I reset to stock and the installation went like a charm first time. Might not be related to your issue but might help someone else...

---

