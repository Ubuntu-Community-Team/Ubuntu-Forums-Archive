---
title: "Problem with Sound!"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by merkki on 2007-10-27
There is no sound coming at all! I know there is NO problem with the speakers etc.

This is what I get when I type  lspci -v  into shell:
-------------------------------------------------------------------------------------------------------------

00:0b.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
        Subsystem: Creative Labs CT4832 SBLive! Value
        Flags: bus master, medium devsel, latency 64, IRQ 9
        I/O ports at c400 [size=32]
        Capabilities: <access denied>

00:0b.1 Input device controller: Creative Labs SB Live! Game Port (rev 08)
        Subsystem: Creative Labs Gameport Joystick
        Flags: bus master, medium devsel, latency 64
        I/O ports at dc00 [size=8]
        Capabilities: <access denied>
-------------------------------------------------------------------------------------------------------------
(Theres a lot more stuff but they don't have anything to do with SB)
Note: access is denied for ALL of my drivers!

I think the problem has something to do with the access denied thing. What should I do? Can access be granted somehow? Can I install something?

THANK YOU VERY MUCH FOR HELP!
I have wasted 2.5 hours trying to solve this myself.

My sound system: Creative Sound blaster live 5.1

---

### Post by DefianceX on 2007-10-27
I have the same sound card and I had sort of the same problem up until a few hrs ago. Sometimes, the pc will boot with audio, half the time, its mute.

I have looked around and found a solution that worked for me.

I disabled the motherboard sound which you can turn off in the BIOS settings. I've now booted ubuntu 5 straight times and all of them with audio so I figure that was the solution for me.

Not sure if that will work for you but good luck.

---

### Post by merkki on 2007-10-27
Where exactly do I find that in bios? Is it the one called Onboard Audio. Sry if this is a stupid question but im a real newbie.

BTW: I found that Sound Blaster was Disabled in bios, so I enabled it, but it didn't work...

I've found lots of other threads with the same problem as I have... but none of them have a solution.

---

### Post by DefianceX on 2007-10-27
Yes try to disable the onboard audio option in the BIOS.

---

### Post by meborc on 2007-10-27
type ```
alsamixer
```in terminal and turn up all the volume... if some channels are muted use the M key tu unmute them... it might just be as simple as that

---

### Post by merkki on 2007-10-27
When I write sudo lspci -v i get:

-------------------------------------------------------------------------------------------------------

00:0b.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
        Subsystem: Creative Labs CT4832 SBLive! Value
        Flags: bus master, medium devsel, latency 64, IRQ 9
        I/O ports at c400 [size=32]
        Capabilities: **[dc] Power Management version 1**

00:0b.1 Input device controller: Creative Labs SB Live! Game Port (rev 08)
        Subsystem: Creative Labs Gameport Joystick
        Flags: bus master, medium devsel, latency 64
        I/O ports at dc00 [size=8]
        Capabilities: **[dc] Power Management version 1**

---

### Post by meborc on 2007-10-27
did you try alsamixer?

---

### Post by merkki on 2007-10-27
I turned all volumes on alsamixer on max, all unmuted. nothing work. When I enable SB in bios and I try it then: BOOOOOOOOOM, there it comes like magic SOUND. man that was loud. I sure woke up:p 

THanks heaps guys!!:):):)

---

### Post by DefianceX on 2007-10-27
I thought that didn't work the first time you tried it?

---

### Post by meborc on 2007-10-27
no problem dude :D ... nice to know it helped you... just be sure to play a bit with the alsamixer to see what channels are you using... it is good to mute the channels you don't use... i had some noise from my built in mic channel... muting it fixed the quality

rock on!

---

