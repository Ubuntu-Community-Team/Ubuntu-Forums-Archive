---
title: "master volume control does not modify sound after installing some apps"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by mchnhed on 2007-08-06
My master volume control does not work for some reason. I get sound, but I** can't** modify it with the master volume, however I **can** modify it with the volume control in different programs. This only started to happen **after** I installed a bunch of multimedia programs (such as amaroK, Banshee, Songbird, etc.)

Here are the devices listed under the Volume Control in Gnome (File - Change Device):

Intel ICH6 (Alsa mixer)
SigmaTel STAC8750,51 (OSS Mixer)

Does anyone have any insight as to why this might be happening? Thanks in advance!

---

### Post by Pragmatist on 2007-08-06
> **mchnhed said:**
> ....I** can't** modify it with the master volume,!....

What exactly happens?  Can you move the slider?  Let's see if we can control it with **alsamixer**, in a terminal type:
```
alsamixer
```
Use the left and right arrow keys to move from one control to the other and the up and down arrow keys to increase or decrease the volume.  If there is a "MM" under a column, you can turn that off or on by pressing 'm' on the keyboard.  When you are finished, hit the ESC key.

---

### Post by mchnhed on 2007-08-20
Yeah, alsamixer from the terminal "works". I changed all the items that had a "MM" at the bottom to 00 by typing "m" under each item. 

Unfortunately this didn't solve the problem. I just checked it with amaroK, and the master volume does not affect the output. The only way that I can modify the volume level is with the actual amaroK media player.

This is weird though, because with some applications the master volume DOES work...

---

### Post by BlkDragon96 on 2008-03-17
I had a similar problem.  The media keys on my keyboard and the gnome applet changed the master volume for my system, but not the level of the actual sound coming out of my system.  With the alsamixer command though, I was able to determine that this was happening because my speakers were plugged into the headphone jack built into my motherboard.  To make my media keys and the gnome applet work, I went to **System>Preferences>Sound** and selected "Headphones" under "**Default Mixer Tracks**".  Hope this helps.

---

### Post by simion314 on 2008-05-14
alsamixer give me the information that i must set the default mixer track to master or PCM and i set it to master and now it works. This post helped me thanke you Ubuntu comunity.

---

