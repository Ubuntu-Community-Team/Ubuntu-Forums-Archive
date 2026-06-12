---
title: "what files can be removed safely"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by gupta_sumesh63 on 2007-07-29
Certain files which are of no use take up lot of space. How can they be removed and which are they? I need to extract some memory space on my Hard disk.

---

### Post by kostkon on 2007-07-29
What type of files you mean? Also, where do you believe these files are located? If you mean personal files that are located in your home folder, more or less would be safe to delete them. 

A good way to find out is to run the *Disk Usage Analyser* that you will find at *Applications->Accessories*. This utility will analyse your disk, and it will show you with numbers and graphs the space, that each file and folder in your system, consumes.

---

### Post by FleetAdmiral74 on 2007-07-29
Extract some memory space? Is that another way of saying making more free space?
I would suggest first going through Synaptic and completely removing any programs you don't need. See if that clears it up, if not just come back here.

---

### Post by hyper_ch on 2007-07-29
In case you ahve downloaded and installed programs through synaptic, the .deb files are still in /var/cache/apt/archives

You could delete all of them:

```

sudo rm -Rf /var/cache/apt/archives/*

```

---

### Post by resistantgnome on 2007-07-29
> **hyper_ch said:**
> In case you ahve downloaded and installed programs through synaptic, the .deb files are still in /var/cache/apt/archives

You could delete all of them:

```

sudo rm -Rf /var/cache/apt/archives/*

```

I just followed what you said and now I can't run apt-get or aptitude
Whenever I do this,,,sudo apt-get update...i get an error message
> 
E: Archive directory /var/cache/apt/archives/partial is missing.


Now help resolving it.

---

### Post by resistantgnome on 2007-07-29
I just created partial folder and things seems to work again.

---

### Post by hyper_ch on 2007-07-29
oh, thx... didn't know about that...

---

### Post by logos34 on 2007-07-29
rather than delete everything in /var/cache/apt/archives/, you might want to move them off on to cd or dvd with **APTonCD**...So if you ever need to reinstall you don't have to re-download all those deb pkgs

---

### Post by AlexenderReez on 2007-07-29
don't remove manually ,please use aptoncd or

> sudo apt-get autoclean

---

### Post by resistantgnome on 2007-07-29
Why do you say...don't remove manually?

---

### Post by resistantgnome on 2007-07-30
*bump*

---

### Post by mcduck on 2007-07-30
> **resistantgnome said:**
> Why do you say...don't remove manually?

He means that you shouldn't go and remove apt's cached files by hand, or by using 'rm'. Instead you should use the tool made for the task, 'sudo apt-get autoclean' (to remove only cached .deb packages that are no more installed, or that are outdated) or 'sudo apt-get clean' (to remove all cache files).

This avoids the problem of possibly deleting the "partial" directory, and the command is shorter to type anyway ;)

---

