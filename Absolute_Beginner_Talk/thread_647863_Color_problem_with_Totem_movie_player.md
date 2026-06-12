---
title: "Color problem with Totem movie player"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by Torqumada286 on 2007-12-22
When using the Totem movie player the colors are off on the files. They can run from too red, to too green, to too blue. I have to adjust the colors for every file as it plays to get the color right. Any ideas what the problem could be?

I originally posted this in the multimedia section, but there haven't been any real responses in 12 hours.  I am hoping that the higher volume of traffic in this section might yield some responses.

Torqumada

---

### Post by djchandler on 2007-12-22
> **Torqumada286 said:**
> When using the Totem movie player the colors are off on the files. They can run from too red, to too green, to too blue. I have to adjust the colors for every file as it plays to get the color right. Any ideas what the problem could be?

I originally posted this in the multimedia section, but there haven't been any real responses in 12 hours.  I am hoping that the higher volume of traffic in this section might yield some responses.

Torqumada

In my experience, Totem is not as robust in any way as VLC (Video Lan Client) is. Try installing VLC and see if the problems go away. I honestly don't know why you are having the problems though. It seems to me that it may be hardware related, or at the very least has something to do with the video card driver you are using and the way it renders overlays.

---

### Post by Torqumada286 on 2007-12-23
VLC is having the same problem, but videos played through Firefox, like at Youtube have normal color ranges.  So is it a hardware problem or software problem?  :confused:

Torqumada

---

### Post by jkblacker on 2007-12-23
What video card and driver are you using?

---

### Post by Torqumada286 on 2007-12-23
> **jkblacker said:**
> What video card and driver are you using?

Radeon X1900XT.  I am not sure if I am using the 7.11 drivers or 7.12.  I am new to Ubuntu and unsure how to find that information.

Torqumada

---

### Post by FreewheelinFrank on 2007-12-23
I found that having some media players installed together caused colour problems. I uninstalled Totem and now the colour in VLC and MPlayer is fine.

I think I also had Realplay(er) as well.

---

### Post by Torqumada286 on 2007-12-23
> **FreewheelinFrank said:**
> I found that having some media players installed together caused colour problems. I uninstalled Totem and now the colour in VLC and MPlayer is fine.

I think I also had Realplay(er) as well.

I only had Totem until someone suggested I try VLC.

Torqumada

---

### Post by rune0077 on 2007-12-23
Dumb question: have you enabled deinterlace? If not, this can cause colour distortion on DVD's and other movie files. In Totem, it's done under View menu.

---

### Post by Torqumada286 on 2007-12-23
That may have done it, but I am not sure.  I don't have any more time right now to fix it.  Thanks for the help so far.

Torqumada

---

### Post by akawale on 2008-06-17
This happens to me when I play a file using realplayer.
After that, every media player (except flash) has colors that area all screwed up. Everything appears blue.

---

### Post by marcon00 on 2008-06-19
I have the same prolem and it seems after instralling RealPlayer !! :) all video media plays in blue theme !!

---

### Post by aboud on 2008-06-21
I share the same problems with you, and nothing seems to help
i uninstalled almost every thing i tried again, beginning from installing Totem alone, then i removed it and installed gstream(s) and installed it again and i tried VLC, but now way .. all my video are black and white.. 
any idea?

---

### Post by KhaaL on 2008-07-19
I have this in both VLC and totem. mplayer seems to have been spared from this though. changing values in gstreamer-properties didn't help much.

---

