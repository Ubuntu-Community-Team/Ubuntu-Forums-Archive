---
title: "Second sound card: Audigy SB0090"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by gentix on 2007-08-19
Hello everyone.  I've been using Feisty for about a week now, and I absolutely love it.  I don't miss Windows one bit.  I'd like to thank everyone who helped me get here.  Now that I'm reasonably settled in, I'm starting to think about a few nonessentials I'd like to get running. 

In particular, the guy  I got this computer from installed a sound card called Audigy 1 SB0090.  I'd like to use this sound card because for some reason, I think its better and stuff than my NVidia nForce2 (which is presently working fine).  I know the reason the nForce2 card is being used is because its card "0" and the Audigy card is card "1".  The command ```
cat /proc/asound/cards 
``` returns ```
 0 [nForce2        ]: NFORCE - NVidia nForce2
                      NVidia nForce2 with ALC650F at 0xe8001000, irq 17
 1 [Audigy         ]: Audigy - Audigy 1 [SB0090]
                      Audigy 1 [SB0090] (rev.3, serial:0x511102) at 0xc000, irq 20

```

I've done a little rooting arround in the BIOS to see if I can find how to switch the default, but I couldn't really find anything, and I don't really know what I'm doing so....

there you have it!  Help is much appreciated, thanks :)

---

### Post by wolfen69 on 2007-08-19
did you disable the onboard sound in the bios?

---

### Post by gentix on 2007-08-20
I didn't find "Onboard Sound" but heres what I could find:

Onboard FDD Controller...........Enabled
Onboard Serial Port 1................3F8/IRQ4
Onboard Serial Port 2................2F8/IRQ3
-Onboard IR Function................Disabled

---

### Post by alienexplorers on 2007-08-20
There may be a jumper on the mobo to disable on board sound.

---

### Post by expatCM on 2007-08-20
There has to be a reason why not, and one of the experts here will know why .....  but .....

Could you enter the following to list the installed cards

sudo asoundconf list

and then 

sudo asoundconf set-default-card selectedcard

to set your preferred card as default.  Just change "selectedcard" with the name of card you want from the list .....

I think this will switch use of one card to the other.

---

### Post by gentix on 2007-08-20
Ok, I think this is progress.  Now, the command
>  cat /proc/asound/card]
produces
 > 0 [Audigy         ]: Audigy - Audigy 1 [SB0090]
                      Audigy 1 [SB0090] (rev.3, serial:0x511102) at 0xc000, irq 21
 1 [nForce2        ]: NFORCE - NVidia nForce2
                      NVidia nForce2 with ALC650F at 0xe8001000, irq 17


Which seems to suggest Audigy is now the default card.  But I am still having trouble.  There are five slots on the card.  In Windows, I used to use the second slot from the left.   THe middle slot is for a microphone.  Now, the only slot that produces any noise is the far right slot, and its really granular with a lot of noise.  What could be producing this problem?  I still have all the sound playback options on "Audodetect".  There is a chocie for "NVidia nForce2 which makes the NVidia card work, but no appairent Audigy option.

---

### Post by AJWhitewolf on 2007-08-20
Actually, I just installed Ubuntu on my main rig, and I am having the same problem that you are with my Audigy card.  I get the grainy sound out of the same port (digital out port, by the way), and no sound out of the others...  This would suggest that you have fixed your default card problem, and have faced an all new one with the Audigy card.  I am new to this as well, and I would REALLY like to have my sound.  It is half of what I do on my computer.

---

### Post by gentix on 2007-08-20
Alright AJWhitewolf, we're going to stick together on this and get it solved :)

Sound is a big part of my computer's job too.

By the way, I found this article "https://help.ubuntu.com/community/HowToConfigureSoundBlasterAudigySEinBreezy" on how to configure sound blaster Audigy SE in Breezy.  Now, I have Feisty, and my Audigy card is a SB0090, but perhaps the difficulty is related?

---

### Post by AJWhitewolf on 2007-08-20
I found the answer...  or, at least, it solved my problem

Double-click the volume icon to bring up Volume Control
Click Edit-->Preferences
Scroll to the bottom of the list and make sure that Audigy Analog/Digital Output Jack is selected
In main Volume Control window, click the Switches tab
Uncheck the Audigy Analog/Digital Output Jack box

Your sound should work!

---

### Post by gentix on 2007-08-20
Brilliant!  Brilliant I say.  Have some popcorn :popcorn:

The music is mine :guitar:

Thanks Whitewolf XD

---

