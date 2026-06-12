---
title: "New user questions."
date: 2008-02-29
forum: Apple Intel Users
---

### Post by damooster on 2008-02-29
I'm sorry if these questions have been answered, but I'm once again at work and trying to sneak this post in before the boss comes down to check on us.  :)

I bought a book called "A Practical Guide to Ubuntu," which you can find on the Barnes and Noble site, and it came with a live/install dvd of Ubuntu 7.10.

I partitioned my hard drive and was going to boot camp it, but I was distracted from my bird pecking at my ear and unwittingly chose the option to repartition the hard drive and install it to the entire disk.  Everything installed fine and I actually like it so far, but I noticed one problem (so far).

If I choose to put my computer on sleep/hibernate, it goes down like its sleeping but then freezes.  If I hit a key or press the mouse, it doesn't boot back up, and I end up having to hold down the power key and then press it again to power it up.

Any idea how to fix this?

---

### Post by banewman on 2008-02-29
How old is the mac?
Is it intel based?

---

### Post by damooster on 2008-02-29
I've had this iMac for about a year.  It is Intel based; it is the 17" Intel Core 2 Duo with a 2.0 processor, 2GB of RAM.

Sorry, I should have included this information earlier.

---

### Post by banewman on 2008-02-29
From google it seems suspend and resume isn't supported yet for your mac - sorry to say
I may be wrong but that is all I've found.
:)

---

### Post by damooster on 2008-02-29
Thanks banewman.  At least I now know that it's not fixable and I won't have to worry about trying to fix it!

---

### Post by cyberdork33 on 2008-02-29
Try changing this in /etc/default/acpi-support: 

```
SAVE_VBE_STATE=false 
POST_VIDEO=false
```

---

### Post by damooster on 2008-02-29
Thanks for the code, I will try that when I get home.

---

