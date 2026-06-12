---
title: "32&quot; HDTV as monitor...issues."
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by HoLLyw00dGT on 2008-02-25
So basically my question:

I have a 32" 1368x768 HDTV as my computer monitor/TV. When I try to go into the BIOS menu of my pc it says no signal...it works just fine on my 15" crt monitor though. I think this is source of my dual boot issue as well. I'm thinking that my tv saying no signal was when the GRUB boot menu was up...so i always just waited and then ubuntu ran by default. Is there something I can do or is this just always gonna be a problem. If it is...i'm getting rid of Ubuntu and going back to windows because i wont be able to dual boot. I am not gonna stop using my tv as my monitor just because of this. 

Suggestions? Same issues?

-Justin

---

### Post by 01000111 on 2008-02-25
Do you have more than one video output on this machine?  If so, there is a setting in the bios that specifies which video card to use at startup...  the choice is usually between an onboard video card and one you've added.

Plug in a monitor into the onboard VGA port, boot to the BIOS setup, and select the other video card.

Worked for me.

01000111

---

### Post by HoLLyw00dGT on 2008-02-25
I have an nVidia 8600GT. I'm assuming my Gigabyte motherboard has onboard audio. Don't all new boards have them? It is brand new. So basically what your saying is to hook up my crt, go into bios, select the onboard car for boot up. I'm not exactly sure where i can do that in bios? Also, How does it know to go to my 8600 after i log into OS...whether it be XP or Ubuntu 7.10?

-Justin

---

### Post by 01000111 on 2008-02-25
Right.  You'll have to poke around in the BIOS 'cause they're all a bit different, but there should be a setting that says the default video card is "Onboard" or "AGP" or "PCI" (depending on the type of card you have.  

As to how Ubuntu knows to switch to the nVidia card, it is specified in the file /etc/X11/xorg.conf

You might also want to take a look at:

[http://ubuntuforums.org/showthread.php?t=682154](http://ubuntuforums.org/showthread.php?t=682154)

for more info on configuring a HDTV.


01000111

---

### Post by HoLLyw00dGT on 2008-02-25
OK i'm having so many issues. I went into bios, looked around and found nothing. The closest thing i found was "Init Display First"...options = PCI or PEG. Tried Peg cuz idk what i'm doing i guess and plugged back in my tv, tried going into bios as a test run....bam...no signal. I just want to dual boot windows and ubuntu >_<

-Justin

---

### Post by HoLLyw00dGT on 2008-02-26
bump. any ideas? i hate this crt and i want my TV back

---

### Post by tgalati4 on 2008-02-26
I assume that you ran *envy* to load the latest nVidia drivers?

---

### Post by HoLLyw00dGT on 2008-02-26
Well apparently I don't have an onboard video card on my gigabyte mobo. Well i can't seem to find it in the manual under specs or anything. I just want to use my monitor =(

---

### Post by HoLLyw00dGT on 2008-02-27
I'm just talking about when i boot my comp, it doesn't show the bios menu if i hit the bios menu key at startup...it goes to no signal. If i do it on my CRT, no problem, shows right up. Nothing to do with linux...yet lol

---

