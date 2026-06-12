---
title: "trouble installing things"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by Henaro on 2007-07-11
Hello everyone.  

I did something.  Not too sure what I did but I've messed something up.  I keep getting this when trying to install, and reinstall things:  

```
subprocess post-installation script returned error exit status 1
```

When I googled I found this post:
[http://forums.debian.net/viewtopic.php?t=5487&](http://forums.debian.net/viewtopic.php?t=5487&)

When I ran the dpkg commands I kept getting this error:
```
dpkg: status database area is locked by another process
```

Anyone know what the deal is?

---

### Post by Inxsible on 2007-07-11
Do you have synaptic or add/remove running while you are trying to install ?

---

### Post by Henaro on 2007-07-11
No.

EDIT:

Here's the full error:

```
Starting Hybrid 7 IRC Server: ircd-hybridinvoke-rc.d: initscript ircd-hybrid, action "start" failed.
dpkg: error processing ircd-hybrid (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 ircd-hybrid
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Henaro on 2007-07-11
Still not working :-(

But also unrelated I keep getting horrible frame rates and the ground textures won't load in WoW under wine.  I suspect a video driver problem.  I have an ATI Radeon x1600 Pro.  I have the driver installed also.  Anyone know how to fix this?

Here's a screenshot:
[http://commabunny.org/public/pub/.WoW.png](http://commabunny.org/public/pub/.WoW.png)

---

### Post by Admiral-Cyclops on 2007-08-19
> **Henaro said:**
> No.

EDIT:

Here's the full error:

```
Starting Hybrid 7 IRC Server: ircd-hybridinvoke-rc.d: initscript ircd-hybrid, action "start" failed.
dpkg: error processing ircd-hybrid (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 ircd-hybrid
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


I am having the exact same problem, did you ever find the solution?

---

### Post by babysteps on 2007-08-21
> **Admiral-Cyclops said:**
> I am having the exact same problem, did you ever find the solution?


I'm running Kubuntu 6.06 LTS and was having some problem with installing some packages.  Here's a link I found that has at least gotten my Adept Manager going again. Hope it helps you, too. 

[http://ubuntuforums.org/showthread.php?t=311885&highlight=database+locked%3F](http://ubuntuforums.org/showthread.php?t=311885&highlight=database+locked%3F)

basically I typed in the terminal:

sudo apt-get dist-upgrade
sudo dpkg --configure -a

now it's downloading updates.

Babysteps

---

