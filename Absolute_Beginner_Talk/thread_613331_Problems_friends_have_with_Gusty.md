---
title: "Problems friends have with Gusty"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by Nod51 on 2007-11-14
I have 3 friends that are moving from XP to Linux for a couple reasons:
Friend 1) 
- Has time on his hands to play around with
- has an 3 year old Ath64 with 512ram, Vista is not an option and does not give anything new.
- Dual boots with Windows XP, but since the NWN editor got working in wine 0.9.47+, he only boots for Corel Draw (which he is looking for a Linux replacement)
- Never Winter Nights (native), WarCraft 3 (wine), Warzone2100 (native)
- Uses NWN editor (works since wine 0.9.47), and Corel Draw (looking for Linux replacement)
WHAT WORKED:
- upgrading from Feisty by doing a fresh install but saving /home worked fine
- Kubuntu install but installed GNOME and GDM so it is more Ubuntu now
PROBLEMS:
- No Corel Draw equivalent. When asked to use Gimp, he tried to use the scroll wheel for zoom and this "simple"  feature does not work. Krita is close and he is playing with it.
- Virtual desktop of like 1024x768 on his 1280x1024 desktop (monitor is 1280x1024)
- Nothing to be fixed but might give someone an idea, since WC3 only works in wine less then 0.9.45, but the NWN editor only works with Wine greater then 0.9.47, I extracted the .deb in his home directory then made a shell script so it used that wine. Not sure how this could change unless there was an apt option to allow users custom installs in their home.


Friend 2) 
- In collage still, CS->network something
- Just upgraded to a dual core 4800+, some NVIDIA Motherboard, and 300 gig HD
- Tried to put XP on it, but sound does not work and with SP1, can only use 120 gigs of the 300. If he installs Linux (dual boot) XP blue screens on boot, so he had to 'cold turkey' to Linux.
- Never Winter Nights (native), WarCraft 3 (wine), Warzone2100 (native)
- Uses NWN editor (works since wine 0.9.47)
WHAT WORKED:
- I installed the NVIDIA drivers, telling them the packages, all was well
- Having him get the 0.9.45 version of wine (WC3 broke some version of wine after) and install was easy for him
PROBLEMS:
- GDM did not ever bring up BPX on his widescreen 1440x900. I set a bad driver on fresh install, and it still did not load BPX.
- Virtual desktop on login, I had to modify the xorg.conf by hand
- Only plays 1 audio at a time, I realize this is a alsa driver thing and they next version should have a new sound system to allow multiple inputs.

- Nothing to be fixed but might give someone an idea, since WC3 only works in wine less then 0.9.45, but the NWN editor only works with Wine greater then 0.9.47, I extracted the .deb in his home directory then made a shell script so it used that wine. Not sure how this could change unless there was an apt option to allow users custom installs in their home.

Friend 3)
- 1 year of CS then went to be a cook, so he knows vi, but only plays games on computers.
- Got a 4800+ with some NVIDIA motherboard, sound did not work so he got another sound card
- Hard drive failed with XP and he does not have the XP CD and HAS to play his games.
- Plays Warcraft3, World Of Warcraft (aka his 'crack')
- uses some voice chat program (v something, works in wine)
- moved to another state, everything done over phone
WHAT WORKED:
- Installing NVIDIA drivers were easy for him after he searched google and followed the instructions
- Having him get the 0.9.43 version of wine (WC3 and WOW broke some version of wine after) and install was easy for him 
PROBLEMS:
- he did a system update and it went to console, BPX did not come up in safe mode and ask anything. It was easy for him to reinstall because I have /home as another partition
- for some reason, it makes a virtual desktop of 640x480. it works for a while then he claims it starts doing this. I walked him through editing his xorg.conf to only have 1 resolution and all is well
- getting his mic to work was a PAIN. I had to get him to get audacity, hit record, then start clicking on lights and upping all the bars in kmix. one the sound worked his chat program worked fine.



So, to recap in short:
- I have yet to see Bullet Proof X, maybe it is because I only tried on wide screens
- Why so may virtual desktop defaults? is there some setting some place?
- Sound output is great (other than 1 channel for friend 2 and 3), can there be a way to have a simple Mic in? Looking on net there is lots of "turn these on, these off" posts, but wish it was easier...

Still for me, who has been using Linux since 1999 and Debian since 2001, I find everything good and easy, but we should be trying to reach more.

My friend will be sad if Starcraft 2 does not come out for Linux but that will be 4 copies Blizzard does not sell (at least right away).

Thanks for reading and a great distribution!

---

### Post by K.Mandla on 2007-11-14
Moved to Absolute Beginner Talk.

---

