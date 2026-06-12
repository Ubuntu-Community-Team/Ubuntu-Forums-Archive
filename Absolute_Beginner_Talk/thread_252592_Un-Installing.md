---
title: "Un-Installing"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by FlukedAnchor on 2006-09-07
Im Still VERY new to using this .. How do I uninstall programs i dont use even tho it says "Use Advanced Uninstaller"  i am sooo lost on all of this lol

---

### Post by amo-ej1 on 2006-09-07
Well, everything you'll ever need to do with apt can be summarized in the following commands:

```

sudo apt-get update
sudo apt-get upgrade
apt-cache search <progname>
sudo apt-get install <programe>
sudo apt-get remove <progname>

```

With the following meanings:
[LIST]
[*]Update the package cache
[*]Upgrade installed packages
[*]Search for a certain application
[*]Install a certain application
[*]Uninstall a certain application
[/LIST]

Or you could use the graphical gnome-app-install to click you way through it all ;-)

---

### Post by xyz on 2006-09-07
Hi-
I just want to add that if, as you say, you are "Still VERY new" to this, you may want to click on "System > Administration > Synaptic Package Manager".

At this point, it'll ask for your root password which you'll type within the appropriate space. That'll open "Synaptic".

Wait a few seconds and click on "Search" and a small window will open which allows you to type in the name of the prog you want to install or uninstall.

Once you've typed it in, Synaptic will search for it. Then right-click on the prog you want to uninstall and select "Mark for Complete Removal". Then you click on "Apply"and OK, I think.

Be careful not to remove just anything! For instance, you may not want the Games that come default when you install! If you were to remove them, this action would make other progs you need not work any more because they are interdependent.

---

### Post by xpod on 2006-09-07
Again aint it better to use "aptitude" as apose to "apt-get".

Aptitude removes all dependancies it installs where as "apt-get" apparently dont.

Thats the advice i see,got...and use

---

### Post by xyz on 2006-09-07
I've always been told that aptitude is the way to go for the very reasons you stated!
**FlukedAnchor** being new to all of this, he/she may want to go Synaptic for a start!

---

### Post by xpod on 2006-09-07
Im having "timeout" probs so if this IS already up...sorry..

I agree about synaptic...same thing but with a nice "click" ability;) 

I noticed though that even using "aptitude"(synaptic) i can always still find empty folders to do with whatever i removed..
Ive noticed a "purge" command that goes with the "remove" command.....is THAT
the best way to COMPLETELY remove all traces of something OR is that just for troublesome removals??

---

### Post by xyz on 2006-09-07
**gtkorphan** in Synaptic or in a console:
```
sudo aptitude install gtkorphan
```
in case you like graphical interface better.
Or this link:
HOWTO: Cleaning up all those unnecessary junk files...
[http://www.ubuntuforums.org/showthread.php?t=140920&highlight=deborphan](http://www.ubuntuforums.org/showthread.php?t=140920&highlight=deborphan)

---

### Post by xpod on 2006-09-07
THATS the one....:D ..cheers.

IF i know what im looking for i use the terminal but if im just checking out all thats on offer then i have to use "synaptic".

Theres some mad app names in there that i still get a slap off the wife for telling her i tried

---

### Post by xyz on 2006-09-07
gtkorphan is good stuff but it won't remove wives' residual slaps! ;)

---

