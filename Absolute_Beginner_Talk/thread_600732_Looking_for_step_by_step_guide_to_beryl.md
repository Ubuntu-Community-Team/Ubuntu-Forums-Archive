---
title: "Looking for step by step guide to beryl"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by Narrwald on 2007-11-02
Hey,

I am completely Linux illiterate. (At least for now.) I installed Ubuntu 7.10 on an external harddrive last night, and am running it now... I also installed beryl after searching around on Google for a guide telling me how. Nothing works, though. I have things like "Desktop Cube" and "Wobbly Windows" checked in Advanced Desktop Effects Settings, but it seems to do nothing at all...

I'm sure whatever I'm doing wrong is really stupid, but I've never touched Linux before, and this all seems foreign to me.

Thanks for any help.

---

### Post by Pumalite on 2007-11-02
[http://ubuntusoftware.info/beryl.html](http://ubuntusoftware.info/beryl.html)

---

### Post by Narrwald on 2007-11-02
Found that last night as well, forgot to mention:

At step 1, of all places, I'm stuck. I get this message when I put in what it tells me to on the terminal: [B]E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
[/B]

---

### Post by Narrwald on 2007-11-02
Never mind... Wrong step 1.

I just suck at this, that's all. Thanks!

---

### Post by jba6511 on 2007-11-02
beryl is no longer supported. Look at compiz fusion, which should be enabled by default in gutsy. You just need to install the configuration manager so you can set it up the way you want. Has all the features of beryl plus some.

---

### Post by mgmiller on 2007-11-02
> You just need to install the configuration manager so you can set it up the way you want. Has all the features of beryl plus some.

Correct.  Just fire up Synaptic package manager by clicking on System > Administration > Synaptic Package Manager  and search for compiz

Then put check marks next to compizconfig-settings-manager and also any of the compiz-fusion plugins that are there.

Click apply and when it's done, look in System > Preferences > Advanced Desktop  Effects Settings

Have fun.

(Yes, I know this can be done more quickly from terminal, but the OP should learn about synaptic)

---

### Post by Maestro23 on 2007-11-02
Compiz-Fusion in Ubuntu: [https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

---

### Post by por100pre1 on 2007-11-02
> **jba6511 said:**
> beryl is no longer supported. Look at compiz fusion, which should be enabled by default in gutsy. You just need to install the configuration manager so you can set it up the way you want. Has all the features of beryl plus some.
> **mgmiller said:**
> Correct.  Just fire up Synaptic package manager by clicking on System > Administration > Synaptic Package Manager  and search for compiz
Then put check marks next to compizconfig-settings-manager and also any of the compiz-fusion plugins that are there.
Click apply and when it's done, look in System > Preferences > Advanced Desktop  Effects Settings
Have fun.
(Yes, I know this can be done more quickly from terminal, but the OP should learn about synaptic)

**Read these previous posts carefully, no need to use other methods in Gutsy.**

---

### Post by Narrwald on 2007-11-02
There we go... Got it. Thanks guys.

---

### Post by SOULRiDER on 2007-11-02
Could you mark the thread as solved please?

Thank you <3

---

