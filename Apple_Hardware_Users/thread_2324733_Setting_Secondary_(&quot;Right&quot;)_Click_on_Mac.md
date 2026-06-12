---
title: "Setting Secondary (&quot;Right&quot;) Click on Macbook Pro Trackpad - Right Bottom Corner"
date: 2016-05-16
forum: Apple Hardware Users
---

### Post by mishaal2 on 2016-05-16
Hello,

I was having issues with my computer so I recently re-installed Ubuntu. Everything works quite well but I cannot figure out one major thing: secondary click setting. 

I know from reading around that I can use a two-finger click for my secondary click (i.e. right click) - but I find this to be very inconvenient. I want to be able to single-click on the bottom right corner area of my Macbook Pro Touch Pad and have that act as the secondary click. My research has lead me to think that this should be accomplished by editing the /usr/share/X11/xorg.conf.d/50-synaptics.conf file, but I can't figure out exactly how to do this.

I am quite sure that this behavior can be accomplished as I believe before I re-installed Ubuntu, I had it set up like this. If someone could please help, that would be really appreciated.Thank you!

---

### Post by howefield on 2016-05-16
Thread moved to the "*Apple Hardware Users*" forum for better support.

---

### Post by mishaal2 on 2016-05-19
I think I found a solution (Though I am not sure if it is the "best" one), using the following commands:

```

$ synclient RightButtonAreaLeft=3068
$ synclient RightButtonAreaRight=0
$ synclient RightButtonAreaTop=4326
$ synclient RightButtonAreaBottom=0

```

The numbers can be changed depending on desired area, of course.

---

