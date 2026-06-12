---
title: "moving an object has a major delay"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by k9brand on 2006-08-26
When I start my computer and log in, things seem very slow.  If I grab a window on the desktop and try to move it around, it will take 15 to 20 seconds to complete the move.  This happens when moving, scrolling, selecting things in a menu, etc.

When I start XGL / Compiz, everything works fine, but I don't want to use XGL/Compiz all the time...I'm using Nvidia drivers, gnome, I have a decent enough computer.

Can anybody help me diagnose the issue?  Here's what I have tried so far:

1.  I restored my backup xorg.conf file 
2.  I put back some changes I had made to gconf-editor
3.  I checked TOP and see nothing going crazy
4.  I restarted the computer

none of these work, it still lags horribly after I log in.
Is there a way to roll back my computer to how it was yesterday???

---

### Post by pyros on 2006-08-26
Try starting up the system monitor and see if anything looks strange. From the way it sounds, you should be able to find a program that is using an abnormal mount of processor time.
You may also wish to check your x conf file to ensure that it is using the "nvidia" and not the "nv" driver.

---

### Post by jordanmthomas on 2006-08-26
Are you still running XGL without compiz?  If so, you could try to go back to using normal X.

```
ps -A | grep X
```

I'm not sure what it would be otherwise.

---

### Post by k9brand on 2006-08-26
Thank you for the quick replies.

When I start the computer and type what you put it shows:
13817 ?        00:00:00 Xgl
13818 tty7     00:00:01 Xorg

What does that mean?  Does that mean that Xgl is started? how would I get back to X ? 

I checked the system resources as well, I see a spike in the CPU when I'm trying to move an object, but I can't see what is causing it (because everything is frozen when it happens).

I am using the nvidia drivers, (not nv)...

---

### Post by pyros on 2006-08-26
How did you install xgl and compiz? Did you use a guide or or easyubuntu/automatix?

---

### Post by k9brand on 2006-08-26
I used the steps in this guide:
[http://www.ubuntuforums.org/showthread.php?t=131267]("http://www.ubuntuforums.org/showthread.php?t=131267")

Is there a way to stop XGL and just run X or something?

---

### Post by pyros on 2006-08-27
Well, if it were me... I would log in to a terminal (press ctrl+alt+f1), kill xgl, uninstall xserver-xorg-core and everything that depends on it, delete my xorg.conf, and install ubuntu-desktop. Removing xorg-core _should_ remove any additional x packages. That would put x back to a "factory" state. Like I said, that's just what I would do. I'm sure there are faster and more elegant ways of doing this.

---

### Post by jordanmthomas on 2006-08-27
Sorry I haven't replied yet...I had to go to Taco Bell for some fourthmeal. ;) 

To get back to a standard X, it depends on what you did to get XGL running.  Chances are you created an Xsession for XGL.  If you followed a guide, that's usually what they have you do.  If this is the case, try clicking 'Session' at the GDM login screen.  (If you don't have anything that says Session, pressing F10 should bring up a menu for you.)  Chances are, XGL will be selected.  Just choose Gnome instead of XGL and you should be good to go.

If this doesn't work, try running gnome-session-properties and see if you have anything that looks XGL / compiz-related under the Startup Programs tab.  If so, disable them and log out then back in.

---

### Post by jordanmthomas on 2006-08-27
Heh, didn't see that you posted which guide you're using.

Here's what you need to do.
```
sudo gedit /etc/gdm/gdm.conf-custom
```

Find the part that looks like this (at the very bottom)
```
[servers]# Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX). 
0=Xgl 

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo 
flexible=true
```

Comment out all of these lines (except the first one) so it will look like this:
```
[servers]# Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX). 
[COLOR="Red"]#[/COLOR]0=Xgl 

[COLOR="Red"]#[/COLOR][server-Xgl] 
[COLOR="Red"]#[/COLOR]name=Xgl server 
[COLOR="Red"]#[/COLOR]command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo 
[COLOR="Red"]#[/COLOR]flexible=true

```

Now, type
```
sudo /etc/init.gdm/restart
```
and you should be good to go.

---

### Post by k9brand on 2006-08-28
thank  you thank you thank you !!!!!  works great.

> sudo /etc/init.gdm/restart

Didn't work for me, but I just rebooted and everything is peachy now.

---

### Post by k9brand on 2006-08-28
Ok, one more question.  How do I run XGL / Compiz then?  Now when I type 

```
thefuture
``` 

it doesn't work anymore... I wish I could have it both ways :)

---

### Post by toasted on 2006-08-28
So what is the BEST way to install XGL / Compiz?
A how to I imagine but which one?

---

### Post by Toxicity999 on 2006-08-28
Look for one one of hte newer how to's the method you used is old school the more popular way is session based, which results in you just selecting Xgl from the Gdm login screen I don't have a howto link on me now but look around. Not hard to find. It's ALOT easier to do also.

---

### Post by grte on 2006-08-29
> **k9brand said:**
> thank  you thank you thank you !!!!!  works great.



Didn't work for me, but I just rebooted and everything is peachy now.

For future reference, the command should be

```
sudo /etc/init.d/gdm restart
```

> 
it doesn't work anymore... I wish I could have it both ways

Before it will work again, you'll have to sudo gedit /etc/gdm/gdm.conf-custom

And change this:

```
[servers]# Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX). 
#0=Xgl 

#[server-Xgl] 
#name=Xgl server 
#command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo 
#flexible=true
```

back to this:

```
[servers]# Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX). 
0=Xgl 

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo 
flexible=true
```

That is, remove the hash marks.

Then do ```
sudo /etc/init.d/gdm restart
thefuture
```

And it should work again.

---

### Post by k9brand on 2006-08-29
Thanks!  There is a slight problem though.  I want to have my system working great the way it is when XGL is commented out, BUT sometimes I would want to run XGL/Compiz.  Does that mean everytime I want to switch, I have to go through this commenting process?  

Should I look into writing a script that basically comments or uncomments that part of the file and restarts GDM?

It seems like my other option is to completely uninstall XGL / Compiz and all the changes I made, then find one of the newer guides to follow.  I gotta say I'm a little scared of doing that when it seems so close to working now.

---

### Post by toasted on 2006-08-29
How about this for a how-to  
Its dated 4/06 and has 2 different methods

[http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)

It tells how to make a graphical log in from gdm (method 2)

---

### Post by k9brand on 2006-08-29
I am going to try this when I get home from work.  It's a little confusing.  I think I am going to backtrack from the guide I did before and try to restore my settings back to their defaults.

I will post results here, if anyone is interested.

---

### Post by Toxicity999 on 2006-08-29
That's precisely what I was talking about, using the easy method you can select XGL or normal Gnome with X from the GDM login point. By clicking sessions but in the same way you would load into failsafe mode. Then you get an easy switch off as most people don't want XGL running as their persistant view.

---

### Post by toasted on 2006-08-29
FYI
I installed today with success using this:
[http://www.ubuntuforums.org/showthread.php?t=245152](http://www.ubuntuforums.org/showthread.php?t=245152)

Its way cool!!

---

### Post by Toxicity999 on 2006-08-30
Still that forces an XGL session on you. For the non technically inclined something goes wrong and they're left in a tty crying. I did play with that notification icon though interesting concept, I also started using the newer WM it's nice looking! I love the flicker hovering over the action buttons for some reason. I could only get compiz vanilla running though which I suppose is the light weight no carbs version. The full packages lag be to the grave and beyond as a... lag induced... zombie... of some sort... yes!

---

