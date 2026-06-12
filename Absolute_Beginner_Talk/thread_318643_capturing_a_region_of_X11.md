---
title: "capturing a region of X11"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by corstar on 2006-12-14
Is there a tool out there that will capture a selected region of X?
Kind of like any screenshot, but selected area via dragging cursor..

---

### Post by Chonnawonga on 2006-12-14
This is going to sound asinine, but why not just do a screen capture and then crop in Gimp (etc.)?

I mean that seriously, though: what are you doing that requires such a specific tool? I'm just curious.

---

### Post by corstar on 2006-12-14
Yeah, that's the way I have been doing it forever.

there are two reasons why i want to find an app such as this:

- I want to mainly use it for capturing region screenies from dialog boxes, models in k3d, blender etc

- also, vista is shipping with a tool that does exactly that. I want to find it one is around so we have another feature that has already existed on posix systems.

And i think it would be fun.

---

### Post by jic on 2006-12-14
the classical "xwd" - dump an image of an X window - doesn't fits to you?
try ksnapshot or even gimp

---

### Post by raul_ on 2006-12-14
Alt-PrintScreen inside a window will only capture that window...i don't know if that helps

---

### Post by corstar on 2006-12-14
What a fool i am.

Ksnapshot does the trick. Thank you.
I didn't even think of looking there and it was right under my nose.

I will try to write a script that calls a terminal and instantly gives you the selection cursor.

Linux beats winblows once again.

---

### Post by IYY on 2006-12-14
This solution is usually enough, but to answer your question more precisely...

```
import *imagename.png*


```

This will give you a selection cursor which you can drag, and the region will be saved to *imagename.png*.

---

### Post by corstar on 2006-12-14
do you mean

ksnapshot --import imagename.png

there are not many options for Ksnapshot with --help

---

### Post by Coolaman on 2006-12-16
[ auto promotion ] Try my script :

 [http://www.ubuntuforums.org/showthread.php?t=312844&highlight=printscreen](http://www.ubuntuforums.org/showthread.php?t=312844&highlight=printscreen)

---

### Post by corstar on 2006-12-22
That's a cool script. Thanks a lot.

---

### Post by aidanr on 2006-12-22
also, the beryl screenshot plugin does this btw

---

