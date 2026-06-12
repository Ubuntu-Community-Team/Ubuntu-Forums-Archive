---
title: "Churn out best graphics"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by pigbig842001 on 2007-10-31
Hi,

I am a newbie and have just started using GNU/Linux. So my questions may be a little annoying. But I want to throw away M$ from my system and hence need your help.

> 
I have a computer and it's specifications are:
1) Intel Core 2 Duo 2.0 GHz processor.
2) Intel DG965WH motherboard (on-board graphics GMA X3000).
3) Kingston 2 x 512 MB RAM.


I have Ubuntu 7.10 (AMD64) on my system.

The graphics are pretty beautiful and compiz is working great.

But what I think is that the full potential of the graphics card is not used. I can see jagged lines at the edges of the rotating cube.

I want to know
> 
1) What's driving these graphics? What's 3D API?
2) What is Xorg? What is X11?
3) What is GLX?
4) What is OpenGL?
5) What is XGL, XGLx, XeGL?
6) What is AIGLX?
7) What is FGLRX?


What is good? What should I do to get the best out of my graphics?

I've heard from somebody that AIGLX improves graphics performance and it's great. Kindly throw some light on it.

Let there be light.

---

### Post by llamakc on 2007-10-31
You may have some luck doing a bit of this research on your own. Try googling for each of those. Good luck and welcome to Ubuntu.

[http://en.wikipedia.org/wiki/X.Org](http://en.wikipedia.org/wiki/X.Org)

Is one link for a start.

---

### Post by haldean on 2007-10-31
2) [http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System) [http://en.wikipedia.org/wiki/Xorg](http://en.wikipedia.org/wiki/Xorg)
3) [http://en.wikipedia.org/wiki/GLX](http://en.wikipedia.org/wiki/GLX)
4) [http://en.wikipedia.org/wiki/Opengl](http://en.wikipedia.org/wiki/Opengl)
5) [http://en.wikipedia.org/wiki/Xgl](http://en.wikipedia.org/wiki/Xgl)
6) [http://en.wikipedia.org/wiki/Aiglx](http://en.wikipedia.org/wiki/Aiglx)
7) [http://en.wikipedia.org/wiki/Fglrx](http://en.wikipedia.org/wiki/Fglrx)

Wikipedia is your friend :)
Whenever you have a question that starts with "what is...", Wikipedia can usually answer it.

---

### Post by pigbig842001 on 2007-11-01
This is all so confusing. Xgl and AIGLX are in a war.

What's good for me out of the two???

How do I get Xgl or AIGLX on my system???

How far are they different from OpenGL and how do they depend on it???

---

### Post by haldean on 2007-11-01
Those are questions with long answers. What's "good for you" depends on your graphics card and which one it supports. AIGLX has always worked well for me on an Intel 915 Integrated card but for other people with the same card Xgl has worked as well. You'll find most of the answers you're looking for by experimenting and checking on Google & other websites to see which one your card is compatible with.

OpenGL is something different. My understanding is - and I'm no expert - that Xgl and AIGLX are compositors - they change the way your graphics card handles transparency and window management. OpenGL is equivalent to DirectX - it's a library for writing applications that want to use 3-D graphics.

---

### Post by LowSky on 2007-11-01
Even the cheapest graphics card of the last generation will out perform onboard graphics.

---

### Post by linuxlizard on 2007-11-01
Jagged lines on the rotating cube-
2 things- make sure you install advanced desktop effects settings (search for it in synaptic under your administration menu).

once installed, find it in your preferences menu and click on it. Then click on general options, then display settings tab, then change texture filter from good to best.

Also, make sure your resolution is as high as is comfortable for your desktop. Lower resolution, of course, will mean more jagged lines.

---

### Post by pigbig842001 on 2007-11-04
thanx everybody. that will do.

---

### Post by pigbig842001 on 2007-11-04
BTW, this is how my desktop looks,

[IMG]http://img146.imageshack.us/img146/1552/screenshot1uo1.png[/IMG]


[IMG]http://img527.imageshack.us/img527/6097/screenshot4mc7.png[/IMG]

---

### Post by pigbig842001 on 2007-11-04
> **pigbig842001 said:**
> BTW, this is how my desktop looks,

[IMG]http://img146.imageshack.us/img146/1552/screenshot1uo1.png[/IMG]


[IMG]http://img527.imageshack.us/img527/6097/screenshot4mc7.png[/IMG]
What I don't like are the jagged edges.

---

