---
title: "[SOLVED] G4 plasma screen of death"
date: 2008-04-06
forum: Apple PPC Users
---

### Post by mikeym on 2008-04-06
Hi,

I've been trying to install XUbuntu on my G4 titanium PPC and I'm stuck. I got the liveCD to boot eventually and install by using *live-nosplash-powerpc break=top* and *modprobe ide-core*. 

However once I had installed it I was in exactly the same position that it would load and I would get a white screen that would fade in a plasma like effect. I have tried every suggestion I can find about it not loading due to the screen on a PPC. 

I've dissabled GDM, tried append="nosplash" in yaboot.conf, edited /etc/X11/xorg.conf to have the VSync and Vsycn of my model's LCD screen, added a reference to each pixel depth to tell it to use 1280x856. 

Any ideas?

---

### Post by stream303 on 2008-04-06
After changing and saving anything in /etc/yaboot.conf, did you make the system aware of that change with:

```
sudo ybin -v -C /etc/yaboot.conf
```

---

### Post by mikeym on 2008-04-06
Yes but I was running it from the live CD so I had to type 
```

/media/disk/usr/sbin/ybin -C /media/disk/etc/yaboot.conf
```

The thing is I can't even get to the console - in fact I've never been to the console on the PPC. If I try it from the live CD I get the same plasma screen of death.

---

### Post by stream303 on 2008-04-06
Ok, looks like you've got the faq, but I'll toss it out for lurkers:
[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

so you've tried
live-nosplash-powerpc
or
live-nosplash-powerpc  video=ofonly
or
live-nosplash-powerpc video=ofonly break=top

as your kernel parameters and none of them worked with the live-cd to get into virtual terminals?

I might be tempted to also try the "alternate" non-live install images ....

---

### Post by mikeym on 2008-04-06
Yes I've been through known issues and every thread I can find. It does seem to differer from most other people's problems. I've only seen a couple that mention the fade effect that can be seen.

So for the other stuff

*live-nosplash-powerpc* = plasma screen of death

*live-nosplash-powerpc video=ofonl*y = black screen where the PSOD normally lives then the PSOD

*live-nosplash-powerpc video=ofonly break=top* = busybox which takes you to PSOD unless you type *modprobe ide-core*. This loads you into the live CD, but this techniques does not work post install!

So I can get to busybox on the post install boot but not to X or the command. Although it is worth mentioning that it has loaded once. I don't know how or what I typed and I have never been able to reproduce it. 

Oh yes there seems to be 2 parts to the PSOD on some settings it just seems to stop there other times it appears to keep loading and sometimes changes resolution or something because it will flicker and you can get stray pixels on it.

---

### Post by stream303 on 2008-04-06
Hmm.  If you can get to busybox, and you do a modprobe-ide, then exit, if you walk away for about a half-hour, do you get anything?  Sounds crazy, but some others have mentioned that they had to wait an unreasonable amount of time after busybox.  Which they then later fixed by doing the initramfs -u once all their patience ran out... :)

I wonder if your machine is using an R128 card?  Which computer do you have, we might be able to suss out some more gotcha's:

[http://www.everymac.com/systems/apple/powerbook_g4/index-powerbook-g4.html](http://www.everymac.com/systems/apple/powerbook_g4/index-powerbook-g4.html)

I know I keep harping on it, but have you tried the "alternate" non-live install image just for comparison?  ...running and ducking ... :)

---

### Post by mikeym on 2008-04-06
Hi,

Thanks for the reply. [Here's]("http://www.welovemacs.com/sppog41g15tm.html") my computer's spec. It appears to use a R9000 which is a bit odd as I'm sure my *xorg.conf* file had references to the R128. 

I'm trying out the alternate CD as we speak.

---

### Post by mikeym on 2008-04-06
Wow! What a difference.

It did stick once - when I booted - at the splash screen but I'm waited and it took me to busybox where  I could type *modprobe ide-core* and *exit*. Not at all the same problem I was having with the PSOD. 

I'm now trying to fix the boot thing and allow mac-like mouse presses with the following 2 posts:

[http://ubuntuforums.org/showpost.php?p=4546107&postcount=1](http://ubuntuforums.org/showpost.php?p=4546107&postcount=1)
[http://ubuntuforums.org/showpost.php?p=2797267&postcount=8](http://ubuntuforums.org/showpost.php?p=2797267&postcount=8)

Thanks again! :)

---

