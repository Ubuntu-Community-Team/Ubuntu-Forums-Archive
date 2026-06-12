---
title: "Problems With Sound In Feisty!!!"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by Urko on 2007-05-08
Hello :confused: 

Recently I install Feisty on my computer. I' am using Sound Blaster Audigy (one) for sound. System detect my sound card normaly and equalizer in media players show me like sound is playing, no errors etc. but problem is that I don't hear any sound from my speakers. I tried to plug jack in other plug-in connectors even, change IRQ-s in Bios, install emu10k1 sound librarie etc.. but none of this things works.
I am desperate at the moment and I don't know what can I do to fix this problem. Any of yours sugestions or information will be very helpful for me???????

Thenx in advance!!!!!!!!!

Urko :(

---

### Post by Urko on 2007-05-08
Is it posible that system recognize other audio device instead primary audio device (audigy).  

IN TERMINAL :
~$ cat /proc/asound/cards
 0 [Audigy         ]: Audigy - Audigy 1 [SB0090]
                      Audigy 1 [SB0090] (rev.3, serial:0x531102) at 0xd400, irq 21
 1 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x330, irq 5

and howcan I bump my real soundcard to card1 ??????????????????'''

Thnx in advance!!!!!!!!!

Urko

---

### Post by Urko on 2007-05-08
Have maybe someone same problem with sound that colud help me ???

Please :confused:

---

### Post by LuisGMarine on 2007-05-08
If no one answers try asking in #alsa.  That is the unofficial support channel for Alsa.  Ask in that IRC channel and someone might help you.  They are a great bunch of people in there that are very good.

---

### Post by chemtut on 2007-05-08
I had the same problem.However,it was easily solved:
right click the sound icon
click volume control
unmute everything

hope it works

---

### Post by Panzor on 2007-05-08
```
Alsamixer
```
Run that app and make sure that all of the levels are in the middle or at least more than nothing. This fixes many people's problems. I hope it fixes yours.

---

### Post by Heisman on 2007-05-08
One other thing to try is to disable your on-board Audio card
within BIOS.  This helped fix a similar problem for me.

---

