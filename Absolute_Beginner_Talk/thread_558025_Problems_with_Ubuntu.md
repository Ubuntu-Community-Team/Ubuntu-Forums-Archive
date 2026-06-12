---
title: "Problems with Ubuntu"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by Phoenix27 on 2007-09-23
I have a few problems with Ubuntu. The 2 I am having are, that I cannot run the LiveCD unless it's on safe graphics mode, due to the fact that it tells me I have a problem with X driver or X graphics of some-sort (I use ATI Radeon 9250). I am also unable to connect to my wi-fi router, the computer picks up the signal, but the internet just doesn't work.

How can I fix these?

(I am not a very computer-coding saavy person, so.. make it easy XD)

---

### Post by Pumalite on 2007-09-23
Try Alternate CD ( text mode; installation only) You can avoids graphics problems and other hardware issues. Install easier. More control. Connect to Internet wired. Configure your wireless later.

---

### Post by Phoenix27 on 2007-09-23
> **Pumalite said:**
> Try Alternate CD ( text mode; installation only) You can avoids graphics problems and other hardware issues. Install easier. More control. Connect to Internet wired. Configure your wireless later.

I can't go wired, my internet box is in a different room, connected to a laptop that I can't put Linux on.

---

### Post by Phoenix27 on 2007-09-23
Help please :(

---

### Post by bruce2000 on 2007-09-23
Reconfiguring the x server may help:

```
sudo dpkg-reconfigure xserver-xorg
```

I've got the same gfx card but not had any issues with it.

---

### Post by Phoenix27 on 2007-09-23
How do I do that?

---

### Post by bruce2000 on 2007-09-23
Open a terminal (applications/accessories/terminal) and type it there.

You say the live cd will only start in safe graphics mode, does that mean you havent installed ubuntu yet?

---

### Post by Phoenix27 on 2007-09-23
> **bruce2000 said:**
> Open a terminal (applications/accessories/terminal) and type it there.

You say the live cd will only start in safe graphics mode, does that mean you havent installed ubuntu yet?

Yes

---

