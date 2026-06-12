---
title: "hp-toolbox and sd card access"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by SamMessing on 2006-11-15
I have a HP PSC 1610 all-in-one printer, and want to write data to a SD card. Using hp-toolbox I seem to be able to only download off of the SD card. Can anyone tell me how can I access / write to the SD card in my printer?

I've looked at the hp-toolbox's website, but the section about SD cards isn't up yet.


Thanks,

Sam

---

### Post by jimrz on 2006-11-15
> **SamMessing said:**
> I have a HP PSC 1610 all-in-one printer, and want to write data to a SD card. Using hp-toolbox I seem to be able to only download off of the SD card. Can anyone tell me how can I access / write to the SD card in my printer?

I've looked at the hp-toolbox's website, but the section about SD cards isn't up yet.


Thanks,

Sam

may be a permissions issue...try sudo

---

### Post by SamMessing on 2006-11-15
I don't think it is... running hp-toolbox as root doesn't give any other options.

Also doing the terminal command for specifically accessing the sd card:

```
 hp-unload -d %DEST%
```

doesn't do anything different either.


Is there a way I can mount it in the terminal and not use hp-toolbox, even though the card reader is in my printer?


Thanks!

Sam

---

