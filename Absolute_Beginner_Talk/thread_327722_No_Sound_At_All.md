---
title: "No Sound At All"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by Dapilot1 on 2006-12-29
I have a old computer with xubuntu on it that wont play any sounds at all.  I tried
sudo asoundconf list
and it told me AudioPCI.  I have an old Sound Blaster 16 PCI.  I checked alsamixer, but i'm not sure if its muted or not.  So, I set the first two settings to 80% and the rest would not move.  Still no sound.  I read a post earlier about a guide to sound related problems, but I can't find it any more.  Does anyone know how to fix my problem or have the like to this sound guide?
Thanks in advanced.

---

### Post by Rippey on 2006-12-29
the guide you're looking for is _[here]("http://www.ubuntuforums.org/showthread.php?t=205449")_.

---

### Post by Dapilot1 on 2006-12-30
Okay, thanks thats exactly what I wanted.  One more if you would be so kind...
How do I do this.

Quote:
Thanks to [http://ubuntuforums.org/showthread.php?t=127402](http://ubuntuforums.org/showthread.php?t=127402) this post I got soundblaster 16 isa working. In short add
Code:

snd-sb16

to /etc/modules then create a new file:
Code:

gedit /etc/modprobe.d/sound

and enter this line:
Code:

options snd-sb16 isapnp=0 port=0x220 irq=5 dma8=1 dma16=5

Code:

sudo update-modules

reboot

Sorry I do not know how to make the cool quote boxes so I used copy and paste.  But yeah, how do I add that code "snd-sb16" to "/etc/modules"?  Once again thanks in advanced.

---

### Post by robinl on 2006-12-30
Copy and paste these codes line by line into terminal

```
sudo su
[[password]]
echo "snd-sb16" >> /etc/modules
echo "options snd-sb16 isapnp=0 port=0x220 irq=5 dma8=1 dma16=5" >> /etc/modprobe.d/sound
update-modules
exit
```

reboot

---

### Post by Dapilot1 on 2006-12-30
So I did that and the sound is still all messed up.  Is it wrong that i have to un-mute "IEC958 1" to hear the poor excuse for garbled sound?

---

