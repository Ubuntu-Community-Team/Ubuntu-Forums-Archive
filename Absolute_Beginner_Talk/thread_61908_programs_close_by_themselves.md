---
title: "programs close by themselves"
date: 2005-09-02
forum: Absolute Beginner Talk
---

### Post by huzzzo on 2005-09-02
Hi, I have a strange problem:
My computer is running with ubuntu from 3 or 4 days with aMule.
Two days ago, when I returned home I noticed that aMule was closed. 
Today when I was using Firefox, it closed itself! Not once, but a lot of times. Xmms also did this!

firefox now is stable and I am using it (but I haven't rebooted my pc).
So... I do not understand...
I am a noob on linux, who could help me?

Thanks!

---

### Post by dbcoder on 2005-09-02
Well, it sounds like these programs are crashing.  Normally programs do not exit on their own.  There is a chance that some hardware is not supported, another chance may be that you have implemented some buggy software, such as a kernel that you have changed the options on, or a buggy beta window manager...

Can you think of anything that you have installed/modified that could possible cause programs to crash?  And please post your system specs.  There is a small possibility there is hardware issues.

Other than that I'm out of ideas.

---

### Post by huzzzo on 2005-09-02
Wow I am very lucky...  :roll: 
thanks for your reply.

Let's start with my (very economic) system specs:
CPU: AMD Barton 2600+ not overclocked w/ liquid cooling by pctuner.net
MB: ECS KM400-M2 (if the problem is hardware, is this worse motherboard)
RAM: 512mb pc3200@2700 (mb do not support pc3200)
VGA On-board

I have installed only some programs like xmms, streamtuner and streamripper, amule and firefox/thunderbird. I use only these programs.
I even touched kernel.

Suggestions?

---

### Post by junior aspirin on 2005-09-06
i have also been getting this. completly diferent hardware though. the only change i have made is to remove one stick of ram, i had 1gig+ now 512mb. this is to see if i have a falty stick ( i get random crashes where nothing works-sems to have solved the problem-i hope). would the removal of the ram affect the stability?

---

### Post by poofyhairguy on 2005-09-06
[QUOTE=junior aspirin]i have also been getting this. completly diferent hardware though. the only change i have made is to remove one stick of ram, i had 1gig+ now 512mb. this is to see if i have a falty stick ( i get random crashes where nothing works-sems to have solved the problem-i hope). would the removal of the ram affect the stability?[/QUOTE]

Bad ram can easily do that.


So can running Breezy.

---

### Post by junior aspirin on 2005-09-06
strange i was running the k7 kernel when the apps were closing on me. iv been booted into the standard one now and it is not happening.

it seems the k7 worked fine with 1gig if ram, but after i reduced to 512mb it started closing stuff on me. strange. i think i was only a bad stick of ram that was causing the random lockups, which is good as ram is a damn lot cheaper than a graphics card like i thought it might be!

---

### Post by nickfull on 2005-09-11
[QUOTE=huzzzo]Hi, I have a strange problem:
My computer is running with ubuntu from 3 or 4 days with aMule.
Two days ago, when I returned home I noticed that aMule was closed. 
Today when I was using Firefox, it closed itself! Not once, but a lot of times. Xmms also did this!
[/QUOTE]

this happens for me also - after an hour or so all programs that are active close themselves down leaving a sad looking empty desktop :o(
 i'm running hoary ppc on a 500mhz pismo with 640 mb ram - as a newcomer to ubuntu i haven't made so many changes to the system yet. i thought this might be something obvious that could be 'switched off' (screen blanking timeout / powerdown time in /etc/console-tools/config ), but maybe it's something more mysterious?! here is part contents of that file:

# screen blanking timeout.  monitor remains on, but the screen is cleared to
# range: 0-60 min (0==never)  kernels I've looked at default to 10 minutes.
# (see linux/drivers/char/console.c)
# BLANK_TIME=30
# Disables Blanking Completely
BLANK_TIME=0

(...)

# Powerdown time.  The console will go to DPMS Off mode POWERDOWN_TIME
# minutes _after_ blanking.  (POWERDOWN_TIME + BLANK_TIME after the last input)
POWERDOWN_TIME=30

any ideas?
thanks for any help

---

