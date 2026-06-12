---
title: "glxgears 287 fps is it enough?"
date: 2008-03-15
forum: Apple PPC Users
---

### Post by samisrafi on 2008-03-15
Hello
I have an ibook which have an ati card and i tested the glxgears  it gave me average of 287.334 fps is this rate enough to run desktop effects and compiz-fusion
thanx

---

### Post by BladeMelbourne on 2008-03-15
I am not familiar with the iBook specs. You need to consider a few points:
* how much video RAM your ATI card has?
* what resolution is typically displayed on your screen? (eg 1024x768  )
* OpenGL performance (glxgears is a good benchmark).

If your specs match:
[http://www.apple.com/lae/ibook/specs.html](http://www.apple.com/lae/ibook/specs.html)
Then you should have enough video RAM to run a 1024x768 screen.
However, I think your glxgears framerate should be maybe 3-4 times greater than what you are getting. You may need to tweak xorg.conf

I have a 32 MB ATI Radeon 9200 in my Mac Mini.
My screen is currently 1280x1024 at 24 bit colour.
I get 1230 fps with glxgears.

However, I cannot run compiz because:
* At 24 bit colour,
* With 32 MB video RAM
The maximum resolution supported is 1024x1024.

If I turn the colour depth down to 16 bit, I can run compiz at 1280x1024. However I would prefer colour rather than effects.

Hope this helps.

---

### Post by jacob01 on 2008-03-17
is that full screen or is it the small window? I ran compiz on my old intel igp and i could get 195fps full screen at 1240x768, haven't tried with my new card.

---

### Post by BladeMelbourne on 2008-03-17
My understanding is that people don't resize their glxgears window (otherwise it wouldn't be much of a benchmark).

Some glxgear results can be found here: [http://www.free3d.org/](http://www.free3d.org/)

---

### Post by Tomatz on 2008-03-17
I get around 2100fps with compiz running on my (heavily) overclocked athlon x2 4200

---

### Post by abalone on 2008-03-17
19600 FPS! [SIZE="1"]When I make the glxgears window as small as possible[/SIZE] :redface:

---

