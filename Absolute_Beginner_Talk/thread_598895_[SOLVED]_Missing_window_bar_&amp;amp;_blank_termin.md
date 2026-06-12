---
title: "[SOLVED] Missing window bar &amp;amp; blank terminal"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by BlueK on 2007-10-31
It all started when I used this "gksu nvidia-settings" in the terminal to set up my duel screens, I did that and restarted my computer like it told me to. When it loaded back up, I was missing my window bar on all programs. Then when I went to the terminal to undo my changes to the duel screens (and try and get my window bar back), the terminal looked like a blank white box.

So I'm really in need of some help, I can't undo my changes in the "gksu nvidia-settings" due to terminal being blanked, plus my keyboard has reverted back to the US keyboard system and not the UK one (as it was before I restarted), I also feel the computer is being much slower, but this could be down to the duel screens, I'm unsure.

The only good thing is that the duel screens work perfectly, shame about the mess they seem to have left behind :S

Also, I tried to attach two screenshots on, but Firefox just said 'sending request', I also tried tinypic and photobucket, neither uploaded my screenshots, despite my internet running fast and smoothly :(

---

### Post by avik on 2007-10-31
Try pressing Alt-F2 and typing in "gksudo nvidia-settings".  Maybe that might allow you to access the settings.

---

### Post by Pumalite on 2007-10-31
Run in Recovery Mode and make your changes.

---

### Post by BlueK on 2007-10-31
Okay, I did alt+F2 and I changed the settings back to what they were, however, when I restarted, the window bars on my programs are still not there and the terminal is still blanked out white.

Any ideas?

---

### Post by BlueK on 2007-10-31
Sorry to bump the post, but I really need help on this please!

---

### Post by overdrank on 2007-10-31
> **BlueK said:**
> Sorry to bump the post, but I really need help on this please!

Hi and I am just guessing here but those issues sound like the desktop effects. Are you using any desktop effects?

---

### Post by BlueK on 2007-10-31
I'm sorry, but what are desktop effects? (I'm a right newbie) I'm using 'extra' on 'visual effects' if that's anything?

---

### Post by overdrank on 2007-10-31
> **BlueK said:**
> I'm sorry, but what are desktop effects? (I'm a right newbie) I'm using 'extra' on 'visual effects' if that's anything?

Yes and you are correct in the visual effects. When you saved your nvidia settings you wrote a new xorg and probably removed some things. You may try and add these to you xorg 
 Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
Under the section device. To edit your xorg use this command 
```
gksudo gedit /etc/X11/xorg.conf
``` Hope this helps. Good luck!

---

### Post by BlueK on 2007-10-31
Yes! Thanks so much! It worked! :D

---

### Post by overdrank on 2007-10-31
> **BlueK said:**
> Yes! Thanks so much! It worked! :D

Woo hooo great good luck! \\:D/:biggrin:

---

### Post by bguito on 2007-11-19
overdrank,

actually I am right now with the exact same problem. If i enable the visual effects, a few bars disappear, and more important, the terminal turns blank. It's not a priority to have this working, i'm using these options disabled at the moment. But since the effects look cool, I'd like further assistance from you or any other person if possible.

best regards,
bguito

---

### Post by bguito on 2007-11-19
Sorry, forgot to mention, I tried your steps, but with no success. I also have a NVIDIA. Please feel free to ask me more details that could help. Thanks in advance

---

### Post by overdrank on 2007-11-19
> **bguito said:**
> overdrank,

actually I am right now with the exact same problem. If i enable the visual effects, a few bars disappear, and more important, the terminal turns blank. It's not a priority to have this working, i'm using these options disabled at the moment. But since the effects look cool, I'd like further assistance from you or any other person if possible.

best regards,
bguito

HI and I am assuming you are using the restricted drivers? Could you post your xorg with the command ```
cat /etc/X11/xorg.conf
``` In the terminal located under applications,accessories.

---

### Post by bguito on 2007-11-20
Overdrank thank you for your fast answer...

Anyway, after i posted here I kept trying to find an answer and then i found this:

sudo nvidia-xconfig --add-argb-glx-visuals -d 24

It worked. Actually don't know why but it worked.

So for those that can't have these effects running properly even after doing what u told them to do, this may solve.

Thank you so mutch for your help anyway.

ps: if you know the answer why I only did it this way, it would be interesting to know it.
Thanks once again.

regards,
bguito

---

