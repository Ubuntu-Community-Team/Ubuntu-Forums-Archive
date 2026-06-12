---
title: "CPU Z for ubuntu???"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by The Jinx on 2007-10-21
Hello,

I am relatively new to using ubuntu and linux in general and i wanted to know if there was any programs like CPU-Z or CPU-ID for the M$ platform, but for Ubuntu that would tell me the specs of my computer(ram, ram lat, cpu, cpu multiplier, etc.)

If there is any terminal code line to find out this information may you put it in layman terms for I have no clue what so ever when i read other posts with terminal codes. May you like teach me step by step.

Thanks alot,
Eric

---

### Post by ed_d on 2007-10-21
use the man pages on lsattr (man lsattr) it will tell you everything you need to know. lsattr is list attributes. I use it in unix to tell me speed of a processor and also amount of memory in systems.

---

### Post by The Jinx on 2007-10-21
So do you just type "man lsattr" on a terminal screen and follow the prompted information?

---

### Post by The Jinx on 2007-10-21
can someone help i really don't understand what to do with "man lsattr"

---

### Post by nrfool on 2007-10-21
Maybe you should try the following command:
**sudo lshw -html > Myhardware.html**
This command will generate a html page containing you hardware information. You can them view it in any web browser

---

### Post by auxiliary.chipmunk on 2007-11-11
thanks this is great! works a treat

---

### Post by jordanmthomas on 2007-11-11
I know you found an alternative (which is great, and better than what I'm about to say) but for the record, cpu-z runs fine under wine.

So, had you wanted a particular feature, it's still available.

---

### Post by Skip Da Shu on 2007-11-11
> **jordanmthomas said:**
> I know you found an alternative (which is great, and better than what I'm about to say) but for the record, cpu-z runs fine under wine.

So, had you wanted a particular feature, it's still available.

Is there a good walk thru for a noob on installing wine?

---

### Post by jordanmthomas on 2007-11-11
1.  Open up Synaptic  (system --> administration --> Synaptic Package Manager)
2.  Go into its preferences and enable the "universe" repository
3.  click the reload button in synaptic to download the list of packages in the universe repository you just enabled.
4.  Search for wine and install it.

That's it, although, you may need to run ```
winecfg
``` after installing it. (press alt + f2 and type winecfg in the box)

After that, wine is installed

---

