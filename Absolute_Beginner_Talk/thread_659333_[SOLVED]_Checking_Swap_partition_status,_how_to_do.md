---
title: "[SOLVED] Checking Swap partition status, how to do this ?"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by Silvain on 2008-01-05
This is my output from free at terminal currently:

```

            total       used       free     shared    buffers     cached
Mem:        775536     707312      68224          0      91088     310136
-/+ buffers/cache:     306088     469448
Swap:       674688          0     674688
```

As you can see my system is using most of my RAM but has not used any of the swap partition yet. My question is, what command would show, if my swap partition is mounted / working properly ?

Also my system seems to be using much more RAM than in the past, not sure why that is either. Any suggestions on this issue would be helpful also .

TIA
Silv

---

### Post by SOULRiDER on 2008-01-05
Using RAM instead of Swap is good, swap is a LOT slower than RAM. Swap gets used only when it really is needed. 
```
Swap:       674688          0     674688
```
That means no swap is being used
```
-/+ buffers/cache:     306088     469448
```
Youre using 306088 of RAM and have 469448 free

---

### Post by dcstar on 2008-01-05
> **Silvain said:**
> 
........
As you can see my system is using most of my RAM but has not used any of the swap partition yet. My question is, what command would show, if my swap partition is mounted / working properly ?
........
```

swapon -s
```

---

### Post by Silvain on 2008-01-05
Oh, was looking at this part mainly.
```
            total       used       free     shared    buffers     cached
Mem:        775536     707312 
 
```

So the RAM being used for cache is still available for programs then ? Edit: Ok found another post that says this is available to programs. 

Tried the "swapon -s" command and got this :

```
 Filename                                Type            Size    Used    Priority
/dev/hda5                               partition       674688  0       -1 
```

Is this proper reply ?

---

### Post by dcstar on 2008-01-06
> **Silvain said:**
> 
........
Tried the "swapon -s" command and got this :

```
 Filename                                Type            Size    Used    Priority
/dev/hda5                               partition       674688  0       -1 
```

Is this proper reply ?

Yep, swap has not been used yet because you still have RAM available.

---

### Post by PeterJS on 2008-01-06
> **Silvain said:**
> 
Also my system seems to be using much more RAM than in the past, not sure why that is either. Any suggestions on this issue would be helpful also .


This isn't necessarily a bad thing, as long as you're not using swap there's no performance hit. Furthermore unused RAM is wasted RAM, linux likes to keep extra stuff in RAM for you, just in case you need it, like disk cache, and shared libraries that are common but might not be in use right this second. These extra bits of caching are marked as having a lower priority, so they offer a bit of speed up by trying to make a good guess at what would be useful to keep in memory. But if something comes along with a specific request the extra caching gets the boot.

---

### Post by Silvain on 2008-01-06
Thanks guys n gals for the informations. Ubuntu really does work entirely different than any  of the ugh , other unmentionable OS, I have used in past,  Lots more to learn still about Ubuntu here for sure.

---

### Post by il-luzhin on 2008-01-06
Various things could cause an increase in RAM usage, it all depends on what you've changed.  For example compiz for AMD64 has a minor mem leak that is not obvious over a few days of uptime but becomes more obvious after a few weeks.  If you run top regularly you can see what's using up your RAM and assess any changes.

---

### Post by dcstar on 2008-01-06
> **PeterJS said:**
> **This is necessarily a bad thing**,.........

Someone needs an edit, I think.........

---

