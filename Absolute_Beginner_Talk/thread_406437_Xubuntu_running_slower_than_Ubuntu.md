---
title: "Xubuntu running slower than Ubuntu?"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by rikc on 2007-04-10
This isn't something I particularly need help on, but I was curious and wanted to ask.

I purchased an IBM Thinkpad x23, installed Ubuntu on it, but considered Xubuntu after hearing how much lighter it was.  This obviously isn't a very powerful machine, so I thought it'd be worth checking out.  I installed Xubuntu Fawn, and it ran terribly!  The response time was awful.  I don't think it was an issue with my video card, as once I actually got programs to run, say GAIM, they would look fine (GAIM would scrool well enuogh when an IM would send/recieve)

I installed Ubuntu Fawn shortly after that and it's running smoothly, so I don't have any real reason to find a lighter OS I suppose.  I'm simply curious as to what might have had Xubuntu running so slowly, if anyone has any ideas.

---

### Post by PointSource on 2007-04-10
If you're using xubuntu 7.06 beta (Fiesty Fawn), then it may not work as well because its still in beta, try using an older version (6.06 or 6.10).

---

### Post by GuitarHero on 2007-04-10
Maybe the xubuntu fawn isnt up to snuff yet.  Did you try edgy or dapper?

---

### Post by Brendantb on 2007-04-12
Hi, 

the IBM X23 is a fantastic machine, with a low weight and power consumption. However it only has an 8mb video card, and in that it shows its age. 

Feisty Fawn, the latest version of Xubuntu, comes with the latest version of the Xfce desktop, Xfce 4.4.0. This is a great advance on the previous iteration, with a lot more support for eye candy, such as transparency and drop shadows. These effects come enabled by default, but the 8mb video cards will struggle with them. That is perhaps why you have had so much problem with redrawing windows, etc, in your new installation. You may unenable the compositing effects in the window tweaks section of settings; doing so will really speed up an older machine. 

Without doing so, it is difficult to see how one can any longer claim that Xubuntu is a light desktop for older computers. It is really maturing into an equal rival for both KDE and Gnome. But it is still a very competent desktop even with the compositing effects turned off, so perhaps you should consider giving it a second chance...

---

### Post by regomodo on 2007-05-08
Hi

I have a T'Pad 570E, very old, and i'm reasonably happy with Xubuntu Feisty on it

I did notice one thing though. Is the default desktop background very jaggy i.e the gradients are not smooth?

Mine had this problem. I found out it is because of xorg. It sets the monitor/graphics chip at 24bit when it can only run at 16bit. It makes moving windows and scrolling things very slow and rather unsightly.

I edited my xorg.conf by removing the 24bit subsection and setting the default bit depth to 16.
Works like a charm now

---

