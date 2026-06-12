---
title: "No sound in Ubuntu"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2007-01-23
Hi
Dual booting Ubuntu 6.10 and WinXP on a Dell Dimension 4550 (2.53 GHz CPU, 1024 MB RAM).
Just upgraded to Edgy about a week ago and most things worked fine including the Rhythm Box music player.
However, now there is no sound whatsoever from anywhere in Ubuntu.
I have checked:
1. Volume controls in Ubuntu/Rhythm Box
2. All appropriate Gstreamer packages installed
3. WMP works fine in WinXP so its not a sound card problem

The symptoms suggest a volume switch is turned off somewhere within Ubuntu but where?
Please help.

---

### Post by deadgobby on 2007-01-23
Dell and getting the sound is problematic. Do you know if your dell has a sound card or on board sound? If a Intell 
 Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
Go to this link
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
Gobby

---

### Post by PaulFXH on 2007-01-23
Thanks for the reply.
I have a Creative SBLive 4.03 sound card.
I can't believe this problem is due to some kind of compatibility issue as I have had sound in Ubuntu on the same computer for some months.
It's only yesterday that I got the problem so everything points to some toggled switch or corrupted file.

---

### Post by xpod on 2007-01-23
Try just typing "alsamixer" in the terminal and check your volume that way.

Sometimes things can end up muted for no apparent reasons

---

### Post by PaulFXH on 2007-01-23
Thanks xpod.
This looks  very interesting if only I knew how to interpret it.

I see eight (8) vertical columns marked ( in this order):

Master
Master M
3D Contr
3D Contr
3D Contr
PCM
PCM Out
Surround

Only the Master and the PCM columns have coloured bars within them so it looks they're the only ones turned on. The PCM Out area doesn't actually have any column at all although obviously they're is space for one here.

Make any sense to you?

---

### Post by xpod on 2007-01-23
left\right arrow keys to select and up\down arrow keys to adjust :D

EDIT not much of any of it makes sense to me......i just follow the instructions as best i can.....IF i can..lol

---

### Post by Wikzo on 2007-01-23
> **xpod said:**
> left\right arrow keys to select and up\down arrow keys to adjust :D

EDIT not much of any of it makes sense to me......i just follow the instructions as best i can.....IF i can..lol

And remeber to use M (Mute) to unmute it! I couldn't get any sound, because some of the things in Alsamixer where muted :P

---

### Post by deadgobby on 2007-01-23
If you have a SB live card. You'll need to go into BIOS and disable the on board sound card. after that you'll here every thing...
Gobby

---

### Post by PaulFXH on 2007-01-23
The sound is back!
Yes, hitting the old "M" key on all of the columns (about half of which were marked MM--which apparently means Mute) brought the sound back.
However, I really have no idea how they got muted.

Many thanks to everybody for your help and advice.

Cheers
Paul

---

