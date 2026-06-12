---
title: "dependency issues installing kubuntu-desktop"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by crav on 2007-08-09
I wanted to install KDE for various reasons that aren't worth going into, so I issued the standard command. I was told a dependency wasn't met, so I tried to fill the dependency and on and on down the line. It seems I need "libdus-1-2" anyone know what this is or where to get it?

My console:
```
:~$ sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: ktorrent but it is not going to be installed
E: Broken packages
:~$ sudo apt-get install ktorrent
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ktorrent: Depends: libdbus-1-2 (>= 0.60) but it is not installable
E: Broken packages
:~$ sudo apt-get install libdus-1-2
Reading package lists... Done
Building dependency tree        
Reading state information... Done
E: Couldn't find package libdus-1-2
```

---

### Post by schorsch on 2007-08-09
It is called "libd[COLOR="Red"]b[/COLOR]us-1-2" ... you forgot the "b" in the name ....

---

### Post by zvacet on 2007-08-09
**synaptic>edit>fix broken packages**
or

```
sudo aptitude install kubuntu-desktop
```

---

### Post by crav on 2007-08-09
> **schorsch said:**
> It is called "libd[COLOR="Red"]b[/COLOR]us-1-2" ... you forgot the "b" in the name ....

You know, now I feel really, really stupid.
Thanks for pointing out my error!

---

