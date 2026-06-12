---
title: "Docking Bar (SimDock) Overlaying Browser"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-09-26
Hi, I have had Sim Dock installed for sometime and can't figure out
why it always have to be in front of everything.  When I open a browser
or any window it always has to be in front.  Is there a way to fix this.
I'd like it to drop into the back ground when a something is opened.

Thanks

 [IMG]http://img212.imageshack.us/img212/8031/screenshotkb4.png[/IMG]

---

### Post by Orbital75 on 2007-10-03
No Takers?  

Hummm...... I really wish someone could help me out on this issue.

---

### Post by Orbital75 on 2007-10-03
I'm really sorry to bump this post but I really would like to solve this.
The board moves so fast not many people get to see if before it hits
the second or third page.

---

### Post by jordanmthomas on 2007-10-03
While I'm sure it's not exactly what you're looking for, there's a program called devilspie that allows you to "glue" any program to the desktop.

---

### Post by Orbital75 on 2007-10-03
Thank you for posting and shooting that idea out but I'd like to stick with Sim Dock.
I like the way the icons grow as you mouse over them ( like OS X ). The problem
with my Install is that I am in Virtual Box and it doesn't support 3D acceleration so
I can't use any of the other similar bars.

---

### Post by jordanmthomas on 2007-10-03
I know you'd like to keep SimDock.  You use devilspie to launch simdock.  Devilspie tells your window manager that simdock should stay on the bottom.

---

### Post by Orbital75 on 2007-10-04
I'm sorry, I thought that you were suggesting another Bar. I didn't
know what devilspie was. Have you used this program before.
If so, how do I implement it?

---

### Post by ramjet_1953 on 2007-10-04
I know it is off-topic, but have you checked-out KoolDock?

It works fine in both GNOME and KDE, with or without Compiz, or Beryl.

It magnifies, just like OSX and you can also make it auto-hide.

[COLOR="Red"]sudo apt-get install kooldock[/COLOR]

Regards,
Roger :cool:

---

### Post by jordanmthomas on 2007-10-04
I've never used it before, but judging from what I've just looked up online (sorry it took a while, my internet connection here at school is pretty painful) this may help:
```
sudo aptitude install devilspie
```
install devilspie (duh)

```
mkdir ~/.devilspie
```

Now, type this:
```
xprop | grep CLASS
```
your cursor will become a crosshair.  Click on your SimDock window and a line like this will be printed in your terminal (I clicked firefox)
```
WM_CLASS(STRING) = "gecko", "Firefox-bin"
```
Remember this value (in quotations)  For example, I'd use Firefox-bin.

```
gedit ~/.devilspie/FixSimDock.ds
```
put this in it:
```
(if
(matches (window_class) “[COLOR="Red"]WHAT YOU GOT FROM XPROP[/COLOR]”)
(begin
(below)
(undecorate)
(skip_pager)
(skip_tasklist)
(wintype “utility”)
)
)
```

Now, run devilspie and then run simdock (quit simdock first if needed).  If all goes well, your problem should be fixed I think.

If what I put here decides to not work, they have a pretty informative wiki [here]("http://foosel.org/linux/devilspie").

Good luck!

---

### Post by jordanmthomas on 2007-10-04
> **ramjet_1953 said:**
> I know it is off-topic, but have you checked-out KoolDock?

It works fine in both GNOME and KDE, with or without Compiz, or Beryl.

It magnifies, just like OSX and you can also make it auto-hide.

[COLOR="Red"]sudo apt-get install kooldock[/COLOR]

Regards,
Roger :cool:
That's a good suggestion, but if he's running it in a VM he may not want both GTK and Qt stuff loaded up unless he has tons of memory.  :)

---

### Post by Ptero-4 on 2007-10-04
Hi. A couple questions about SimDock. Does it reserve it's area (like the panel does)? Does it allow the user to disable the tasks section? Does it have a trash can? and can it handle gnome URI's properly?

---

### Post by Ptero-4 on 2007-10-10
An update. I just tried simdock and there are some things about it.
It's task module can be turned off.
It can handle gnome URI's.
It reserves it's desktop area.
It seems to lack a trash plugin.

But now a question.
When I run it (on debian lenny with XFCE) it shows an error message about not being able to find the image at /usr/share/pixmaps/backgrounds/gnome/background-default.jpg and another one about not being able to find the background image. Where are they and how to make simdock find them? also it shows the black border that kiba-dock normally shows when you have compositing disabled (I have mine enabled and I'm using xfwm4's compositor).

---

### Post by jordanmthomas on 2007-10-10
The black window is probably caused by it not being able to find the background.  I would specify my background on the command line when launching it probably with the -b switch.

more info:
[http://simdock.wiki.sourceforge.net/FAQ](http://simdock.wiki.sourceforge.net/FAQ)

---

### Post by Orbital75 on 2007-10-10
I think this Background issue is directly related to my problem.  It can't find the new background
once a program is opened so it just keeps the desktops.  It also as you said, reserves desktop
space.  I'd say about an inch from the bottom.

---

### Post by nikoPSK on 2007-10-10
> **ramjet_1953 said:**
> I know it is off-topic, but have you checked-out KoolDock?

It works fine in both GNOME and KDE, with or without Compiz, or Beryl.

It magnifies, just like OSX and you can also make it auto-hide.

[COLOR="Red"]sudo apt-get install kooldock[/COLOR]

Regards,
Roger :cool:

Great! A dock without a composter! I hate that awn requireds compiz or beryl which are not always up to it (for me at least)

---

### Post by Orbital75 on 2007-10-13
Well, I still can't get this resolved.  Has anyone else had this issue, or is it just my
machine?

---

### Post by nikoPSK on 2007-10-14
Probably your machine. Try re-installing linux, that might help. Or try a completely different dock like awn.:popcorn:

---

### Post by jordanmthomas on 2007-10-14
> **nikoPSK said:**
> Probably your machine. Try re-installing linux, that might help. Or try a completely different dock like awn.:popcorn:

I hate to sound like a jerk here, but a) reinstalling Linux would be a waste of time and b) he said he doesn't want to use AWN because he's running in a virtual machine.

Anyway, my final suggestion would be to delete any config files simdock left behind and either reinstall simdock or try running it again after removing its config.

By the way, did devilspie not work for you?

---

### Post by nikoPSK on 2007-10-14
> **jordanmthomas said:**
> I hate to sound like a jerk here, but a) reinstalling Linux would be a waste of time and b) he said he doesn't want to use AWN because he's running in a virtual machine.

Anyway, my final suggestion would be to delete any config files simdock left behind and either reinstall simdock or try running it again after removing its config.

By the way, did devilspie not work for you?

Ubuntu is an hour max install, for me its around 45.:)

---

### Post by Orbital75 on 2007-10-14
Nope, it sure didn't.... I really wish it would have.
The same problem persisted afterwards.

I really like SimDock and would be more than happy to try something
that looked similar but as stated the Virtual Machined doesn't support
3D and most all of these Docks require Beryl or Compiz.  I haven't found
one yet that looks near the same and has the popup feature like OSX and
doesn't require advanced 3D.

Humm......

---

