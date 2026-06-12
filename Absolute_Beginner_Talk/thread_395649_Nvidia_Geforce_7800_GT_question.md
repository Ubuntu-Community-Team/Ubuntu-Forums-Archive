---
title: "Nvidia Geforce 7800 GT question"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by Churchill on 2007-03-28
I need a little help,

I recently tried installing a dual boot for ubuntu 6.10 for AMD 64 bit processors. I had a few glitches with the cd so i removed my graphics card (Nvidia Geforce 7800 GT OC) and used the integrated on board card to install ubuntu. 

Upon completing the install i ran into a few problems. One, my windows partition was split amongst my two hard drives so i lost windows when i completely erased my 60 gig and put ubuntu on it. this is a different question for a different time i just figured i would include it to give you the most information.

The second problem I am having is that gnome is running reeeaaally slow. moving windows around is very choppy and browsing firefox takes forever. I have a decent AMD dual core 64 bit processor, the specs i am unsure of right now as i am at work. 

My third and final problem is that when i put my graphics card back into my box and boot up ubuntu it give me some fatal error stuff and its really hard to read what the problem is.

My question is this. Where can i go or what can i do to prepare my system for inserting my graphics card? I tired envy but i could not get it to work. I am a serious noob please help me.

Thanks

---

### Post by igknighted on 2007-03-28
I'm not sure why you removed the graphics card to install?  If the live CD wont load, use the alternate CD to install, then boot into recovery mode to install the drivers (sudo apt-get update && sudo apt-get install nvidia-glx && sudo nvidia-xconfig).  Then boot normally and you should be set.  This should fix the slow windows, to speed up FF you should disable ipv6 in about:config.  There are a few how to's with some other FF tweaks, just search the wiki, its all there.

---

### Post by Churchill on 2007-03-28
I didn't download the LIVE iso, I started with the install CD. How do I boot into recovery mode? Do I need to have the Install CD in when I reboot?

---

### Post by igknighted on 2007-03-28
At the grub menu there is an option to boot into recovery mode.  Also, after initial install you shouldn't need the CD again.

---

### Post by lamalex on 2007-03-28
when you're booting hit escape at grub 1.5 and then chose the recovery mode

---

### Post by Churchill on 2007-03-28
Great, 

Thanks for the help guys, I will try this when i get home tonight. Just curious, is this all i need to type?

sudo apt-get update
sudo apt-get install nvidia-glx
sudo nvidia-xconfig

Once i have entered this is to i just type exit or quit or reboot or what?

Thanks again.

---

### Post by dreadlord_chris on 2007-03-28
> **Churchill said:**
> Great, 

Thanks for the help guys, I will try this when i get home tonight. Just curious, is this all i need to type?

sudo apt-get update
sudo apt-get install nvidia-glx
sudo nvidia-xconfig

Once i have entered this is to i just type exit or quit or reboot or what?

Thanks again.
those 3 lines should fix ya up.
when done just give it the 3-fingered salute _**Control-Alt-Delete**_

---

