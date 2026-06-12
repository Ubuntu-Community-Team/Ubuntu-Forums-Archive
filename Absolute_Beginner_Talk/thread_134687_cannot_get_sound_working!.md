---
title: "cannot get sound working!"
date: 2006-02-22
forum: Absolute Beginner Talk
---

### Post by candide on 2006-02-22
hi

I am running breezy on a dual boot ubuntu and XP machine.  
I have never been able to get ANY sound to play! 
nothing is muted, ubuntu seems to have detected the sound card, when i play an mp3 the tab moves along that bar like it is playing, but NO SOUND!

what could i try? 
maybe i need to load a driver or "redetect" my card? could xp be interfering somehow?\

thanks

---

### Post by Rumor on 2006-02-22
What sound card do you have? Does your motherboard have integrated sound on it? 

Click System | Preferences | Sound and make sure that the sound card you are using is listed as the default sound device. 

When I installed Ubuntu, it listed my onboard sound as the default. When I switched to the default device to my Audigy, it worked just fine afterward.

---

### Post by candide on 2006-02-22
[QUOTE=Rumor]What sound card do you have? Does your motherboard have integrated sound on it? 
[/QUOTE]

The only card listed is an intel ICH6
to my knowledge, this IS the right card.

any more suggestions?

---

### Post by LordBug on 2006-02-22
> to my knowledge, this IS the right card.
You're implying you have more than one soundcard... is this the case?

Your speakers are hooked into the correct output?  They are powered on?  They are turned up?  Stupid questions, I know, but let's cover all the bases.

I'm assuming your MP3 player is XMMS?  If the bar is moving, your sound hardware is seen.  I'd suggest firing up alsamixer from a command line and double checking if your outputs are muted (I've had this happen a few times now).

---

### Post by rudiz on 2006-02-22
....

---

### Post by candide on 2006-02-22
lord bug was right- i have 2 soundcards! i never knew! i had been trying to use alsa mixer- but i needed to use OSS!!

just right click on speaker icon in top R corner, properties, switch to OSS and SOUND!!!!

thanks for the help

---

