---
title: "Compiz cube - 3D Windows does not work"
date: 2012-10-31
forum: Asus Ubuntu Support (CLOSED)
---

### Post by fi2 on 2012-10-31
I have a fresh install of Ubuntu 12.10. on an Nvidia-Optimus laptop. Activating 3D Windows in ccsm kills the rotate cube effect. I attached screenshot of a situation, not even the worst - which is a completely black screen. Desktop Cube and Rotate Cube work fine.

I know one can live without it, but it is only too easy to get used to the good. 3D Windows is a nice feature to look at application windows on top of each other, so it would be very good to get it work.

Could anybody help please?

---

### Post by milliman on 2012-11-03
I have the exact same issue with my Intel Integraged G41 grahics. The Unity Support Test says that everything should be supported.

---

### Post by ScottDeagan on 2012-11-03
I have the exact same problem. I'm using 12.10 with the Nouveau drivers installed. Those 3D window effects were ultra cool, and although it shouldn't be a big issue (after all, it's "only eye-candy"), for me personally, it is. I really miss the 3D windows - it was something that gave Ubuntu that extra "WOW!" factor when showing off to friends/co-workers.

---

### Post by fi2 on 2012-11-04
Another issue: no transparency of top and bottom of the cube. Opacity slider in ccsm  does not have any effect.

---

### Post by fi2 on 2012-11-13
No solution....?
It is somewhat disturbing that whenever I upgrade Ubuntu there are some good features gone. I may be conservative, but for me clouds and adverts do not compensate sloppy parts.

---

### Post by jerrt on 2012-11-20
I recently installed 12.10 to fix a windows install [go figure, it worked] figured I would try and get my favorite ubuntu eye candy to work, and had this same problem both with the 3d windows and the transparent cube caps.

I am running nvidia 8600gts with the automatically assigned drivers.  I am also running dual monitors.

Thanks in advance

---

### Post by ranger1021994 on 2012-11-20
PLease visit this link and check whether your Unity supports 3D :

[http://www.webupd8.org/2011/10/how-to-find-out-if-your-computer-can.html](http://www.webupd8.org/2011/10/how-to-find-out-if-your-computer-can.html)

---

### Post by fi2 on 2012-11-24
```
Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

```It looks like it does.

---

### Post by QIII on 2012-11-24
Compiz is down to three dedicated developers (and maybe one by now).

3D windows has been taken out of the stack being maintained,  among other things like cylinder deformation.

They just can't maintain it all.

---

### Post by guilleroldan17 on 2012-11-25
Exactly the same issue, is there any workaround?

---

### Post by QIII on 2012-11-25
Yes, there is a work around.

Contact Sam and let him know you would like to work on maintaining some of the Compiz Unity plugins.

[http://smspillaz.wordpress.com/2012/09/07/maintainers-for-the-unsupported-plugins/](http://smspillaz.wordpress.com/2012/09/07/maintainers-for-the-unsupported-plugins/)

That's from [http://www.compiz.org/](http://www.compiz.org/), "Planet", "Maintainers for the unsupported plugins"

---

### Post by fi2 on 2012-11-27
**QIII**:
Thanks for the intel. Not that it makes me any happy. We, people don't need any more development on Compiz, it would be satisfactory only not to degrade it step by step.
As I understand Ubuntu is committed with Unity, and Unity is a Compiz plugin. Not a very firm base, once Compiz support is vanishing.

---

