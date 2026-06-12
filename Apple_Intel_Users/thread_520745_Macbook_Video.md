---
title: "Macbook Video"
date: 2007-08-08
forum: Apple Intel Users
---

### Post by asmith3006 on 2007-08-08
Just installed Ubuntu on my macbook and am loving it :) One small problem though, when I try to play a video (experience ubuntu.ogg for example). When I try and play it I see no video until I move it, and then I get to see a frame or two.

Does anyone have any suggestions? I've got a core duo macbook.

Thanks

---

### Post by benanzo on 2007-08-08
Do you have desktop effects enabled?  This is a known bug in the **intel** or **i810** graphics driver.  To fix it you have to turn off video acceleration in gstreamer.

Open a terminal (Applications -> Accessories -> Terminal) and do:
```
gstreamer-properties
```
Then click on the **Video** tab and under **Default Output** change the plugin to **X Window System (No Xv)**.  Then close it and restart the movie player.  This bug is marked as *high priority* on launchpad, so hopefully it will get fixed before Gutsy is released.

Have a look [here]("http://ubuntuforums.org/showthread.php?p=3138952#post3138952") if you want to fix it in other movie applications too (VLC, MPlayer, Xine, etc.)

Good Luck!

---

### Post by asmith3006 on 2007-08-09
Well, I don't have desktop effects enabled, but I am running Beryl. Is that the same thing in the context of this conversation?

---

### Post by cyberdork33 on 2007-08-09
> **asmith3006 said:**
> Well, I don't have desktop effects enabled, but I am running Beryl. Is that the same thing in the context of this conversation?

Yes

---

