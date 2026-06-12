---
title: "need to gunzip or execute this file"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by mjp29 on 2007-06-19
the file is cnxtinstall.run

it appears to be a script when I look at it's properties with a right mouse click

do I gunzip it or what?

I'm quite the newbie, so tell me exactly what to type into terminal to make it execute  [please]

---

### Post by nine01a on 2007-06-19
Try "sh cnxtinstall.run".

Hth.

---

### Post by mjp29 on 2007-06-19
terminal reports back that it can't open it

I need to know exactly what to type first then second, etc...  (including any sudo) or do I need to gunzip it first (what do I type to do that), etc....

---

### Post by Bachstelze on 2007-06-19
YOu need to make it executable, and then run it :

```
sudo chmod +x cnxtinstall.run
sudo ./cnxtinstall.run
```

---

### Post by mjp29 on 2007-06-19
your first command I typed into terminal tells me no such file or directory even though it's sitting right there on the desktop called "cnxtinstall.run"

??

---

### Post by Bachstelze on 2007-06-19
It is on the desktop, but are *you* on the desktop ? ;)

```
cd ~/Desktop
```

---

### Post by mjp29 on 2007-06-19
now we're getting somewhere - thanks so much - you are very helpful [but i don't know if dial up is working again yet] but your specific instructions to cd ~/desktop really helped me a lot as of now.

i will test dial up modem to see if it works now and post back and complain later [lol!]

p.s. I had the dial up working fine and the evolution working fine until I allowed ubuntu to update the system.  Do you think my Uncle [his computer I'm setting up] will have to go through this again and again when ubuntu bugs him to do an update and he allows it to - ?

---

