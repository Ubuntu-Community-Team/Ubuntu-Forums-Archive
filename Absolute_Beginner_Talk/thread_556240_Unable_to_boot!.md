---
title: "Unable to boot!"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by WW123abc on 2007-09-21
When I was shutting down ubuntu, it froze. I turned off the computer using the main power switch, and now, when i try to start my computer, I just get a black screen... I dont even get to grub(meaning i cant even open windows)...It won't boot cd's either...

Anyone help please!

---

### Post by chongchongworks on 2007-09-21
Hi, 

It might not be the problem of ubuntu, did u get the congradulations when u finish installation?
When u restart your computer, did it alarm from mainboard?

---

### Post by bikeboy on 2007-09-21
If it won't boot CDs either, it suggests something independent of the OSs on there, did your BIOS reset to default perhaps? Check that the CD Drive is still above HDD in boot priority.

---

### Post by WW123abc on 2007-09-21
no alarm... not sure about congratulations...

---

### Post by WW123abc on 2007-09-21
I cant really check boot order, because my screen is all black from the moment i press the power button

---

### Post by PreviousN on 2007-09-21
I get this all the time. In fact its why my server restarts. The ide master port on the computer is going bad and I'm outta money to buy a new raid card. Anyways...yes, sounds like a problem with anything BUT ubuntu.

== Fix ==
1. Open your computer. Reseat/make sure the cables are in tightly
2. Close your computer
3. Boot, go to bios config
4. Check on boot order. There may be something called "harddrives" that's selectable to configure which hard drive boots.
5. Make sure your hard drive with ubuntu on it is at the top of the list 
6. press F10 (usually) to save and exit
7. Reboot. Press tab to see if your hard drive is detected
8. If detected, and the settings are right in bios, and you still get black screen it could mean something drastic...
9. use live cd (i prefer a slackware one to get to a root terminal) and type "mount /dev/sda1 (or whatever your partition is) /mnt

That should mount your hard drive in the /mnt folder on the cd (i know...weird..but whatever.) 

Then you should be able to recover data/do other scthuff that is good. for teh win.

---

### Post by WW123abc on 2007-09-21
I should have mentioned that it is a laptop. HP dv9550 to be exact... So there really aren't any cables to check... And I can't go to bios config, because the screen is black no matter what i do... It almost seems like the screen is broken, which would be a little weird, seeing as the computer was standing in the exact same place 2 hours ago when it worked...

---

### Post by Sef on 2007-09-21
Is there a monitor around that you can plug in and see if you get anything?

---

### Post by WW123abc on 2007-09-21
yup but that didn't work either.....

---

### Post by chongchongworks on 2007-09-21
Hi, just take out your memory, and then plug in again, see what happen.

Sounds crazy, but it might help.

---

### Post by Sef on 2007-09-21
> Is there a monitor around that you can plug in and see if you get anything?

> yup but that didn't work either.....

I suspect your graphics chip is not working.   How old is your laptop?

---

### Post by WW123abc on 2007-09-21
10 days...

---

### Post by nero_86 on 2007-09-21
I think is a matter of bad assembling of components. Can be the monitors cable or even a not working graphic chip...
I had a similar problem some time ago. Was an hardware problem solved whit the manufacter's laptop guarantee.

---

### Post by paul.matthijsse on 2007-09-21
> **WW123abc said:**
> 10 days...Hi, just return that laptop and ask for a good one. If you hear/see no harddisk activity after booting then the problem might be in your motherboard (an overcharge perhaps). I have a two years old machine like that, it doesn't load the bios anymore. 

Cheers, Paul.

---

### Post by brcane on 2007-10-10
I am having the exact same problem with what is in all likelyhood a nearly identical hp dv9550. Is there any hope of getting my laptop goin again or am I gonna have to contact hp and have a hardware problem fixed? Also I am using the beta 7.1 version, and this appears as if it could be a recurring problem that needs reporting. Thanks for your help. 

Brcane

---

