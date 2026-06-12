---
title: "Cannot isntall Ubuntu"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by someguy91 on 2007-06-23
When I put in the live CD.. everything works fine... it gives me the screen of choices.. to install.. start.. check.. what not.

I select install and the ubuntu logo pops up with the scrolling progress bar... it gets to the point where the entire progress bar loads... and then my monitor says "Entering Power Save" and I can't see anything that happens afterwards.. I don't know what is causing this.

I have an R520 class video card.. DVI connection.. tried both.. to no avail..

A little history.. I just installed windows vista 64.. there are 3 partitions i put in my computer.. 1 for vista 1 for ubuntu and 1 for data.. I put vista in the 2nd partition...

my msn is [email]psychosomatica01@hotmail.com[/email] if you would like to do this over msn... or replying here is fine too

thanks in advance.

---

### Post by DBStevens on 2007-06-23
Have you actully tried to run under the liveCD to see if it works with your hardware.  

That is have you used the start option?

Your monitor is saying it isn't seeing anything worth staying awake for happening within its timeout windows and then it goes into power save mode.

---

### Post by pmshirey on 2007-06-23
Go to:[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and click the box that says > Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer.. Then start the download, that should work. If not please feel free to e-mail me at [EMAIL="pmshirey@insightbb.com"]pmshirey@insightbb.com[/EMAIL]

---

### Post by pmshirey on 2007-06-23
> I put vista in the 2nd partition...Oh, you put vista in 2nd partition...Windows, has to be the 1st partition...

---

### Post by wpshooter on 2007-06-23
> **someguy91 said:**
> When I put in the live CD.. everything works fine... it gives me the screen of choices.. to install.. start.. check.. what not.

I select install and the ubuntu logo pops up with the scrolling progress bar... it gets to the point where the entire progress bar loads... and then my monitor says "Entering Power Save" and I can't see anything that happens afterwards.. I don't know what is causing this.

I have an R520 class video card.. DVI connection.. tried both.. to no avail..

A little history.. I just installed windows vista 64.. there are 3 partitions i put in my computer.. 1 for vista 1 for ubuntu and 1 for data.. I put vista in the 2nd partition...

my msn is [email]psychosomatica01@hotmail.com[/email] if you would like to do this over msn... or replying here is fine too

thanks in advance.

Have you checked the integrity of your Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

Have you tried starting in safe graphics mode ?

---

### Post by nutz on 2007-06-23
I had the same issue; fixed it by switching to the VGA. For some reason my DVI doesn't work under Ubuntu. As soon as I switched to use the VGA instead it runs fine...

This is with an nvidia card but it sounds related.

---

### Post by someguy91 on 2007-06-24
> **DBStevens said:**
> Have you actully tried to run under the liveCD to see if it works with your hardware.  

That is have you used the start option?

Your monitor is saying it isn't seeing anything worth staying awake for happening within its timeout windows and then it goes into power save mode.

Well when I boot up the CD it has a "start or install" option and then there's a "safe graphics" option and then the other options. When I select "start or install" OR "safe graphics" the ubuntu logo comes up... then an orange bar goes back and forth.. after a while.. it becomes a progress bar.. when the progress bar finishes loading the monitor enters power save mode.

> **pmshirey said:**
> Go to:[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and click the box that says . Then start the download, that should work. If not please feel free to e-mail me at [EMAIL="pmshirey@insightbb.com"]pmshirey@insightbb.com[/EMAIL]

would a text based version make a difference?

> **pmshirey said:**
> Oh, you put vista in 2nd partition...Windows, has to be the 1st partition...

uh really?

> **wpshooter said:**
> Have you checked the integrity of your Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

Have you tried starting in safe graphics mode ?

yes and yes

> **nutz said:**
> I had the same issue; fixed it by switching to the VGA. For some reason my DVI doesn't work under Ubuntu. As soon as I switched to use the VGA instead it runs fine...

This is with an nvidia card but it sounds related.

both my outputs are DVI-D... my card is a 1900xt... Processor E4300... motherboard p5k... I would think it's compatible... I'll plug in the VGA adapted and see what's up.

Any other suggestions guys? I've been looking to use Ubuntu for a while... :/

---

### Post by nutz on 2007-06-24
> **someguy91 said:**
> Well when I boot up the CD it has a "start or install" option and then there's a "safe graphics" option and then the other options. When I select "start or install" OR "safe graphics" the ubuntu logo comes up... then an orange bar goes back and forth.. after a while.. it becomes a progress bar.. when the progress bar finishes loading the monitor enters power save mode.



would a text based version make a difference?



uh really?



yes and yes



both my outputs are DVI-D... my card is a 1900xt... Processor E4300... motherboard p5k... I would think it's compatible... I'll plug in the VGA adapted and see what's up.

Any other suggestions guys? I've been looking to use Ubuntu for a while... :/

What I meant to say is my DVI doesn't work during the install but the VGA does. I can switch back to the DVI after it is install and my driver is loaded...

---

### Post by oilchangeguy on 2007-06-24
these two threads [http://ubuntuforums.org/showthread.php?p=2905803#post2905803](http://ubuntuforums.org/showthread.php?p=2905803#post2905803) need to be combined. the user is asking almost the same question in two different threads.

---

### Post by BobCFC on 2007-06-24
When I had similar problems it helped to change boot options from splash to nosplash and delete quiet so I could see more error messages.

Also since XP you can install windows anywhere.  98 was fussy but not anymore aslong as ntbootloader is on C:

---

### Post by dpar on 2007-06-24
I think Nutz is pretty close to your answer. I had the same problem when I first installed Linux, but once I got the proper Nvidia drivers installed my monitor started acting right.

---

### Post by nutz on 2007-06-24
Just try it; do the install in VGA then after you load your video driver you can switch back to the DVI...

---

### Post by someguy91 on 2007-06-24
Thanks Nutz you were right.

However.. slight problem. I installed using alternate CD.. and then went alright. The issue is that when I still need VGA to boot into Ubuntu... do i have to install the closed-source drivers to get it to work?

---

### Post by nutz on 2007-06-24
> **someguy91 said:**
> Thanks Nutz you were right.

However.. slight problem. I installed using alternate CD.. and then went alright. The issue is that when I still need VGA to boot into Ubuntu... do i have to install the closed-source drivers to get it to work?

Yes unfortunately. I have not been able to use the DVI without them.

---

