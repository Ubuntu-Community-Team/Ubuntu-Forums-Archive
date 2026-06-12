---
title: "Clock panel applet failed to load"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by jonlemur on 2008-02-29
Hello everyone,

I just recently started having some trouble with my clock applet.  Here's the error message I get:

"The panel encountered a problem while loading "OAFIID:GNOME_ClockApplet"."

This appears whenever I try to add the clock applet to the gnome panel.  It didn't use to give me any trouble, but now it won't display the time.  I think it may have happened after a software upgrade, but I'm not certain if that was the issue or not.  Has any one else had similar issues, like there was a error in an update?  

Any ideas?  I'm currently stuck without being able to tell the time.  Not at all convenient.

Oh, btw, I'm running Gutsy Gibbon in Gnome.

---

### Post by erginemr on 2008-02-29
Hello,

Quite a few people (including me) have ben suffering from the OAFIID bug in Gutsy/Gnome:
[http://ubuntuforums.org/showthread.php?t=608767&highlight=OAFIID](http://ubuntuforums.org/showthread.php?t=608767&highlight=OAFIID)

> **erginemr said:**
> +1
I am also suffering from the same problem with the following error message:
The panel encountered a problem while loading "OAFIID:GNOME_MixerApplet".
.....
As ideasman42 suggested above:
"... I worked around the problem by logging off. killall gconfd-2, and removing gconf-username and mapping-username, orbit-username files from the temp dir. Then the problem went away...."
it may have something to do with the locked files in the temp folder that decide to remain locked by themselves.
Possibly a bug, which I hope will be addressed by the developers very soon.

> **ideasman42 said:**
> Seems like we should do a bug report, this keeps happening every so often for people here. I just remove their temp files and kill gconfd-2.

This could also happen because of Pressing Ctrl+Alt+Backspace (I do it sometimes when nothing important is running) - it would make sense that if some apps run in gnome dont die correctly.

METHOD I:
-------------
We are putting the problem to hibernate by deleting what is inside the /tmp folder. So, you should first try this trick, by opening nautilus, entering your /tmp folder and deleting what is inside all. Restart your computer to see if the problem is gone.


METHOD II:
--------------
Otherwise, you should try to reinstall all applets by following:
> **mlissner said:**
> The only solution I could figure out for this was: ```
aptitude search applet | more
```
Then I did an ```
aptitude reinstall [any applet preceded by a v or an i in previous step]
```

This essentially reinstalled all the applets on my system, and that did the trick. What a pain. I have no idea what caused this either.

but odds are that it may turn into a bigger problem:
> **pxrox said:**
> Yes, I did follow your instructions:

```
aptitude search applet | more
aptitude reinstall [any applet preceded by a v or an i in previous step]
```

Some applets got installed OK, but then lots of python errors on, e.g., deskbar-applet !

I just posted separately regarding this python error, [http://ubuntuforums.org/showthread.php?p=4131366](http://ubuntuforums.org/showthread.php?p=4131366) , which is really vexing me (worked hard to get python2.5 uninstalled/reinstalled, and yet still I get these python errors w/

```
 sudo apt-get purge deskbar-applet
```

(see [http://ubuntuforums.org/showthread.php?p=4131366](http://ubuntuforums.org/showthread.php?p=4131366) )

I thought I was fixing something little, and it seems to have turned into something big....:(

---

### Post by jonlemur on 2008-02-29
Thanks very much for your advice, however neither technique took care of the problem for me.  Could there be something that I could install an older version of, or another clock that would sit up where the previous one did?

---

### Post by erginemr on 2008-02-29
There is xfce's orage, but it has been developed with xfce desktop in mind, so I don't know whether it will work on a Gnome panel:
[http://ubuntuforums.org/showthread.php?t=245353](http://ubuntuforums.org/showthread.php?t=245353)
[http://ubuntuforums.org/showthread.php?t=177763](http://ubuntuforums.org/showthread.php?t=177763)

---

### Post by jonlemur on 2008-03-07
I have orage installed, but I can't figure out how to get it to appear on the dock.  Is there a way to do this?

---

### Post by SunnyRabbiera on 2008-03-07
> **jonlemur said:**
> I have orage installed, but I can't figure out how to get it to appear on the dock.  Is there a way to do this?

Its XFCE only so it wont work in gnome, XFCE and gnome might share the same library (gtk) but have little else in common.

---

