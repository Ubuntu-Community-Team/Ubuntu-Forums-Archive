---
title: "What drivers are used in LiveCD / Recovery Mode?"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by thepuss on 2008-01-21
Good day all...
I'd appreciate an explanation of the following so I can look further... I'm trying to run Xubuntu Gutsy on a Sony Vaio C1 (256Mb max ram, ATI Mobility Radeon)

When I boot LiveCD prior to an install, I can basically setup and do everything I am likely to want to do with Xubuntu for the moment... create internet connection using Netgear wireless card WG511 with WSK/AES key, Browse web, etc.

When I do an install, after it is complete and I boot into it I get a screen of black and white flickering lines. no discernable "anything" and I have to restart. (I have let the system complete boot-up, by watching the harddisk light flicker to see if it corrects itself, but no luck).

If I book into recovery mode, I get a screen that is (or appears to be) fine, but I can't set up the wireless card as I only have basic WEP encryption options available.

So my question... how do I find out the screen and net/wireless drivers being loaded by (a) Live CD and (b) Recovery Mode because they are both better than what's loaded in the completed install?

Ideally I want my completed install to use (for the moment at least) what LiveCD boot uses.

Additional Info...
When in recovery mode, if i look at the xorg.conf file it appears to specify an ATI Radeon driver but I suspect that this is not what is being used in the recovery mode boot.

On recovery mode boot there is an error for Prism54 which I thing is the wireless card, and isl3890 firmware not found (or something like that). Now I *think* this is related to a problem I've seen around these forums and I have to use the ndiswrapper package with this card. Am I in the right ball park here?

Can someone please tell me, where I can look to find out more?

regards,
Puss

---

### Post by renzokuken on 2008-01-21
do you know what grafix chipset your laptop has?

the recovery mode uses the generic **"vesa"** driver i beleive.

the live cd may be detecting your chipset (ATI/nvidia/intel) wrong and using the wrong driver

---

### Post by shearn89 on 2008-01-21
In recovery mode you can run (if its installed, i think it is) "sudo hwd -s", and look at your video card. It should tell you what chipset it is, and you can then install the drivers for it with apt-get. To get you up and running, i'd suggest changing xorg.conf to use the generic vesa drivers, as mentioned by renzokuken.

---

### Post by thepuss on 2008-01-22
Folks,
Many thanks for your ideas and help.
I got the wireless card working with help from a "MatSwe" document on this forum concerning the use of the NDISWRAPPER package, which seems to have done the trick.
The video works fine *provided* I hit Ctrl-Alt-F1 after booting into my completed install. I don't know why I have to do this (otherwise screen is black and white fuzzy stripes still), but perhaps I will find out in the course of my future learning.

ThePuss

---

