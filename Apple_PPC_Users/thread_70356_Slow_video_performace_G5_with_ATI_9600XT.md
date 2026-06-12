---
title: "Slow video performace? G5 with ATI 9600XT"
date: 2005-09-29
forum: Apple PPC Users
---

### Post by Flaystus on 2005-09-29
Noticed the screen updates a bit slowly in the OS sometimes, then I tried to load Planet Punguin on a whim and its like I'm running a 386. Took me 2 min just to get the mouse properly over the Quit command.

Is there something wrong with the video support?

---

### Post by stuporglue on 2005-09-29
You don't have video accelration enabled. It's not possible with all video cards, and amount of support varies. If you can check what kind of video card you've got people will be able to give you better ideas of what to expect from it. 

As a really rough not-really-a-benchmark sort of test, you can run glxgears and see how many fps it gets. 
```
glxgears -iacknowledgethatthistoolisnotabenchmark
```
If you're not getting more than 500fps, acceleration is almost definately missing. 

So, post your hardware and the fps from glxgears.

---

### Post by Flaystus on 2005-09-30
[QUOTE=stuporglue]You don't have video accelration enabled. It's not possible with all video cards, and amount of support varies. If you can check what kind of video card you've got people will be able to give you better ideas of what to expect from it. 
As a really rough not-really-a-benchmark sort of test, you can run glxgears and see how many fps it gets. 
```
glxgears -iacknowledgethatthistoolisnotabenchmark
```
If you're not getting more than 500fps, acceleration is almost definately missing. 
So, post your hardware and the fps from glxgears.[/QUOTE]

1680 frames in 5.1 seconds = 326.714 FPS

BTW I already mentioned its an ATI 9600XT.

---

