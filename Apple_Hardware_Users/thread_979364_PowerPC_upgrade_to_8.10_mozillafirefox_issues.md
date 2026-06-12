---
title: "PowerPC upgrade to 8.10 mozilla/firefox issues"
date: 2008-11-11
forum: Apple Hardware Users
---

### Post by ubuntubrian on 2008-11-11
I successfully upgraded to Intrepid on My G4 TiBook. Quite the process but it boots and runs, with issues.
Firefox crashes if I try to play youtube videos, or any other swf file, with the gnash plugin. Oddly, this is not an issue on my G3Powerbook running Intrepid. Also Epiphany or Galeon will not run at all with segfault.
I have a bunch of dependency issues, almost all KDE, which will not function anymore but I don't mind as I use Gnome. I'm trying to install the Seamonkey suite but Synaptic wants to remove mozilla-browser, fine with me, but the removal fails:
```
unable to remove /usr/bin/mozilla: Inappropriate ioctl for device
```
I've googled this to no avail.
BTW, mozilla-browser runs and shows the gnash-plugin in about:plugins, as does firefox, but I get the standard need to "install flashplayer or enable java message" whereas Firefox just crashes. Midori also runs but no flash.
I think that Firefox is almost playing flash. 
BTW-smae result with gnash from repositories or built from CVS sources.

---

### Post by stream303 on 2008-11-12
I had this weirdness too from a fresh install of Intrepid.  Although I like Firefox, I also like to use Gnome's low-resource Epiphany-browser, and after install, it just disappears.

If I find anything, I'll let you know, since Epiphany-browser is one of my favorites.  (I installed the Gecko version not knowing that there is a webkit version too - too chicken to see if the webkit version works until I do more research...)

---

### Post by Leslie Viljoen on 2008-11-12
There seem to be quite a few programs that segfault soon after starting in Xubuntu - your post seems to confirm that the problem is happening in Ubuntu too. I think something went wrong with a library during the ISO build process, because most of the programs I build from source start working. 

Only Totem showed no change after a rebuild, but it was only crashing when trying to go to fullscreen, so that may be some other problem.

See:
[http://ubuntuforums.org/showthread.php?t=977120](http://ubuntuforums.org/showthread.php?t=977120)

---

### Post by milkwood on 2008-11-12
Hi,folks.
This is just off the top of my head,why not boot firefox in a state of failsafe?
It might be something to do with firefox's extensions.
And why not erase kde's proglam by backing to the pure gnome?
It may be a little bit painful.
I may be handing over wrong advice,but please forgive me.
Because I am tired today and I don't happen to have enough knowledge to reply this.
I think it's just conflict problems or etc(for example,upgrade's process).
I don't know.
I hope you will welcome bland-new days.

Thanks.

---

### Post by ubuntubrian on 2008-11-12
I logged into Xubuntu and Thunar segfaults just like Epiphany and Galeon.This doesn't make my inability to uninstall mozilla-browser any clearer though. Maybe we'll get this cleared up. Oddly, the upgrade on my other notebook worked fine and nothing crashes and even gnash plays in Firefox. KDE4 works too. I haven't updated it in a few days and perhaps I won't in case it's the newest packages causing the problems.

---

### Post by milkwood on 2008-11-13
I'm so sorry.I totally misunderstood what you mentioned.
I don't know why I misunderstood this obvious thing to that wrong.
Maybe I just drunk too much.
You mean Firefox crashes with gnash when you try to play flash files,don't you?
I have experienced this problem with swfdec before.
Perhaps It related with my PC's cpu.
The power to deal it might be not enough.
This is my case. 

And When I upgraded from hardy to intrepid,I've also experienced low-graphic solution thing.
When I logged in gnome on low-graphic mode,I didn't use any application even terminal
except applications not belong to gnome or need things that related with that(I could use "opera" and "Xine" on that state).
I think the one you upgraded succeeded ,and the other one failed.

This is all what I can say so far.
I hope this isn't too far from what you mentioned.

---

