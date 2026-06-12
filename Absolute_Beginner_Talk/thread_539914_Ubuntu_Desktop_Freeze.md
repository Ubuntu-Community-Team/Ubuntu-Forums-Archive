---
title: "Ubuntu Desktop Freeze"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by tj71587 on 2007-08-31
I just got a friends old computer, ran windows xp just fine, but i install ubuntu server on it and the terminal runs just fine, but then i install the desktop and it boots, i enter name and pw and then the desktop loads and the screen freezes.  The computer is an atholon xp with 768 of ram, and ive run ubuntu on worse machines.  Does anyone have a suggestion?

---

### Post by WedgeWouldUseLinux on 2007-08-31
What video card are you using? I've had some video cards that won't run X11 to save their lives.

ATIs especially don't like running Linux, so that would be the first thing to check.

My old ATI 9000 wouldn't run X11, but my ancient pentium 1 era card at least worked. Although, it did performed about as well as a video card with 2MB of video ram could be expected to run.

---

### Post by gundumfx on 2007-08-31
well what gfx card are you using an does it have ram an what prosser

---

### Post by tj71587 on 2007-09-01
It just has onboard graphics (64mg), I do have and extra geforce 4 around the house that i could put in if that would be needed, but the other computers ive put it on with onboard video have worked.

---

### Post by alienexplorers on 2007-09-01
Can you run in terminal
> lspci
so we can see exactly what your onboard video is.  If it's intel it may need the 915resolution driver loaded.

---

### Post by tj71587 on 2007-09-01
It says the onboard video is a geforce 4 MX...could that be a problem?  I changed the drivers to vesa from nv and that didnt seem to help either.

---

