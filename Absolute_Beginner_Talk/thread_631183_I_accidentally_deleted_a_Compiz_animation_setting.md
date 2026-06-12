---
title: "I accidentally deleted a Compiz animation setting"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by sentientd on 2007-12-04
Hi, I accidentally deleted the setting in my Compiz-Fusion manager for the closing animation that is for normal windows... 

I'm looking for the part that goes into the "Window Match" section.

The animations don't seem to work without the correct window match.

Would anyone mind pasting in the correct information so I can pop it in there?

Is there a tutorial on this specific thing somewhere?

---

### Post by rax_m on 2007-12-04
Hi, 

Here's my settings.. this is from the Animations plugin -> Close Window

((type=Normal | Utility | Unknown) | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(role=toolTipTip | role=qtooltip_label) & !(type=Normal & override_redirect=1) & !(name=gnome-screensaver)

Couldn't you just click the little brush on the right hand side to set it to default again?

---

### Post by sentientd on 2007-12-04
> **rax_m said:**
> Hi, 

Couldn't you just click the little brush on the right hand side to set it to default again?

Uhh, well... maybe... lol! I didn't know what that brush was for so I thought I would just leave it alone. :p

Wow. I just learned something!

Thank you! :)

I've been trying to read about "window matching" but its making me feel more confused instead of less. If I'm lucky eventually I'll stumble upon some sort of Rosetta Stone and it will all become clear.

---

### Post by rax_m on 2007-12-05
LOL no problems... sorry I don't know much about the window matching "stuff" ;)

---

### Post by GSF1200S on 2007-12-05
> **sentientd said:**
> Uhh, well... maybe... lol! I didn't know what that brush was for so I thought I would just leave it alone. :p

Wow. I just learned something!

Thank you! :)

I've been trying to read about "window matching" but its making me feel more confused instead of less. If I'm lucky eventually I'll stumble upon some sort of Rosetta Stone and it will all become clear.

Haha, I remember you from messed up X thread. I see you didnt waste any time and you went ahead with installing Gutsy and compiz. Good call ;)

---

