---
title: "Issue w/ Headphone Jack Not Recognised."
date: 2011-05-10
forum: Any Other OS
---

### Post by DevinJCan on 2011-05-10
Hello and thanks for reading my thread,
I have recently purchased a Toshiba Satellite  C655D-S5138 laptop running windows 7 (removed) and I have installed Linux Mint 10.10  gnome. I am having an issue with the headphone jack as it is not recognised by the system. I get sound from the internal speakers. This is no issue with the hardware. I have run the Alsamixer v1.0.23 in terminal it looks like this:

 [ATTACH]191725[/ATTACH]


Any solutions/suggestions will be appreciated! I thank you for your time.  

:popcorn:

---

### Post by ankarajasekar on 2011-05-10
> **DevinJCan said:**
> Hello and thanks for reading my thread,
I have recently purchased a Toshiba Satellite  C655D-S5138 laptop running windows 7 (removed) and I have installed Linux Mint 10.10  gnome. I am having an issue with the headphone jack as it is not recognised by the system. I get sound from the internal speakers. This is no issue with the hardware. I have run the Alsamixer v1.0.23 in terminal it looks like this:

 [ATTACH]191725[/ATTACH]


Any solutions/suggestions will be appreciated! I thank you for your time.  

:popcorn:
hello i also face the  problem in  11.04

---

### Post by screaminj3sus on 2011-05-10
if you have an intel chipset try this:

gksu gedit /etc/modprobe.d/alsa-base.conf 

Add this line at the end: options snd-hda-intel model=eapd probe_mask=1 position_fix=1

Save, restart.

I've had to do this in pretty much every distro since around when ubuntu 8.04 was released. May also be similar fixes for other chipsets.

---

### Post by DevinJCan on 2011-05-10
](*,)   
 I am tempted to put "Toshiba Tech Support" on blast as they should be called "Windows OS Tech Support." I told the "Tech Support" I had changed my operating system from Window 7 to Linux Mint and the guy was mystified.
[-X<--I can imagine him doing this at his desk.



...I guess I should get to the point. I am assuming that I have an AMD chipset as I have an AMD processor. Anyone with the ubuntu to aide me in these music-less times is a god!

---

### Post by screaminj3sus on 2011-05-11
Tech support only supports the OS that comes with the machine, it makes sense. Pretty much every company will do this.

---

### Post by DevinJCan on 2011-05-14
Solved:  
[http://www.linuxquestions.org/questions/linux-hardware-18/issue-w-headphone-jack-not-recognised-880200/](http://www.linuxquestions.org/questions/linux-hardware-18/issue-w-headphone-jack-not-recognised-880200/)

---

### Post by DevinJCan on 2011-05-14
I know very little about code. I get that it is the magic that makes  things work. Would anyone consider it bad form to choose, say, 
"options snd-hda-intel model=thinkpad" 
over "options snd-hda-intel model=eapd probe_mask=1 position_fix=1"
"options snd-hda-intel model=thinkpad" is working for me now, 
"options snd-hda-intel model=eapd probe_mask=1 position_fix=1" 
seems like a more legitimate code. does this make sense to anyone?

I am going to try "options snd-hda-intel model=eapd probe_mask=1 position_fix=1" and follow up here with what I encounter.


Thank you everyone for aiding me through this learning process. I am  enjoying it. It was a cool and gratifying moment when I plugged my  external speakers in and they worked! 1,000 thank yous!


_ok, The " =eapd probe_mask=1 position_fix1 " did not work for me. so much for how the code looks: if it works keep it, am I right?

---

