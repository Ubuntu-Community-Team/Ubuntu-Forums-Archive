---
title: "XGL Increasing the speed of drawing?"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by uriahs on 2006-11-15
Hi, I have an okay graphics card, if I install XGL will that move the window drawing processes to the graphics card and increase my drawing/refresh speed?

Primarily I'm talking about Azureus drawing it's windows (JRE).

And if it does return a performance increase, how can I install it?

---

### Post by uriahs on 2006-11-15
Does anyone have any opinions/references they can point to? Or should I just be trying it and hope for the best?

---

### Post by d3v1ant_0n3 on 2006-11-15
It's not so much XGL/AiGLX you want, as Beryl or Compiz.

Have a look at the link in my sig for a million and one howtos for installing them on various hardware.

I find that Beryl gives me much smoother window drawing on my hardware- but Azureus is noticeably more laggy than other programs. It was the same with windows tho'- Java is laggy for me.

*EDIT* Sorry, forgot the standard disclaimer. Beryl is still pre beta, and as such can be prone to buggy moments.Nothing that's killed my system, but then I always seem to be one of the lucky ones, judging from the forums:p

---

### Post by dasunst3r on 2006-11-15
XGL is something that renders desktop effects, and will require you to have a decent graphics card.  As a matter of fact, if you try installing that without installing the graphics driver, it will slow down your computer to a grinding halt!  Also, drawing windows, regardless of what's putting them out, is usually a 2D operation, so computers usually work fine even without the drivers or XGL.

So, the ball's back in your court.  What do you want?

---

### Post by uriahs on 2006-11-15
> **d3v1ant_0n3 said:**
> It's not so much XGL/AiGLX you want, as Beryl or Compiz.

Have a look at the link in my sig for a million and one howtos for installing them on various hardware.

I don't want Beryl or Compiz, I just want Gnome to shift some of the processing from my CPU to Graphics card.

I found this site through your links page:
[A &#8220;what is&#8221; guide to 3D desktops]("http://www.freesoftwaremagazine.com/node/1757")

It was really really helpful. I will be choosing my new graphics card based on whether it supports XGL, I like the sounds of AIGLX but it seems AIGLX doesn't like the sounds of me.

EDIT: Beryl and Compiz are both window managers aren't they? And would be a replacement for Gnome? Or just the Gnome Window Manager? (It's getting a little confusing)

---

### Post by uriahs on 2006-11-15
> **dasunst3r said:**
> XGL is something that renders desktop effects, and will require you to have a decent graphics card.  As a matter of fact, if you try installing that without installing the graphics driver, it will slow down your computer to a grinding halt!  Also, drawing windows, regardless of what's putting them out, is usually a 2D operation, so computers usually work fine even without the drivers or XGL.

So, the ball's back in your court.  What do you want?

Well it seems there is a performance increase, and it supports older hardware. I have the nVidia drivers installed for my card, and they are working fine.

We'll see if it slows me down, I am expecting a performance increase though.

Although drawing windows is a 2D operation, it can be processed by the graphics card, this is what I want to hopefully improve responsiveness.

If it doesn't work, I'll upgrade a bit when finance permits. :-)

---

### Post by d3v1ant_0n3 on 2006-11-15
As it stands at the moment, XGL is of most use to ATI card owners- ATI and AIGLX don't work well together by all accounts. I use Beryl with Edgy's built in AIGLX and it's nice and smooth. There *is* a slight lag in comparison to just using metacity as my WM, but it's much smoother and easy on the eye. Pretty much all of the effects in Beryl can be either toned down or plain switched off (wobbly windows aren't mandatory!), and there are plugins available that allow you to use metacity (or kwin in KDE) themes rather than Emerald (Beryl's Window Decorator)'s flashy, glassy ones.

For me, however, bring on the pointless eyecandy!

---

### Post by qamelian on 2006-11-15
> **d3v1ant_0n3 said:**
> As it stands at the moment, XGL is of most use to ATI card owners- ATI and AIGLX don't work well together by all accounts. 
This depends on the ATI card. My laptop has an ATI Mobility Radeon 9000 IGP. It can't use XGL because XGL requires the FGLRX driver from ATI which only supports 2D, not 3D, on my GPU. AIGLX, however, works just fine with the the x.org Radeon driver. On my desktop, which has an Nvidia card, unless I use the current beta drivers, the reverse is true. I can use XGL, but not AIGLX. Withe the beta drivers, AIGLX works fine with the Nvidia card, as well.

---

### Post by uriahs on 2006-11-16
> **d3v1ant_0n3 said:**
> As it stands at the moment, XGL is of most use to ATI card owners- ATI and AIGLX don't work well together by all accounts. I use Beryl with Edgy's built in AIGLX and it's nice and smooth. There *is* a slight lag in comparison to just using metacity as my WM, but it's much smoother and easy on the eye. Pretty much all of the effects in Beryl can be either toned down or plain switched off (wobbly windows aren't mandatory!), and there are plugins available that allow you to use metacity (or kwin in KDE) themes rather than Emerald (Beryl's Window Decorator)'s flashy, glassy ones.

For me, however, bring on the pointless eyecandy!

Okay, but apparently nVidia also doesn't work well with AIGLX.

What do you mean with Edgy's built in AIGLX?

---

### Post by uriahs on 2006-11-16
> **qamelian said:**
> This depends on the ATI card. My laptop has an ATI Mobility Radeon 9000 IGP. It can't use XGL because XGL requires the FGLRX driver from ATI which only supports 2D, not 3D, on my GPU. AIGLX, however, works just fine with the the x.org Radeon driver. On my desktop, which has an Nvidia card, unless I use the current beta drivers, the reverse is true. I can use XGL, but not AIGLX. Withe the beta drivers, AIGLX works fine with the Nvidia card, as well.

Since nVidia is backing the AIGLX these drivers should be better for AIGLX which is supposed to be more actively developed and better developed to be a long term solution.

Are the Beta drivers better than the regular drivers? Are they stable? Are they faster than the regular drivers? Are they hard to setup? Have you had or heard of any problems? Will they be updated through the regular package manager?

---

