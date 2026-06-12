---
title: "[SOLVED] Update manager trying to install KDE ?"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-08-24
Why is the update-manager trying to install a bunch of KDE crap ? Please see attachments.

The only thing related to KDE that I have installed is Kopete and K3B. Do those apps need all this kde packages like kdesktop and kicker kdelibs etc ?

Its also trying to install Compiz Fusion packages, but I am avoiding those as I have been bitten by those earlier.

---

### Post by Patrick793 on 2007-08-24
Odd. I would say, don't install them.

---

### Post by Inxsible on 2007-08-24
But why is it showing up all of a sudden? It never did before :(

---

### Post by Ink-Jet on 2007-08-24
It just looked like libraries to me, and the update went fine.
Pretty sure KDE itself didn't get installed, the package was way too small for it.

---

### Post by Inxsible on 2007-08-24
> **Ink-Jet said:**
> It just looked like libraries to me, and the update went fine.
Pretty sure KDE itself didn't get installed, the package was way too small for it. So you are saying you got it too ? and you don't use Kubuntu, right ?

---

### Post by carloslosgrande on 2007-08-24
[FONT="Comic Sans MS"]I just got it installed now and as far as I can tell nothing has changed. I don't run KDE, just a couple of apps. I didn't get any compiz stuff, but then I don't run any compiz.
I guess I'll really know when I restart.[/FONT]

---

### Post by philinux on 2007-08-24
If you notice all they are are updated files that are allready in synaptic. Just a later version.

---

### Post by mcurtiss1970 on 2007-08-24
if you have amarok installed, would that trigger some kde updates?  i saw the same thing.

---

### Post by igknighted on 2007-08-24
k3b and kopete both require the main KDE libs packages that you see.  I believe that with what is required for kopete you would have enough to select KDE at gdm and log in to a KDE session, but I'm not 100% sure.  Either way, since KDE apps basically all share the same libraries, you need the whole kitten kaboodle for just an app or two.

EDIT: You do realize that all those things are installed, right?  You have compiz fusion on your system already.  If you don't want it, delete it.  Otherwise you might as well update it so the icon stops annoying you to do it :).  Same with the KDE libs.  Definitely update them unless you plan to delete them (and thereby the apps that use them).

---

### Post by quinnten83 on 2007-08-24
I've got Amarok, and getting the same thing.
I just looked into my cache and Amarok is like the biggest application in there. Mebbe it needs a lot of dependencies...

---

### Post by Buddha443556 on 2007-08-24
Just updated 33 packages, mostly KDE, no problem. Rebooted fine.  I'm running Kubuntu Dapper.

---

### Post by Inxsible on 2007-08-24
> **Buddha443556 said:**
> Just updated 33 packages, mostly KDE, no problem. Rebooted fine.  I'm running [COLOR=Red]Kubuntu[/COLOR] Dapper.
ummm.. No wonder ;)

---

### Post by Inxsible on 2007-08-24
> **igknighted said:**
> k3b and kopete both require the main KDE libs packages that you see.  I believe that with what is required for kopete you would have enough to select KDE at gdm and log in to a KDE session, but I'm not 100% sure.  Either way, since KDE apps basically all share the same libraries, you need the whole kitten kaboodle for just an app or two.

EDIT: You do realize that all those things are installed, right?  You have compiz fusion on your system already.  If you don't want it, delete it.  Otherwise you might as well update it so the icon stops annoying you to do it :).  Same with the KDE libs.  Definitely update them unless you plan to delete them (and thereby the apps that use them).
Yeah Kopete is just a trial thing I was trying because GAIM doesn't do webcast. But it seems odd that it would download the kdesktop  for it. 

And yeah, I do know that they are already on my system given that I have installed a couple of KDE apps. Just hate to "be reminded" of it ;)

I still am going to keep K3B -- so I guess I should just go ahead and install.

W.R.T Compiz Fusion, I do NOT want to update, because the last time i did, it messed up the whole CF install. I have also heard that the latest update has screwed up the settings manager for CF. I might just comment out the CF repos ..so it doesn't show me the updates. I shall wait to update CF when I know for sure that the update is stable :D

---

### Post by igknighted on 2007-08-24
> **Inxsible said:**
> Yeah Kopete is just a trial thing I was trying because GAIM doesn't do webcast. But it seems odd that it would download the kdesktop  for it. 

And yeah, I do know that they are already on my system given that I have installed a couple of KDE apps. Just hate to "be reminded" of it ;)

I still am going to keep K3B -- so I guess I should just go ahead and install.

W.R.T Compiz Fusion, I do NOT want to update, because the last time i did, it messed up the whole CF install. I have also heard that the latest update has screwed up the settings manager for CF. I might just comment out the CF repos ..so it doesn't show me the updates. I shall wait to update CF when I know for sure that the update is stable :D

Good idea about cf.  My settings manager doesn't work at all (in Fedora... so the issue goes all the way back upstream).  My settings are bearable so I'm just gonna wait it out and keep updating, the work it would take to switch to an old version is more than I care to put in :).  I figure thats a huge break, they've gotta come out with a fix soon.

EDIT: totally off topic, but does anyone know if you can adjust compiz-fusion directly from gconf?  Or is the broken part between gconf and the cf app itself?

---

### Post by Inxsible on 2007-08-24
> **igknighted said:**
> Good idea about cf.  My settings manager doesn't work at all (in Fedora... so the issue goes all the way back upstream).  My settings are bearable so I'm just gonna wait it out and keep updating, [COLOR=Red]the work it would take to switch to an old version is more than I care to put in[/COLOR] :).  I figure thats a huge break, they've gotta come out with a fix soon.

EDIT: totally off topic, but does anyone know if you can adjust compiz-fusion directly from gconf?  Or is the broken part between gconf and the cf app itself?You said it man !!

About changing settings from gconf, read this link

[http://ubuntuforums.org/showthread.php?p=3244342#post3244342](http://ubuntuforums.org/showthread.php?p=3244342#post3244342)

I havent tried it as I am at work, but might give it a go later tonite.

---

### Post by igknighted on 2007-08-24
> **Inxsible said:**
> You said it man !!

About changing settings from gconf, read this link

[http://ubuntuforums.org/showthread.php?p=3244342#post3244342](http://ubuntuforums.org/showthread.php?p=3244342#post3244342)

I havent tried it as I am at work, but might give it a go later tonite.

Thanks for the tip, I'll try it when I get home

---

### Post by Happy_Man on 2007-08-24
Sorry, wrong thread. Someone delete this.

---

