---
title: "Made a fresh install... updated... now the sound doesn't work"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by Mardok45 on 2007-06-21
When I installed Ubuntu Feisty on my laptop the sound was working perfectly fine.  After I updated everything, the sound STOPPED working.  I went to the Comprehensive Sound Problem Solutions Guide and followed the instructions until the last step failed ](*,).  

Before I make a fresh install of ALSA, is there a way to revert back?  You know, downgrade...

---

### Post by p_quarles on 2007-06-21
I can only think of a kinda dumb solution, but it should work:

1. Do another fresh installation
2. When you update, uncheck anything that has to do with the sound system.

If that doesn't do it, I would imagine that it's the kernel upgrade that killed your sound. Depending on the level of the kernel upgrade, sometimes the old version will appear in the Grub menu. 

I know that doesn't solve anything, but it should help you diagnose the source of the problem. Good luck.

---

### Post by Mardok45 on 2007-06-21
Just out of curiosity... does anyone have this much trouble with Linux platforms?  I've had Fedora for a while and it did NOT give me this much trouble, at any time.  There's the exception of getting all the drivers to work, but that's more of a "feature" of Linux.

After reinstalling Ubuntu for the 3rd time, I'm almost ready to pack up and go back to my first love, Fedora.

---

### Post by p_quarles on 2007-06-21
> **Mardok45 said:**
> Just out of curiosity... does anyone have this much trouble with Linux platforms?  I've had Fedora for a while and it did NOT give me this much trouble, at any time.  There's the exception of getting all the drivers to work, but that's more of a "feature" of Linux.

After reinstalling Ubuntu for the 3rd time, I'm almost ready to pack up and go back to my first love, Fedora.
No shame in that. Fedora's a great OS. I haven't had any problems to speak of, but as you know it's all a matter of how well a distro gets along with your hardware. If it doesn't, you go for another distro.

---

### Post by Crafty Kisses on 2007-06-21
> **Mardok45 said:**
> When I installed Ubuntu Feisty on my laptop the sound was working perfectly fine.  After I updated everything, the sound STOPPED working.  I went to the Comprehensive Sound Problem Solutions Guide and followed the instructions until the last step failed ](*,).  

Before I make a fresh install of ALSA, is there a way to revert back?  You know, downgrade...

You might want to post this log:
```
lspci
```
Also you might want to try installing all the codecs and drivers for your sound card, just a thought.

---

### Post by BobLand on 2007-06-23
I've gone thru this a number of times.  I made this thread as a reference so I can update it and use it when sound fails.  So far this has worked for me consistently.

```
http://ubuntuforums.org/showthread.php?t=457373
```

---

