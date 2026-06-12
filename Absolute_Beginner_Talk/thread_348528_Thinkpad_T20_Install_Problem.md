---
title: "Thinkpad T20 Install Problem"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by IronMac on 2007-01-28
Hi all,

I'm trying to install Ubuntu on my old T20 that had a major hal.dll error (don't ask). So, I decided to go with Linux in this situation. I'm at the installation where I've gone through all six pages of the Install window and it begins installation. It then hangs at 34% at copying files while Installing System. Does anyone have a clue as to what the problem is?

Thanks!

---

### Post by moshuptrail on 2007-01-28
Just a guess.  Try formatting the HD using something like the Gparted Live CD.
I've believe (but not sure) that Ubuntu only does a "quick" format during the install.  But if the disk is "messy" the install hangs or fails.
Just a guess.

---

### Post by lamego on 2007-01-28
> 
I'm trying to install Ubuntu on my old T20 that had a major hal.dll error (don't ask). So, I decided to go with Linux in this situation. I'm at the installation where I've gone through all six pages of the Install window and it begins installation. It then hangs at 34% at copying files while Installing System. Does anyone have a clue as to what the problem is?

Are you using the LiveCD ? If yes try with the Alternate CD, the text mode installer is usually more stable.

Unlike moshuptrail the installer does not format the disk during the files installation phase, it you were able to create and format the partitions it should not be disk partitions related.

---

### Post by IronMac on 2007-01-28
I'm using the LiveDVD and, then, I go into the Install process. I could try the text mode installer...

---

### Post by IronMac on 2007-01-29
Ok, I just tried to install through text mode and it stalls at copying files over. I then went to the screen where I could choose "Check CD for Defects" and it goes through its paces but finally dumps me in the Live DVD desktop.

Can anyone tell me if the DVD is defective or what's going on? Thanks!

---

### Post by atihimself on 2007-01-29
try using safe mode installing and reformat youd HDD I had same problems with my notebook, tryed different live CD's  but same thing all the time, so first use gparted, and then install in safe mode (at least Dapper had that kind of option),

---

### Post by IronMac on 2007-01-29
Thanks for the tip but how do I get into Gparted on the DVD?

---

### Post by IronMac on 2007-01-29
Ok, tried installing through Safe Graphics mode and the system has hung at the Installing System screen at 24%.  :(

---

### Post by IronMac on 2007-01-29
Ok, am into GParted and now formating /dev/hda1 as ext3. I'm hoping that this helps.

---

### Post by IronMac on 2007-01-29
Tried a regular install and it has hung at 24% copying files but the cursor can still move around the screen so that's a bit of progress.

Any other suggestions? Thanks.

---

### Post by IronMac on 2007-01-29
Sorry to bump this but I'm hoping to get this install done by tomorrow. Got a lead on an Orinoco Gold wireless card.  :D

---

### Post by IronMac on 2007-01-29
Bumping...

---

### Post by IronMac on 2007-02-02
Ok, giving up on the install for now. It kept stalling out at 24%. I've ordered the Dapper Drake release.

---

### Post by mumbles on 2007-08-05
I had issues with the dapper install cd, and found that if i used a 5.10 cd to install from. i  then upgraded to dapper and used[ http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T21]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_T21") to solve the x problems. dapper works fine now. though a bit on the sluggish side.

---

