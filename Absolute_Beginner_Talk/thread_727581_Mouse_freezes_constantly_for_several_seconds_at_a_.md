---
title: "Mouse freezes constantly for several seconds at a time"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by newbuntumom on 2008-03-17
This problem just started yesterday.  After about five seconds (but sometimes more) it starts working again.  Strangely, when this happens, the little scroll wheel on the mouse works fine even when moving the mouse does not move the cursor.  After reading about a similar issue in another post, I tried sudo cat /dev/input/mice, and I got no "garbage" from moving the mouse around when it was stuck, only when the mouse would get unstuck.  If that makes sense.

It is a Microsoft Wheel Mouse Optical USB mouse and up until yesterday, worked just fine!

Thanks so much in advance for any advice you can offer.

---

### Post by PointyWombat on 2008-03-18
Hi newbuntumom,

I don't have a solution, just some questions which may help lead to one.

1) If it's wireless, when is the last time you changed the battery? (my #1 suspect)
2) How often does this occur?
3) Are you running any specific applications or it doesn't matter?
4) When the mouse goes dead, is the light in the mouse on, off, dim, bright?

HTH,

---

### Post by newbuntumom on 2008-03-19
Thanks for replying, PointyWombat.

1) It's not wireless.
2) Yesterday it happened a couple times a minute, maybe, but today it seems much less frequent.  Like once every several minutes.
3) I think it only happens when I'm running Firefox.  It seemed to happen at random times while running Firefox, not necessarily when loading a new page or anything like that.
4) The light goes and looks just as bright as normal.

Thanks!

---

### Post by Xiong Chiamiov on 2008-03-19
There *are* some issues with Firefox, particularly if you have many extensions installed, since you are reliant on those authors' code.  For the sake of narrowing down the problem, try using another browser (Kazehakase, Opera) for a while and see what happens.

---

### Post by PointyWombat on 2008-03-20
Sounds like it may be a Firefox issue then. Like Xiong suggested, try another browser and see if problem persists.

This will install Kazehakas:

```
sudo apt-get install kazehakase
```

You'll then find it under applications/internet.

Let us know.

---

