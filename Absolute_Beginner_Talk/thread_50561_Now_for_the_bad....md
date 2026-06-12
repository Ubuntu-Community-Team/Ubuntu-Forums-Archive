---
title: "Now for the bad..."
date: 2005-07-20
forum: Absolute Beginner Talk
---

### Post by grofaz on 2005-07-20
...Having done a fresh install onto my second hard drive, I've set everything back up. Extra-repositories, updates, fav packages, etc. My Add/Remove Programs Application Installer hangs up. Start it up, the little wheel in motion cursor warps up to speed and that's it, just keeps on going. Nothing happens. Now I tested it before I updated everything and it worked, but after updating it does not work. So something must be askew in the update department, some sort of conflict. Any ideas ?? What should I do to fix this ??

---

### Post by poofyhairguy on 2005-07-20
[QUOTE=grofaz]...Having done a fresh install onto my second hard drive, I've set everything back up. Extra-repositories, updates, fav packages, etc. My Add/Remove Programs Application Installer hangs up. Start it up, the little wheel in motion cursor warps up to speed and that's it, just keeps on going. Nothing happens. Now I tested it before I updated everything and it worked, but after updating it does not work. So something must be askew in the update department, some sort of conflict. Any ideas ?? What should I do to fix this ??[/QUOTE]

Is synaptic broke? Use that for upgrades...

---

### Post by ozzie123 on 2005-07-20
Yes, I agree with poofyhairguy, you should use Synaptic (or Kynaptic on KDE) to do that. It's safer and checks for dependencies (although add/remove program also checks for it, but go with Synaptic anyway).

---

### Post by grofaz on 2005-07-20
I do use synaptic, it just bugs me that the add/remove app isn't working. Means something is wrong under the hood.

Getting to like Linux more and more everyday. It's really cool that you can make it as fat or as lean as you like. Microsoft...master foisters of bloat!

---

### Post by poofyhairguy on 2005-07-21
[QUOTE=grofaz]I do use synaptic, it just bugs me that the add/remove app isn't working. Means something is wrong under the hood.
[/QUOTE]

That feature was brand new in hoary...give it another release.

Downside of two releases a year....

---

### Post by grofaz on 2005-07-21
Using synaptic is cool with me. Is there a way to get rid of the Add/Remove app ?

---

### Post by bored2k on 2005-07-21
[QUOTE=grofaz]Using synaptic is cool with me. Is there a way to get rid of the Add/Remove app ?[/QUOTE]
 You can remove the   gnome-app-install package.

---

### Post by grofaz on 2005-07-21
gnome-app-install, ah thank you!

---

### Post by grofaz on 2005-07-21
Hmmm...If I uninstall gnome-app-install synaptic takes out ubuntu-desktop with it. I'm not sure that's a very good idea. So what's the story here?

---

### Post by bored2k on 2005-07-21
[QUOTE=grofaz]Hmmm...If I uninstall gnome-app-install synaptic takes out ubuntu-desktop with it. I'm not sure that's a very good idea. So what's the story here?[/QUOTE]
 ubuntu-desktop is a metapackage that supposedly provides a clean installment/upgrade. You can remove it safely. Heck, most of us don't even have the package, so go ahead,

---

### Post by TravisNewman on 2005-07-21
You'll want to install ubuntu-desktop before upgrading to Breezy, if you decide to do so. It's harmless to keep gnome-app-install, but upgrading may not go so well if you don't keep ubuntu-desktop.

---

### Post by bored2k on 2005-07-21
[QUOTE=panickedthumb]You'll want to install ubuntu-desktop before upgrading to Breezy, if you decide to do so. It's harmless to keep gnome-app-install, but upgrading may not go so well if you don't keep ubuntu-desktop.[/QUOTE]
 I'm a complete upgrade "from scratch" advocate.

---

### Post by poofyhairguy on 2005-07-21
[QUOTE=bored2k]I'm a complete upgrade "from scratch" advocate.[/QUOTE]

Me too....Windows ways die hard...

---

### Post by TravisNewman on 2005-07-21
one of my installations is from right when warty came out, and it's been dist-upgraded all the way through the hoary test cycle, and was dist-upgraded to breezy, and then dist-upgraded back down to hoary, and I haven't had a single problem.

EDIT: I haven't had a single problem that wasn't easily fixed, that is.

---

### Post by bored2k on 2005-07-21
[QUOTE=panickedthumb]one of my installations is from right when warty came out, and it's been dist-upgraded all the way through the hoary test cycle, and was dist-upgraded to breezy, and then dist-upgraded back down to hoary, and I haven't had a single problem.[/QUOTE]
This is me trying to dist-upgrade:
[IMG]http://img324.imageshack.us/img324/4624/04466ly.jpg[/IMG]

This is me reinstalling from scratch:
[IMG]http://img324.imageshack.us/img324/766/leapsheep7zk.jpg[/IMG]

---

### Post by poofyhairguy on 2005-07-21
[QUOTE=panickedthumb]one of my installations is from right when warty came out, and it's been dist-upgraded all the way through the hoary test cycle, and was dist-upgraded to breezy, and then dist-upgraded back down to hoary, and I haven't had a single problem.
[/QUOTE]

It can be done...but then you don't see the new installer.

I'm bad....I'll reinstall if my wireless quits working....I reinstall because I tried kubuntu and didn't like it. I reinstall to pass time....

---

### Post by grofaz on 2005-07-22
OK, it's removed. We'll see about upgrading when the time comes. Thanks!

---

### Post by UbuWu on 2005-07-22
[QUOTE=poofyhairguy]That feature was brand new in hoary...give it another release.

Downside of two releases a year....[/QUOTE]

But in breezy all things will be better  :grin: 
See for yourself what the add/remove apps program will look like:
[http://www.niran.org/code/soc/](http://www.niran.org/code/soc/)
I think it is one of my favourite new features of breezy.

---

