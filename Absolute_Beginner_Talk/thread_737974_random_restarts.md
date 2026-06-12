---
title: "random restarts"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by DaveGiant on 2008-03-28
From time to time my laptop just randomly restarts. Its not a complete restart. My screen goes black, some text comes on the screen then the login screen appears. I login and I am back to where I was. However I lose all of the work I am doing.

Does anyone have any idea what is causing this and how I might avoid this in the future.

---

### Post by Trail on 2008-03-28
X server might be crashing. Take a look at the logs.

(compiz?)

---

### Post by DaveGiant on 2008-03-28
Where can I find these logs, as the forum suggest, I am an absolute beginner :)

---

### Post by Trail on 2008-03-28
Inside the directory **/var/log/**

For example, Xorg.0.log (there should be more logs like this in similar filenames).

Look for errors, (EE) warnings (WW), etc.

For example, I get in my logs at some point:
```

(EE) NVIDIA(GPU-0): Your GeForce 8600M GS graphics card does not have the
(EE) NVIDIA(GPU-0):     necessary external power cables attached; X will not start
(EE) NVIDIA(GPU-0):     unless this is rectified.  Please shut down your computer,
(EE) NVIDIA(GPU-0):     open its case, and attach the appropriate power
(EE) NVIDIA(GPU-0):     connectors.  Your video card may have multiple power
(EE) NVIDIA(GPU-0):     connectors.  If so, each must be attached to a separate
(EE) NVIDIA(GPU-0):     power cable.  Please see the documentation provided with
(EE) NVIDIA(GPU-0):     your video card for more details.  If you think you have
(EE) NVIDIA(GPU-0):     received this message in error, you may specify the
(EE) NVIDIA(GPU-0):     "NoPowerConnectorCheck" X configuration option in the
(EE) NVIDIA(GPU-0):     Screen section of your X config file.

```

...which is because I removed the AC connector on my laptop :)

Optionally, if you wish to use the terminal, you can use the command:

```

grep -H '(EE)' /var/log/Xorg.*

```
 to search for all error messages in all Xorg logs. You can substitute (EE) with (WW) for warnings etc. (Basically, the third parameter there is a search pattern)

---

### Post by hyper_ch on 2008-03-28
are you sure it's not the screen saver kicking in?

---

### Post by stefangr1 on 2008-03-28
I had that to a while ago. Suddenly, after installing some updates, xorg crashed now and then. What solved it was in my case reinstalling the NVIDIA drivers.

---

### Post by DaveGiant on 2008-04-01
I have found the cause.

If I have Firefox, Scite and Filezilla running simultaneously. Then I minimize Firefox, my computer reboots. Well reboots in inaccurate. It just seems to drop everything and log me out.

Any ideas on how to fix this.

---

