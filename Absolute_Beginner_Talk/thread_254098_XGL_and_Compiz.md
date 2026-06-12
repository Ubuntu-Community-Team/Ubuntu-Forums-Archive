---
title: "XGL and Compiz"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by PPAAUULL on 2006-09-09
I was justwondering if I could run XGL and Compiz smoothly with my built in graphics chip. I have a Dell Dimension 1100 2.8 ghz with 1gb Ram and a Celeron D proceccor. 

Thanks for the help

---

### Post by jordanmthomas on 2006-09-09
What kind of graphics card is it?  I use an Intel i915 with AIGLX (not exactly XGL, but yields the same compiz effects)
You can see what kind you have by doing this:
```

lspci | grep Display

```

that is, assuming you have a PCI onboard card.. stupid me

---

### Post by PPAAUULL on 2006-09-09
I have Integrated Intel® Extreme Graphics 2.

---

### Post by PPAAUULL on 2006-09-09
I also found this one "Intel(r) 82865G Graphics Controller". I hope that helps.

---

### Post by jordanmthomas on 2006-09-09
I am pretty sure you can go with AIGLX and have no troubles.
[http://xgl.compiz.info](http://xgl.compiz.info)
has the repositories you need to add.
You can search around for how to set it all up (there's good guides that are pretty easy to follow)

Also, if you need help there are compiz forums at [http://compiz.net](http://compiz.net)

---

### Post by max.diems on 2006-09-09
Do what I'm doing- wait for edgy. I tried downlaoding a few  times, it didn't work, now I'm hoping edgy's pre-installed XGL Just Works(tm).

---

### Post by PPAAUULL on 2006-09-09
Edgy comes with XGL pre-installed? That would be great!

---

### Post by Dinerty on 2006-09-09
If you wish to try it now before Edgy is officially released then definetely install aiglx, I know some slowdown may happen when blur effect is turned on

---

### Post by ButteBlues on 2006-09-09
Disabling the blur plugin before starting compiz for the first time is the way to go. Blur is just downright resource-hogging.

As for including XGL into Edgy... I think it's a bad move. AIGLX is the direction that Xorg is going in to begin with, so why not go with the smoother path to the end of the road? But whatever, I'll still be using AIGLX since XGL doesn't support my card.

---

