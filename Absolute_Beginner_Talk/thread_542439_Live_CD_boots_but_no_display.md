---
title: "Live CD boots but no display"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by BeerMit on 2007-09-03
my post in another thread got plenty of views but no help
so heres to hoping this one brings me fruition
honestly i know very little about linux

im trying out the 7.04 'desktop' version of ubuntu
the Live CD
i can get it boot fine
i know this because i can hear it boot
however my display is completely blank when i hear it
but before that point i can see it loading the drivers and whatnot

someone please help
ive checked the image, its fine
ive burned the disc at a low speed
ive used the noapic nolapic commands (not sure what they do)
ive tried pci=acpi (not sure what that does either)
please help, im losing my mind here

---

### Post by splintercellguy on 2007-09-03
Have you tried booting in Safe Graphics mode?

---

### Post by BeerMit on 2007-09-04
ive tried that too
ive also tried setting my resolution to 640 x 480 x 16 and x 32

---

### Post by Crafty Kisses on 2007-09-05
> **BeerMit said:**
> ive tried that too
ive also tried setting my resolution to 640 x 480 x 16 and x 32

You can use the alternate installer disc if you are trying to install Ubuntu.

---

### Post by BeerMit on 2007-09-05
I was about to when i solved the problem
I figured out that as soon as Ubuntu loaded fully, the video output would switch to my second video card
So it became simply a matter of switching my video cable between cards when i load Ubuntu
Which is working great by the way :-)

Except for a new problem that has arisen
After getting it installed and updated
i decided to get up to date drivers
The whole process went smoothly until i rebooted
Now X Server wont start
And being the Linux noob that i am
i have no idea how to get in there and reconfigure X server
all i know ho to do is change directories :-/

insight please?

---

