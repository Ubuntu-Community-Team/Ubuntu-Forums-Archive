---
title: "Sound Problems on Macbook (1G)"
date: 2007-10-22
forum: Apple Intel Users
---

### Post by Pierre Lourens on 2007-10-22
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/102818](https://bugs.launchpad.net/ubuntu/+bug/102818) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hey Everybody!

I've completely installed Ubuntu on my Macbook and everything has gone smoothly -- except for sound.  Adjusting the volume on the keyboard (or software control) seems to adjust the treble and bass instead of volume.  The similar bug is reported [COLOR="Blue"][here.]("https://bugs.launchpad.net/ubuntu/+bug/102818")[/COLOR].  

I tried messing around in Gnome's ALSA mixer and it didn't change anything.  Changing sound preferences in Ubuntu's sound preference didn't fix it.  

I have the Core Duo Macbook, 1st generation.  Any ideas?

Thanks!

---

### Post by mirco_paronetto on 2007-10-23
I have your same problem, tried with alsamixer but nothing changed...dont know how to get rid of it!!If you find something please let me know!!

---

### Post by Pierre Lourens on 2007-10-23
> **mirco_paronetto said:**
> I have your same problem, tried with alsamixer but nothing changed...dont know how to get rid of it!!If you find something please let me know!!

I messed around more in ALSAMixer and still have no solution.  I've got control on my keyboard again, but the sound quality is still bad and it still adjusts treble/bass more than anything.  I'm glad I'm not the only incident.

---

### Post by Pierre Lourens on 2007-10-25
> **Pierre Lourens said:**
> I messed around more in ALSAMixer and still have no solution.  I've got control on my keyboard again, but the sound quality is still bad and it still adjusts treble/bass more than anything.  I'm glad I'm not the only incident.



Ok, I've got a solution.  The sound isn't the best, but it is at least better than it was.  First, I loaded "Gamix" (available off Add/Remove; it's an ALSA graphical editor).  I put Master's levels all the way to the top, clicked the circles over "front".  Then, in the Sound Preferences (System >> Preferences >> Sound), I 
selected "HDA Intel" as the device and selected both PCM and Front in the list (using ctrl to select more than one item).  Click close and your keyboard should control "Front and PCM"--which actually controls the volume.  Weird, I know.

But now: my headphones and normal speakers work on my 1G Macbook.  If anyone has more questions / needs clarifications, please respond.  I've included a screenshot of my gamix window settings.  It doesn't really matter what Front and PCM's levels are set to, because your keyboard controls that anyway.

---

### Post by muselive on 2007-10-26
This worked for me....

System --> Preferences --> Sound

Default Mixer Tracks

Device: HDA Intel

Then select PCM from the list. Then it should work... well, it does for me anyway. Let me know if you have any luck

---

### Post by dmber on 2007-10-26
thank you so MUCH!  that has been my one BIG problem on my macbook.

---

### Post by Pierre Lourens on 2007-10-26
> **dmber said:**
> thank you so MUCH!  that has been my one BIG problem on my macbook.

So it worked for you?  I'm glad to help :).  Cheers.

---

### Post by globose on 2007-10-30
This worked for me, too!  Thanks!

---

### Post by mnml on 2007-10-30
it was explained here:
[https://help.ubuntu.com/community/MacBook#head-d374bb9e1b7183c133759a8c6877a34c50c4ba7d](https://help.ubuntu.com/community/MacBook#head-d374bb9e1b7183c133759a8c6877a34c50c4ba7d)

---

