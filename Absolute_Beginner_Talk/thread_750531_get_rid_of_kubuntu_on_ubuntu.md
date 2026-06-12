---
title: "get rid of kubuntu on ubuntu"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by larsdk on 2008-04-09
Hi there,

I just wanted to have a look at Kubuntu and installed it by using

```
sudo apt-get install kubuntu-desktop
```

however 

```
sudo aptitude remove kubuntu-desktop
```

does not remove it all. Far from it, since my menus in Ubuntu are now filled up with KDE stuff...

How du I get rid of all of Kubuntu?

---

### Post by ELF_O8 on 2008-04-09
it didn't remove everything because you didn't tell it to.
you just told it to remove the desktop environment.
I don't know how to remove the rest short of 
manually in synaptic

---

### Post by Average Joe on 2008-04-09
Follow the [Psychocats]("http://www.psychocats.net/ubuntu/puregnome") instructions.

---

### Post by nickpaton on 2008-04-09
Hi

It's worth doing a search within the forums for this.

I found[ this]("http://ubuntuforums.org/showthread.php?t=744198") which will work for you, but there may be easier methods.

Good Luck!

---

### Post by larsdk on 2008-04-09
pasting the suggested commands for[ "Remove Kubuntu"]("http://www.psychocats.net/ubuntu/puregnome") might seem like the thing to do. However I can see that it wants to remove thing i don't want it to remove (such as my mySQL and php and all sorts of other things)

---

### Post by nickpaton on 2008-04-09
The instructions on Psychocats takes you back to pure Gnome.  What you then need to do is to add the Ubuntu Desktop programs as per their [howto]("http://www.psychocats.net/ubuntu/gnome")

---

### Post by larsdk on 2008-04-09
i can see that this is what it does (and it also includes a ```
&& sudo apt-get install ubuntu-desktop
``` in the end). 

However, as I wrote, it lists up all the things that will be removed. And this includes my mySQL server and my PHP setup - and I would really like to avoid that :)

---

### Post by fela on 2008-04-09
kubuntu-desktop is a meta package. If you'd of installed it using aptitude (not apt-get), you would only have to run ```
sudo aptitude remove kubuntu-desktop
``` to uninstall it and all associated stuff (dependencies). Since you did not, you will have to manually remove all packages that were automatically installed when you installed kubuntu-desktop. Sorry, but it's the only way if you use apt-get.;)

---

### Post by aysiu on 2008-04-09
For the record, using *aptitude* to remove a metapackage's (*kubuntu-desktop*'s in this example) dependencies will work only if you'd also used *aptitude* to install that metapackage in the first place.

---

### Post by Shazaam on 2008-04-09
Do you already have ubuntu-desktop installed? If you do, when you boot up you can choose either kde or gnome at the login screen.
As stated before look at the links if you REALLY want to uninstall kubuntu-desktop.

---

### Post by larsdk on 2008-04-09
i have ubuntu gutsy installed already, so what i want is just to get back to the default gnome without all the KDE stuff...

---

### Post by Average Joe on 2008-04-10
I have had a similar problem (I think). When I removed all the KDE stuff following the Psychocats instructions, it wanted to remove my Apache webserver as well.

So I first copied my webserver settings (to my home folder), then removed the KDE things, and then reinstalled the Apache webserver and restored the saved settings. Maybe you could try something similar.

---

### Post by stchman on 2008-04-10
> **larsdk said:**
> Hi there,

I just wanted to have a look at Kubuntu and installed it by using

```
sudo apt-get install kubuntu-desktop
```

however 

```
sudo aptitude remove kubuntu-desktop
```

does not remove it all. Far from it, since my menus in Ubuntu are now filled up with KDE stuff...

How du I get rid of all of Kubuntu?

You need to use the autoremove command:

```
sudo apt-get autoremove kubuntu-desktop
```

If you install with apt-get then remove with apt-get.  For aptitude the same thing.

The autoremove command removes all unused dependencies.

---

### Post by aysiu on 2008-04-10
Backing up settings is a good regular practice to employ, regardless of what you're doing, but uninstalling packages usually does not affect settings.

---

### Post by GSZX1337 on 2008-04-10
> **larsdk said:**
> i have ubuntu gutsy installed already, so what i want is just to get back to the default gnome without all the KDE stuff...

Have you tried 
```

sudo apt-get remove kde

```

---

