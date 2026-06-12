---
title: "Low Sound Volume"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by sargonious on 2007-01-05
I recently upgraded to the newest version of Xubuntu. My sound volume is very low even when changing the mixer settings or running the alsamixer command in terminal. What can I do to raise the volume? I have a 533 MHZ Pentium 3 Ibm 300PL with Cirrus Logic (CS4236) integrated sound, 384 MB of RAM, and a 20GB harddrive, with a CD R/W drive just to give you an idea of what I'm running.

---

### Post by annda on 2007-01-05
i think alsamixer gives you the most control over your settings. are you sure you adjusted all the options there (pcm etc.)? i usually get much better (louder) results with that on many linux distributions than i used to with windows.

---

### Post by chesman on 2007-01-05
I have noticed this as well, with my volume control all the way up in Ubuntu, i have to turn the volume up on my speakers a lot more then i would in windows. and i cannot figure out whats going on

---

### Post by Sasa_Ivanovic on 2007-01-05
> **chesman said:**
> I have noticed this as well, with my volume control all the way up in Ubuntu, i have to turn the volume up on my speakers a lot more then i would in windows. and i cannot figure out whats going on
have the same problem.

---

### Post by rkh on 2007-01-05
I had the same problem-really low volume. I fixed it on my machine by going into Audacity and turning the output volume (the slider on the right) all the way up. I have no idea why this worked, but it did.


-RKH

---

### Post by oyvindaa on 2007-01-05
Yeah alsamixer is the way to do it I think. At least it was on my system.

```
sudo alsamixer
```

---

### Post by sargonious on 2007-01-05
Yeah, "sudo alsamixer" is a no-go. Are there any files I can edit to alleviate this headache? What about the ALSA configuration files? Is there anything I could do with those and if so which files could I edit?:evil:

---

### Post by filippod on 2007-01-09
> **rkh said:**
> I had the same problem-really low volume. I fixed it on my machine by going into Audacity and turning the output volume (the slider on the right) all the way up. I have no idea why this worked, but it did.-RKH

Weird as it is, this worked for me as well (IBM X60s + Ubuntu Edgy). I had already checked everything else (including alsamixer and sound preferences) to no avail. 

After installing Audacity and turning the volume to 70% the sound got louder on system level. Before doing that max volume was just acceptable, now max volume is almost unbearable (as it should be).

I wonder what Audacity touches and if it's possible to configure manually what Audacity did.

P.S.
Today, for no apparent reason, the volume went back to very low and the Audacity trick did not work. I played a bit with the mute and the volume buttons of the X60s to no avail. Then I turned the master volume on Ubuntu fully down and fully up and the sound came back to its former "loud" self.
I can't elaborate more or test further because tonight I switched back to my T42 (the X60s was a test machine), but I hope it helps.

P.P.S.
I'd like to add that I never had such problems on the T42. I suspect there is some discrepancy between the Ubuntu master volume and the X60s volume buttons (up, down and mute) but as mentioned I don't have the X60s anymore to test further.

---

### Post by sargonious on 2007-01-11
Nothing, zip, zero. No change. : (

---

### Post by sameoldude on 2007-03-24
> **sargonious said:**
> Nothing, zip, zero. No change. : (

yeah, same here.
no sound on my laptop, tried both solutions above but nothing worked

---

### Post by enoksrd on 2008-02-08
I'm having a similar problem with Gutsy on an X60s.  Turning everything all the way up in alsamixer did not help, but ***WORKAROUND*** if I use the volume buttons above the keyboard I can bring the volume up very high ***WORKAROUND*** (No idea why this works).

---

### Post by tdn on 2008-02-13
I have the same problem on my IBM Thinkpad T42 after upgrade to Kubuntu Gutsy.
I have tried alsamixer, but it does not help. The volume is much lower than in Feisty. Even when turned all the way up.

---

