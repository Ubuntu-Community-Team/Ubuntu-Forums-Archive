---
title: "magenta greeting screen after &quot;switch user&quot;"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by redseventyseven on 2007-12-20
Hi all

this is my first ever ubuntu forums post! hopefully not my last :)

i've had ubuntu for a couple of weeks, got most things working fine thanks to all the howto's and forums.

i've still got one problem though - when i use fast user switching, the login screen has this kind of magenta filter on it (all black colours turn bright magenta for example) and when i log in as the new user (or the same as the one before) the screen stays that way.

bizarrely i have a dual monitor setup with an LG flatscreen (the main monitor) and an old tv (secondary monitor) and the colours on the TV are fine!

has anyone seen something like this before? can anyone help?

thanks!

---

### Post by nowshining on 2007-12-20
have u tried turning off compiz - right click change background (on the desktop) last tab and turn that off and try again.

---

### Post by redseventyseven on 2007-12-21
> **nowshining said:**
> have u tried turning off compiz - right click change background (on the desktop) last tab and turn that off and try again.

hi nowshining,

i tried that and it made no difference - still getting the magenta filter effect!

---

### Post by nowshining on 2007-12-21
ah what videocard to u have?

---

### Post by redseventyseven on 2007-12-24
> **nowshining said:**
> ah what videocard to u have?
I have an NVidia GeForce FX 5200.

---

### Post by redseventyseven on 2008-01-15
OK, quick update:

I tried using a different monitor (an old Dell CRT box) and still the same problem occurred.

I'm in the middle of trying to get a video up on youtube which shows exactly what happens.

I've tried googling this problem and haven't managed to come up with anything (if anyone has more success, please let me know what you typed in!). I'm fairly new to using linux of any form, so if there are any "standard" diagnostic tools or screen outputs I should be offering to try to solve problems like this, please let me know what they are and how I can get them!

Many thanks!

---

### Post by williumbillium on 2008-01-22
It seems I am having the same problem.  I also have a very similar set up to the OPnv.  Here's my info:

Gutsy (KDE)
nVidia GeForce FX5200
Dual screen setup (ViewSonic LCD + TV in "separate X screen" mode, no xinerama)
nvidia-glx-new video driver

My situation is I upgraded to gutsy over the weekend and that's when the problem started.

Like the OP, when I switch to a new user, the login screen has a magenta cast and after logging in, the magenta cast is still present.  The symptoms are not present on the TV output.

Some additional info:

If I switch back to the 1st user, it also has the magenta cast.  Restarting X for the 1st user gave the 2nd user a blue cast.  Restarting X for the 2nd user didn't make any difference.

Anyone have any ideas on how to procede? would my xorg config be useful? X logs or anything else?

Thanks.

---

### Post by williumbillium on 2008-01-25
Well, all I've got so far is that disabling the second monitor (tv-out/svideo) in xorg.conf stops this from happening.

---

### Post by redseventyseven on 2008-02-05
All I can add at this stage is that having switched to PCLinuxOS the problem still persists.

---

### Post by redseventyseven on 2008-02-18
Another update.

I've upgraded my second monitor to a standard DVI monitor (which uses the DVI output rather than the S-VIDEO output of my graphics card).

Magically the problem seems to have disappeared! Fast user switching from one user to a second user and back again now works fine.

---

