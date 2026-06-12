---
title: "Dual Monitors?"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by Touch.Code on 2007-02-16
Hey,

I have this problem with my laptop screen, and sometimes the backlight goes off. So when it does, I plug in my second monitor. Now normally in Win Xp, it recognizes straight away and I can see! But in Ubuntu 6.10 I can only see lots of coloured blocks/squares.

I have tried changing my screen resolution, through the Screen Resolution tool, which took about 10 mins because I can barely see the screen and I have also tried Restarting X (Ctrl+Alt+Bkspc). Nothing worked.

Is there a simple way of doing it? Baring in mind I can get to the terminal but can change and .conf settings because I cant see that well.

Thanks,
Touch

---

### Post by Touch.Code on 2007-02-16
BUMP? I really need help with this.

---

### Post by bodhi.zazen on 2007-02-16
See if any of this helps.

Laptop monitors: (see also Dual Monitors)
	Best: [http://ozlabs.org/~jk/docs/mergefb/](http://ozlabs.org/~jk/docs/mergefb/)
	xorg.conf: [http://www.linux-on-laptops.com/forum/showthread.php?p=1253](http://www.linux-on-laptops.com/forum/showthread.php?p=1253)

	Presentations: [http://www.astro.umd.edu/~teuben/linux/laptop-display.html](http://www.astro.umd.edu/~teuben/linux/laptop-display.html)

	See also: [http://ubuntuforums.org/showthread.php?&t=237640](http://ubuntuforums.org/showthread.php?&t=237640)

	[http://ubuntuforums.org/showthread.php?&t=298075](http://ubuntuforums.org/showthread.php?&t=298075)

	Dual monitors, Ubuntu thread:
		[http://ubuntuforums.org/showthread.php?&t=308673](http://ubuntuforums.org/showthread.php?&t=308673)

Also it may be helpful if you could post details regarding your external monitor and xorg.conf.

---

### Post by Touch.Code on 2007-02-17
I could tell you my xorg.conf settings f I could see my laptop screen. What I want to do, is display my laptop screen on my External Screen, not extend my desktop.

---

### Post by bodhi.zazen on 2007-02-17
The first link is most helpful ....

You could also look at this :

[http://www.ubuntuforums.org/showthread.php?t=240150](http://www.ubuntuforums.org/showthread.php?t=240150)

---

### Post by Touch.Code on 2007-02-17
Thanks, so that will allow me to view my current desktop on two monitors?

---

### Post by bodhi.zazen on 2007-02-17
The fist link has been most helpful to the majority of people ...

The second link was to a working xorg.conf, but I see it is broken.

Try this one : [http://bmrc.berkeley.edu/people/chaffee/xfree86_cirrus.html](http://bmrc.berkeley.edu/people/chaffee/xfree86_cirrus.html)

You will NOT be able to cut and paste these xorg.conf to your laptop, but look at the monitor and server sections ;)

The last link I gave you is for independent monitors. I gave that one to you because you indicated you did not want twinview ;)

What you likely need to do is to add information to xorg.conf regarding you external monitor ...

Unfortunately I do not know of any automated mechanism to do this :(

Back up you current xogr.conf ...

Give it a try

If yo have problems, post your xorg.conf ...

---

