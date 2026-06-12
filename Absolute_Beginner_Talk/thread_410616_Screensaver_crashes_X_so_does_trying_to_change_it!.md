---
title: "Screensaver crashes X so does trying to change it!!!"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by slambrick on 2007-04-15
I changed the screen saver the other day I thnik it was the gnome default installed one. As soon as I selected it the x window crashed. Now whenever I try to access the screensaver option or the machine tries to screensave it reboots X.
Can I reset the screen saver in terminal? How do I do this? any other suggestions?:confused:

---

### Post by RomeReactor on 2007-04-16
Hi. Do you have 3d acceleration with your video card? If you don't, and you chose a screensaver that uses acceleration, then that may be why X is crashing. I uninstalled the default screensaver that came with gnome, so I really can't be of much help to you in that regard; however, try this: Open Synaptic, search for "gnome-screensaver" and wait for it to come up; then, right-click on it and select "Properties" and on the "Installed Files" tab, look for an entry in **/usr/bin**. Then open a terminal an enter:

```
man PROGRAM_NAME
```

where **man** is the manual page and PROGRAM_NAME is the name you found in "usr/bin". It should provide you with a manual of operations, settings and options for that program.

Another option would be to completely uninstall it, and perhaps reinstall it again later; it's up to you.

---

### Post by ckoester on 2007-05-05
I'm having the exact same problem.  The worst part is that when the screensaver starts it crashes X and kicks you back to the logon screen - losing all of your open programs...

The only solution I have found so far is to uninstall gnome-screensaver, which is not very practical.

---

### Post by kurtstricker on 2007-05-07
I have the same problem.  Can anyone tell a newbie how to disable or change the screen saver back to default?  I have set the screen saver to molecules and this hangs the OS after 10 minutes.  If I try and change it, the screen hangs immediately.  Help???  My wife is driving me crazy on this...

---

### Post by the_burk on 2007-05-09
what processor and what ubuntu release are you people running ... im on amd 64 edgy 64 bit .. maybe its a 64 bit bug ?? when did it start .. what did you do before ??

---

### Post by the_burk on 2007-05-09
oh btw .. sorry.. 

to make it dissappear .. go to synaptic ... find gnome-screensaver and remove it .. 

leaves you with no screen saver .. but it wont kill x server all the time either..

Edit*

the problem isnt actually the screen saver .. its opengl .. try to start glxgears and see what happens .. 

just open synaptic and remove the glx screensaver hacks ... xscreensaver-gl  xscreensaver-gl-extra rss-glx

at least you got screen savers .. but not the opengl ones..

---

### Post by ckoester on 2007-05-09
I just upgraded to Feisty from Edgy, and the screensaver problem is fixed.  

This leads me to believe that there is some screesaver settings file that must be restored to defaults to fix this problem.  I don't know what file it is, but the Feisty upgrade process definitely took care of it.

This is not a great solution, but it does work.  I am afraid to change screensaver settings now in fear that the problem will happen again.

---

### Post by kurtstricker on 2007-05-09
Thanks for the ideas.  

It was after the upgrade to Fawn that this problem first happened.  

It is fixed.  I reinstalled the xscreensaver-gl using Synaptic and was able to change the screen saver to blank screen.

---

### Post by ibbuntu on 2008-01-28
This has just started happening to me for no apparent reason. I run gutsy. GL screensavers were working fine, and now every time they run they crash x. Anyone got any ideas about what might have happened and how to fix it? (Apart from uninstalling GL stuff)

---

### Post by imaginal on 2008-01-28
I've had the same problems, and lack of solutions.
[http://ubuntuforums.org/showthread.php?t=664962]("http://ubuntuforums.org/showthread.php?t=664962")

---

