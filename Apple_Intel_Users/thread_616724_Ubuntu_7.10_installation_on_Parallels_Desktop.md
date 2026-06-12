---
title: "Ubuntu 7.10 installation on Parallels Desktop"
date: 2007-11-18
forum: Apple Intel Users
---

### Post by jose mourinho on 2007-11-18
So I've got the installation CD, and I try to install it on Parallels Desktop on my Macbook. Soon after starting the installation, the Parallels window starts resizing over and over, and finally I get a message like "The screen has reset 6 times over the past 90 seconds, something is probably wrong. Waiting 2 minutes to try again on display :0" -- not exactly that, but something similar. 

Any help would be greatly appreciated.

---

### Post by helpmepleaseiknownothing on 2007-11-19
I've been having the exact same problem.  No idea what to do.  It's kind of annoying.

---

### Post by helpmepleaseiknownothing on 2007-11-19
Although, I downloaded the ISO and was installing from that.  I don't have a physical CD with Ubuntu on it.  Don't know if that matters, but anyway, anybody who knows how to fix this, please help.

---

### Post by cyberdork33 on 2007-11-19
This is a parallels issue...
[http://forum.parallels.com/showthread.php?t=17069](http://forum.parallels.com/showthread.php?t=17069)
[http://kb.parallels.com/entry/32/568/](http://kb.parallels.com/entry/32/568/)

---

### Post by helpmepleaseiknownothing on 2007-11-19
Well those don't seem to help much.  I don't know how to uninstall "parallels tools" whatever that is.  Also, no idea how to edit the "xorg" file.  If you could give a step-by-step that would be extremely helpful.

---

### Post by cyberdork33 on 2007-11-19
> **helpmepleaseiknownothing said:**
> Well those don't seem to help much.  I don't know how to uninstall "parallels tools" whatever that is.  Also, no idea how to edit the "xorg" file.  If you could give a step-by-step that would be extremely helpful.

The second link is a step by step instruction to install Ubuntu 7.10 in parallels.

---

### Post by helpmepleaseiknownothing on 2007-11-19
I know, and I appreciate that you took the time to find it, but I guess I'm just a complete noob.  I read it and I don't know what half of that means.  How do I get to the "Xorg" file to edit it?  Is it in the ISO, or is it something I do in Parallels while booting?  I tried the first step and I don't see anything about a "Xorg" file after that.  I guess this is more suited to the Parallels forums.  Didn't mean to sound like a jerk in the last post, just reread it and realized it kind of came across that way.

---

### Post by cyberdork33 on 2007-11-19
> **helpmepleaseiknownothing said:**
> I know, and I appreciate that you took the time to find it, but I guess I'm just a complete noob.  I read it and I don't know what half of that means.  How do I get to the "Xorg" file to edit it?  Is it in the ISO, or is it something I do in Parallels while booting?  I tried the first step and I don't see anything about a "Xorg" file after that.  I guess this is more suited to the Parallels forums.  Didn't mean to sound like a jerk in the last post, just reread it and realized it kind of came across that way.

The first step is that which you use to actually get the Ubuntu disc (or image) to boot. On the boot screen, you have to hit F6, type "Single" then press enter to continue.

Next, after the system starts, (I am guessing you will get a commandline, but if not you can lauch a terminal from the menu), then use the commands listed to do other steps...
```
[FONT=Tahoma][SIZE=2]pico /etc/X11/xorg.conf
```
This will open the xorg.conf file in an editor where you can make the noted change.

all the terminal/commandline commands are in ' '. 

If you do not own parallels yet (just trying it out) i would suggest using vmware fusion as they seem to better support linux users.
[/SIZE][/FONT]

---

### Post by helpmepleaseiknownothing on 2007-11-19
Something ain't right.  I hit F6, typed single, it started booting, then came to a black screen with a cursor, which I'm guessing is the command line.  I typed in 'pico /etc/X11/xorg.conf' and it said "No such file or directory."  This is what happened before my last post.  I guess I should have included that...  I guess I was doing everything right, but I thought that was an impossibility.  Damn computers.  I'll try VMware I guess.

---

### Post by helpmepleaseiknownothing on 2007-11-19
Nevermind!  I didn't realize there is a space in "pico /etc..."  Pico SPACE slash etc.  I entered that, and it worked.  Of course then I had very little idea of what to do.  I don't think it worked since it started booting but then said it was running in low graphics mode because the graphics card couldn't be detected properly.  I'll try it again.  The format of how to enter the subsections is a bit confusing.

---

### Post by cyberdork33 on 2007-11-19
> **helpmepleaseiknownothing said:**
> Nevermind!  I didn't realize there is a space in "pico /etc..."  Pico SPACE slash etc.  I entered that, and it worked.  Of course then I had very little idea of what to do.  I don't think it worked since it started booting but then said it was running in low graphics mode because the graphics card couldn't be detected properly.  I'll try it again.  The format of how to enter the subsections is a bit confusing.

the low graphics mode is probably ok until you can get the parallels tools installed (can be done from the menu). You might have more luck find information about this in the VM forum:
[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

---

