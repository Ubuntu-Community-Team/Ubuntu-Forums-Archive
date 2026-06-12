---
title: "ibook G4 light"
date: 2007-05-22
forum: Apple PPC Users
---

### Post by Xenner on 2007-05-22
I have noticed that the default gentoo packages utilize the light on the ibook as a harddrive activity light, is there any way to do this in ubuntu as well?

---

### Post by stmiller on 2007-05-22
This is an option that must be enabled in the kernel. It's not on by default in the stock ubuntu kernel. So unfortunately you'd have to recompile your own kernel and enable this option. :(

---

### Post by Xenner on 2007-05-22
well do you know what the option is called, so i can go ahead and do that?

Thanks!

---

### Post by stmiller on 2007-05-22
I think it's somewhere in here:

```
 
Device Drivers>
Block devices  --->
    ATA/ATAPI/MFM/RLL support --->

            [*]       Blink laptop LED on drive activity

```

---

