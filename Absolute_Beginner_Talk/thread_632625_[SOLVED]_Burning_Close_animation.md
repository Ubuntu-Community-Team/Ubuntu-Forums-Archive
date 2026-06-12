---
title: "[SOLVED] Burning Close animation?"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by Phiber_tek on 2007-12-05
I've got everything working great except for my animations...whenever I close a screen it simply fades down into the bar, the animation I'd like it to is the burning one where it just burns the window up...how do I go about doing this? Thanks!

---

### Post by Therion on 2007-12-05
That animation is listed as "Fire" in the Effect Settings section.  

If you want windows to burn when closed, obviously, you'd to set that option (Fire) as the close animation.

[Pertinent Link]("http://wiki.compiz-fusion.org/Plugins/Animation#head-0a30508088c6419f1b222114d6b5c4f012780bd5")

---

### Post by Phiber_tek on 2007-12-05
> **Therion said:**
> That animation is listed as "Fire" in the Effect Settings section.  

If you want windows to burn when closed, obviously, you'd to set that option (Fire) as the close animation.

[Pertinent Link]("http://wiki.compiz-fusion.org/Plugins/Animation#head-0a30508088c6419f1b222114d6b5c4f012780bd5")

I did that, the included screen shot shows what I have as my settings but still whenever I press the X to close it just 'disappears'...

---

### Post by jordank on 2007-12-05
This sounds really neat, but where are you seeing this "Fire" option? Is it just in the Advanced Desktop Effects Settings Menu?
How would I go about getting this?

---

### Post by Phiber_tek on 2007-12-05
Well the image is way to big so I suppose it's just as easy to tell you...I have none of them selected but 'burn' in the Close animations tab in animations under advanced desktop effect settings burn is the only one selected but it still fails so yah i guess Im not too sure what to do about that...

---

### Post by Therion on 2007-12-05
> **Phiber_tek said:**
> I did that, the included screen shot shows what I have as my settings but still whenever I press the X to close it just 'disappears'...

Hmmmm... not sure what to tell you then.  Restart X maybe??  Also, I don't see a screenshot in your post, that might be helpful, but if you know how to configure the animations, setting fire to your close animation is no different than any other...

Edit:

From your above post it sounds like you're doing everything correctly.  Kickstart X and see if that will maybe get things going for you.  Not sure what else to suggest.

---

### Post by jordank on 2007-12-05
Okay, I see what you're talking about now.  What do you put in the window match part?

---

### Post by Phiber_tek on 2007-12-05
Wait when I said X i meant just like the X button up in top right or left of window to close that window but I think that might be my problem too What should be in the top half of that window? In the bottom half it has a list of all the animations but in the top half there's that box that you can add stuff to, I added one and put the animation as 'burn' and duration at 200 but I'm not sure what to do with Window Match or Options? Could this be it?

---

### Post by jordank on 2007-12-05
Yeah. that's what i'm talking about. You're going to have to put something in the match window part, but i don't know what.

---

### Post by jken146 on 2007-12-05
In Window Match, I have ```
((type=Normal | Utility | Unknown) | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(role=toolTipTip | role=qtooltip_label) & !(type=Normal & override_redirect=1) & !(name=gnome-screensaver)
```

[Screenshot]("http://www.dur.ac.uk/j.r.kennedy/compiz-shot.png")

---

### Post by Phiber_tek on 2007-12-05
Hmm...me neither but my Cube just crashed too...so I think I may have broke something I'm just gonna do a restart, hopefully that fixes it because I just had it all set-up nicely but yah it just froze and when it was back I had 1 workspace but everything was still the same in Advanced Settings and I hit alt+ctrl and clicked and dragged but nothing happens so I'm not sure what just happened?

---

### Post by JillSwift on 2007-12-05
Chances are you have a line already (the one on top) with a "match" like so:```
((type=Normal | Utility | Unknown) | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(role=toolTipTip | role=qtooltip_label | name=gdesklets-daemon) & !(type=Normal & override_redirect=1) & !(name=gnome-screensaver)
```This matches nearly every window type already, notably excepting menus, tooltips and the like. You'll want to edit this line so that the effect is "Burn". Double click it to edit, then use the drop-down menu in the dialog.

Alternatively, if that top line says "Random", just un-check everything but "Burn".

---

### Post by Phiber_tek on 2007-12-05
Beautiful looks completely amazing thanks a bunch!!!

---

