---
title: "New 7.10 install and Compiz"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by mudflap5 on 2007-11-14
I've loaded a fresh copy of Ubuntu 7.10, did all of the updates, and now am trying to get Compiz up and running.  System, Preference, Appearence, then the Visual Effects tab, click on the "Extra" button and it says, " The Composite extension is not available". Can someone help out?
Thanks

---

### Post by Inxsible on 2007-11-14
What graphics card do you have ? Have you enabled the restricted drivers?

---

### Post by mudflap5 on 2007-11-14
> **Inxsible said:**
> What graphics card do you have ? Have you enabled the restricted drivers?

ATI X1300 is the card and the driver is the ATI accelerated graphics driver.

(And yes, it is enabled!)

---

### Post by DutyDuty on 2007-11-14
That' strange. You shouldn't have to go into that panel to run Compiz properly. What about compiz is not working?

---

### Post by Ub1476 on 2007-11-14
t's because you have an ATI driver, and the _stable_ ATI driver needs to run XGL in order for you to use compiz. Just open the terminal and  type in (or open nautilus and click your way):

```
 sudo apt-get install xserver-xgl
```

Now just log in and out and try to enable Compiz.

If you want extra effects, you gotta install the Compiz-settings-configurator (also found in synaptic).
```

sudo apt-get install compizconfig-settings-manager
```

XGL wont be necessary in the next Ubuntu release (April), since ATI will open they driver soon, and let's just hope they will release new good drivers every month, as they have promised to do.   

:)

---

### Post by kade on 2007-11-14
I recommend you read this post: [http://ubuntuforums.org/showthread.php?t=569654](http://ubuntuforums.org/showthread.php?t=569654)

It provides a good guide on how to get Compiz and Xgl working with Ati hardware (including your x1300).  Check out post #7 for the instructions on how to install the necessary packages.  It worked wonders for my x1400.  Good luck.

---

