---
title: "VNC Not Updating Screen?"
date: 2006-02-18
forum: Absolute Beginner Talk
---

### Post by simon0t7 on 2006-02-18
Hi,

I'm very new to Ubuntu and I got it up and running and starting using the VNC build into the OS.  I've worked with RealVNC on my windows machine and they are incredible fast over my home network and over internet (from school to home) regardless of what internet activity I had going on.  When I try to VNC into my ubuntu machine, it's responsive but the screen doesn't exactly update everything.  Here's a screen shot of how the package manager looks like when I open it:

[[IMG]http://img467.imageshack.us/img467/2914/vnc4td.th.jpg[/IMG]](http://img467.imageshack.us/my.php?image=vnc4td.jpg)

It's not because of the screen saver.  I closed the package manager, opened up terminal and here's a second screen shot:

[[IMG]http://img98.imageshack.us/img98/8089/vnc20wg.th.jpg[/IMG]](http://img98.imageshack.us/my.php?image=vnc20wg.jpg)

any ideas what I can do to make it refresh the entire screen as opposed to places where it wants?

Thanks!



System specs:
P4 3.0E no overclocking
2*256 MB memory in dual channel no overclocking  (could this be the problem?)
HIS X700
120 GB IDE 7200 RPM hard drive 2MB

---

### Post by Pragmatist on 2006-03-11
What happens if you just have no windows open, just the desktop.  Then what if you have just one window open; I would test it in this fashion and gives us your results.

---

### Post by Woody@N87 on 2007-07-31
Ever get a solution to this?  I have RealVNC, client on windows, turn on Remote desktop on the ubuntu machine and have the same problem.  I've tried every configuration on the Ubuntu machine that I can think of and it doesn't change.  When I sign in I see whatever is on the screen but the client side will not update.  If the screen saver is on that will not change either, yet, I've been able to wake two other computers up with the RealVNC hook up.

I've even run the effected computer side by side to with the client to watch.  The server (ubuntu side) reacts to mouse clicks and the screen changes (for example changing websites on firefox) but the client side screen never updates.

Thought it might be a version issue.  Installed ubuntu from the same CD onto another computer and that one works fine with the exact same set up. (using it now in fact).

Any ideas?  I want it to work on that particular machine to make it the permanent gateway to my home network, it has the most horsepower.

---

### Post by Pragmatist on 2007-07-31
Have you read any of these yet?
[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=vnc&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=vnc&titlesearch=Titles)

It sounds to me like an issue with X and VNC

---

### Post by Woody@N87 on 2007-07-31
No, I haven't but I just looked at some of it and it appears way over my head.  I'd have to do without before I got into all that.

I don't see what the difference between the installs could be, I did everything exactly the same.

---

### Post by Ek0nomik on 2007-07-31
The built in VNC software in Ubuntu is rather bleak.

Try following this:

[http://ubuntuforums.org/showpost.php?p=2757451&postcount=6](http://ubuntuforums.org/showpost.php?p=2757451&postcount=6)

You could also use SSH instead of VNC to control files or even run programs remotely.

---

### Post by fastpakr on 2007-07-31
Woody, are you running Desktop Effects/Compiz/Beryl?

---

### Post by Woody@N87 on 2007-07-31
I believe you may have something here, that's one thing I did on the machine in question that I didn't do on the other two machines.  I enabled a "driver" if I recall to allow desktop effects.  I don't recall seeing the word Beryl anywhere though.

 I just went into that section and disabled the effects themselves (workspace on a cube, Windows wobble when moved), that didn't help.  I don't see any way to disable the aforementioned enabled driver, is there a way you know of?

...and thanks for the direction on this...

---

### Post by fastpakr on 2007-07-31
Have you tried running VNC again since disabling desktop effects?  My guess is that you were prompted to enable the restricted driver for your video card when you enabled it, but that isn't really an issue here.  I think there's a workaround for making desktop effects work through VNC, but I've never fiddled with it.  What may work for you is creating a VNC server on display 1 (separate virtual session) so you can connect remotely to use the machine but still have it running effects on display 0 (the attached monitor).

---

### Post by Woody@N87 on 2007-08-01
I have turned off the effects and that didn't do anything, I think disabling the driver somehow would be the way to make it work.

I appreciate all the help and ideas, I think you've zeroed in on the problem.  It might be easier  (and faster) for me as the newbie that I am to simply back up my files to the external, format the drive and re-install the operating system.

  I've done very little customization at this point.

  Thanks again, the available help and great brainstorming is what keeps me going with this project.

   Woody

---

### Post by fastpakr on 2007-08-01
I really don't think the driver is the problem here.  Just so I'm clear - you can connect to the VNC session, but once you're there you just get an initial shot of the screen with no updates?  That really sounds like some kind of effect is running that's keeping it from sending the screen updates.

---

### Post by Woody@N87 on 2007-08-04
Just in case anyone else is following this.  I have re-installed the OS and run the updates.  I didn't enable the driver and I'm writing this note via VNC so, I'm guessing that enabling the driver was the issue.

Thanks Again,
         Woody

---

### Post by fastpakr on 2007-08-04
What driver are you currently using?

---

### Post by foxer on 2007-08-04
no need to disable the driver.  Just disable the desktop effect.  This work for me.

---

### Post by crisco96 on 2007-09-12
Just in case anyone else has this issue.  I resolved it by going to System->Administration->Restricted Drivers Manger and disabled my ATI accelerated graphics driver.  After the restart vnc worked properly.

---

### Post by Augi on 2007-11-06
Just wanted to confirm that disabling desktop effects solves the problem, in some cases it seems. I had the same issue on my box until that was done.

Regards.

---

### Post by peterc_ubun on 2008-02-28
Just want to let Fedora Core users out there that might stumble on this thread know that disabling Desktop Effects in FC7 solved my issue with Vino/VNC's non-responsiveness.

Thanks all for posting on this topic!

---

