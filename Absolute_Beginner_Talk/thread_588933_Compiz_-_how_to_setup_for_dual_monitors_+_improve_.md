---
title: "Compiz - how to setup for dual monitors + improve performance ..."
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-10-23
I'm running two monitors on an nvidia setup too. The card is a geForce 6250,

I changed to Twinview from nvidia-settings and I get the visual effects on both monitors - independent cubes on each monitor.

But, when I rotate the cubes, the windows on the face of the cubes is not exactly right.  Windows on the right cube appear on the left cube during the rotation. 

Beryl worked correctly - and it seems Beryl was quite a bit faster at rotating the cube but I do remember setting some parameters to tweak Beryl.

Anyone have an idea how to a) fix the cube when using dual monitors and b) tweak Compiz for performance?

Thanks

Carl

---

### Post by Phesto on 2007-11-16
I am experiencing the same issue. Beryl would rotate as one rectangular box across both monitors but now with gutsy the rotation happens by two separate cubes on each monitor but yet with linked desktops. For example two virtual desktops creates a cube and 4 virtual desktops creates an octagon. I have yet to find a solution either.

--edit found this post
[http://ubuntuforums.org/showthread.php?t=482995&highlight=cube+rotation+dual+monitor](http://ubuntuforums.org/showthread.php?t=482995&highlight=cube+rotation+dual+monitor)

---

### Post by nPoc on 2008-02-18
Have you guys found a solution for this yet?  I'm really starting to get irritated. The cube was working great under beryl with 7.04.  I hate this weird *** octagon thing.

---

### Post by nPoc on 2008-02-18
Here's the solution

1.  Open Synaptic and install compizconfig-settings-manager

2.  After installing open System->Preferences->Advanced Desktop Effects and Settings

3.  Click Desktop Cube.

4,  Set Multi Output Mode to "On big Cube".


YAY!

---

