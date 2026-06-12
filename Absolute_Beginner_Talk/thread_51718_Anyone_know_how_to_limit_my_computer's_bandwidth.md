---
title: "Anyone know how to limit my computer's bandwidth?"
date: 2005-07-25
forum: Absolute Beginner Talk
---

### Post by GreyFox503 on 2005-07-25
I'm using Ubuntu 5.04, and have searched the forums but can't find exactly what I'm looking for.  I need a program not to *monitor* my bandwidth, but to *regulate* it.

Some programs (like Azureus, which is great) can do this pretty easily, but I want something that can be a systemwide bandwidth limiter that I can adjust in realtime.

Specifically, when I'm getting large amounts of Synaptic package updates or something else, my bandwidth usage goes through the roof, which upsets some of the more sensitive members of my family (i.e. little brother playing Halo 2 online).

Anyone have any ideas? Thanks for reading.

I haven't posted many questions myself, and yet by looking through the forums, you guys have already taught me sooo much by helping others.

---

### Post by heimo on 2005-07-25
I haven't done it myself, but what you're looking for is called shaper or "traffic shaper", something like this:
[http://packages.ubuntu.com/hoary/net/wondershaper](http://packages.ubuntu.com/hoary/net/wondershaper)

Hopefully this gets you closer to solution.

---

### Post by GreyFox503 on 2005-07-27
Thanks, heimo!

I had already tried searching the package manager (Synaptic) for "bandwidth limiter" and other similar terms, but got no results.  A search for "shaper" though turns up a few good ones.

I used to use a program called "net limiter" for windows, and i was not familiar with the term "shaper" in the networking context.

---

### Post by GreyFox503 on 2005-07-27
Update for future reference:

I installed "wondershaper", and its a command-line tool used to regulate bandwidth (upstream & down)  The instructions made it seem really complicated, but to use it, all you have to do is issue a command like:

```
sudo wondershaper eth0 3000 2048
```

for limiting downstream to 3000 kbps and upstream to 2048 kbps. (and yes, thats in kiloBITS, not kiloBYTES)

After testing my connection, this program seems to work pretty well, but not extremely precisely, though that's fine for my needs.

You can configure it to take effect on startup, but I didnt need that.

---

