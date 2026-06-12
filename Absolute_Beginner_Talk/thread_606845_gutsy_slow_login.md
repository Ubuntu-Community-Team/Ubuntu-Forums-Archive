---
title: "gutsy slow login"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-11-08
my boot up is great :D
14seconds or less,

but when it logs me in i hear the music, then a long wait..

much longer than feisty,

any ideas what would be causing it?

i dont have many sessions running, actually 2.

---

### Post by FuturePilot on 2007-11-08
I've noticed it's a bit longer too. It's because there's a lot more stuff being run on login than there was in Feisty. Check your Sessions menu. You'll see what I mean.

---

### Post by snickers295 on 2007-11-08
> **Bob Barker said:**
> I've noticed it's a bit longer too. It's because there's a lot more stuff being run on login than there was in Feisty. Check your Sessions menu. You'll see what I mean.
I agree with you.
i think these compiz like stuff help plenty to slow it down.

---

### Post by sports fan Matt on 2007-11-08
My startup is about a minute and a half..How did you tweak it to 14 seconds or less amd is it complicated..I'd like to know how to reduce the startup time, if ya'll do not mind:)

---

### Post by skymera on 2007-11-08
i got Boot Up manager

and foolowed a tut on here just disabled loads of stuff.

tada!

[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

but im going to make a new custom kernel to my spec, the generic one has so much stuff we dont need, sloooow.

---

### Post by snickers295 on 2007-11-08
my boot up takes about 30 seconds and i didn't tweak it about.

---

### Post by skymera on 2007-11-08
yeah im not on about boot up.

im on about login

---

### Post by bcdeck on 2007-11-10
On startup I get 2 minutes 30 seconds of blank screen between the time grub starts and the "please wait" flashes up and the login screen appears. It's driving me nuts.

I'm using Gutsy and Kubuntu.

EDIT: I had tried changing my splash screen resolution via /etc/usplash.conf and building a new profile with sudo update-usplash-theme usplash-theme-ubuntu. 
THIS SLOWED ME DOWN CONSIDERABLY!!! I changed the resolution back to 1024x768 (what it had been before) and it cut two minutes off my wait time.

---

### Post by snickers295 on 2007-11-11
ya upgrading your os can do that, think a bout me using windows 98 on a old computer then installing xp. now that will slow you down

---

### Post by skymera on 2007-11-11
but its not win98 tho..

its 6month difference, not 7years or so.

---

### Post by Partyboi2 on 2007-11-11
I was having the same problem, but ended up re-installing and that worked for me, but that doesn't work for everyone. There is another post about this problem
[http://ubuntuforums.org/showthread.php?t=585635](http://ubuntuforums.org/showthread.php?t=585635) 
Where different people have been trying to troubleshoot this problem.

---

### Post by bcdeck on 2007-11-12
Interesting thing is, the appearance of my login screen didn't change when I tried the suggested method for changing resolution.

---

