---
title: "PowerBook G4 / Gustsy - sound problems"
date: 2007-11-22
forum: Apple PPC Users
---

### Post by davduf on 2007-11-22
Hi All,

Everything's fine with Gusty install (an upgrade from Feisty), except for the sound. I can't get sound.

Do you have the same problems? How to install driver for the 17" G4 PowerBook?

All my thanks,

D.

---

### Post by sportjunkie on 2007-11-22
Try to load the snd-powermac module

```
sudo modprobe snd-powermac
```

If that works make it permanent with

```
sudo echo snd-powermac >> /etc/modules
```

And please next time before you post use the search function - cheers.

---

### Post by davduf on 2007-11-25
> **sportjunkie said:**
> Try to load the snd-powermac module

```
sudo modprobe snd-powermac
```

Thank you so much. it works!


[QUOTE]
If that works make it permanent with

```
sudo echo snd-powermac >> /etc/modules
```

And please next time before you post use the search function - cheers.

OK. What do you  mean exactly? What i have to do exactly ?

Thank you so much!

---

### Post by sportjunkie on 2007-11-25
What I meant is, that with the first command I posted the kernel module for the sound device is only loaded as long as you not switch off the pc. You have to type in this command each time you start your pc and want to use the sound device. To tell the OS to load the module each boot you have to add the module name into the modules file /etc/modules. You can do this with an editor or with the second command I posted.

Hope that explains it a bit. Otherwise try to find an article about kernel modules.

---

