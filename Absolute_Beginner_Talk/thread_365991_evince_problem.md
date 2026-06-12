---
title: "evince problem"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by sauravbhaumik on 2007-02-20
Evince is creating problem. When I start evince more than 4-5 times, the problem begins.
The problems are 
1. after starting evince 4-5 times, evince doesn't start immediately. It takes 1minute approx to start.
2. Once there is problem 1 faced, the system hangs up while shutting down.

I give you the result of starting evince by terminal and scrolling pages of a pdf doc in it:```
saurav@saurav:~$ evince
Attempt to register the same DBusConnection with the message bus, but it is already registered
Error: Bad bounding box in Type 3 glyph
Error: Bad bounding box in Type 3 glyph
Error: Bad bounding box in Type 3 glyph
Error: Bad bounding box in Type 3 glyph
Error: Bad bounding box in Type 3 glyph
Error: Bad bounding box in Type 3 glyph
Error: Bad bounding box in Type 3 glyph
Error: Bad bounding box in Type 3 glyph
Error: Bad bounding box in Type 3 glyph
Error: Bad bounding box in Type 3 glyph
Error: Bad bounding box in Type 3 glyph
Error: Bad bounding box in Type 3 glyph
Error: Bad bounding box in Type 3 glyph
Error: Bad bounding box in Type 3 glyph
Error: Bad bounding box in Type 3 glyph
Error: Bad bounding box in Type 3 glyph
Error: Bad bounding box in Type 3 glyph
Error: Bad bounding box in Type 3 glyph
Error: Bad bounding box in Type 3 glyph
Error: Bad bounding box in Type 3 glyph
Error: Bad bounding box in Type 3 glyph
Error: Bad bounding box in Type 3 glyph
Error: Bad bounding box in Type 3 glyph
Error: Bad bounding box in Type 3 glyph
Error: Bad bounding box in Type 3 glyph
Error: Bad bounding box in Type 3 glyph

```
the "top" result doesn't hint much at the reason of the shut down problem.

---

### Post by ashmew2 on 2007-02-20
How about opening up the synaptic , marking up the package "Evince" for complete removal and then going to a terminal and 
```
sudo apt-get install evince
```

?
If you dont like evince , u could try kpdf or other PDF viewers!

Btw , If u mark it for complete removal , be sure that it DOES NOT remove any other of your applications lol..I once uninstalled about 90% of things (even nautilus)when i completely removed something...

---

### Post by sauravbhaumik on 2007-02-20
> Btw , If u mark it for complete removal , be sure that it DOES NOT remove any other of your applications lol..I once uninstalled about 90% of things (even nautilus)when i completely removed something...
But you see, if you chose to completely remove evince, you have got to remove Ubuntu-desktop too.
I tried to follow your track, stuck at this point yet!

---

### Post by ashmew2 on 2007-02-20
dont worry about the UBuntu-Desktop thing , its just a meta package.
A meta package is something like a list of stuff which come with your gnome installation . U can remove it no problems :)

---

