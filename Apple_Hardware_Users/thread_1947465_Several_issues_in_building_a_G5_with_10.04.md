---
title: "Several issues in building a G5 with 10.04"
date: 2012-03-26
forum: Apple Hardware Users
---

### Post by jamesisin on 2012-03-26
I have built a G5 with 10.04 and there are several things which aren't working as I would have expected them to work.

One of the things I do every time I build an Ubuntu box is run through this very excellent HowTo so as to get a bunch of audio and video things working best:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

The trouble is that many of the steps are not working for this machine.  For instance the repository for medibuntu:

```
W: Failed to fetch http://packages.medibuntu.org/dists/lucid/Release  Unable to find expected entry  free/binary-powerpc/Packages in Meta-index file (malformed Release file?)
```

I have a similar issue when I attempt to add the repository for Opera:

[http://jamesisin.com/a_high-tech_blech/index.php/2008/09/add-opera-to-ubuntus-update-manager-synaptic/](http://jamesisin.com/a_high-tech_blech/index.php/2008/09/add-opera-to-ubuntus-update-manager-synaptic/)

Gnome-Do is crashing if I touch the search box with the mouse:

[http://ubuntuforums.org/showthread.php?t=1943677](http://ubuntuforums.org/showthread.php?t=1943677)

I can't get Compositing to work with the installed video card:

[http://ubuntuforums.org/showthread.php?t=1943665](http://ubuntuforums.org/showthread.php?t=1943665)

Great hunk of hardware currently running at maybe a 50% handicap.

What can I do to make it run more fully?

---

### Post by svtguy88 on 2012-03-26
I replied to your other thread.  Why are you using 10.04?  12.04 will be out very soon, and even the Beta is pretty solid (or so I assume...the last PPC build I installed was an alpha on my G4 tower).

I would just install 12.04 and see what works...10.04 is getting old...

---

### Post by jamesisin on 2012-03-26
I don't imagine the version (12 or 10) is what is causing the repository problems and that's the largest issue of those listed above.

(I replied to the other post as well.  Thanks.)

---

### Post by svtguy88 on 2012-03-27
12.04 may not have been officially released, but as someone who has fiddled with Ubuntu/Lubuntu/Debian on PowerPC hardware a number of times over the passed few years, I can say that 12.04 has had the best "out of the box" support that I've seen.

I would seriously consider downloading the Beta (actually, I think it's at beta II now) of Lubuntu for PowerPC and see what happens.  10.04 is old, and though I can't comment on the specifics, I've noticed MUCH better video support with the newer versions (I used to have to make a pretty complex Xorg.conf to get video at all on my G4/Geforce 6200, 12.04 doesn't need a Xorg.conf at all for my setup....).

If you really want to stick with 10.04, give us the output of "lspci" to get things started...and maybe "glxinfo" too (it's output is pretty big.  The lines I'm looking for are OpenGL vendor, OpenGL renderer and OpenGL version)....you'll need mesa-utils or something like that installed to run glxinfo.

---

### Post by jamesisin on 2012-04-21
pkmgarf - I posted that output into the thread I made for the video problem:

[http://ubuntuforums.org/showthread.php?p=11863031#post11863031](http://ubuntuforums.org/showthread.php?p=11863031#post11863031)

---

