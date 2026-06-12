---
title: "Disable Touch-Pad Click"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by x02flash on 2008-01-20
Hey, recently I've been getting annoyed by the tap-click feature on my laptop's touchpad.  Is there any way to turn it off without disabling the rest of the touch pad?

Thanks In Advanced

-Alex

---

### Post by oldb0y on 2008-01-20
System>(Not the administration, but the other one)>Mouse
Go to third page an un-tick the tapping box:D

---

### Post by x02flash on 2008-01-20
> **oldb0y said:**
> System>(Not the administration, but the other one)>Mouse
Go to third page an un-tick the tapping box:D

No third page, only have "Buttons" and "Motion"

---

### Post by tact on 2008-01-21
I have my touchpad set up so that it is disabled for 2 seconds after any keypress.  Meaning I can type as hard and fast as I like and accidently brush the touchpad and it has no effect at all.

Once I stop typing, only after 2 seconds, then the touchpad is reactivated.  All automatic in ubuntu.  There are other options too - this is just how I set it up.

Without giving a step by step (search and you will find plenty of that) you need to basically:
1.   Install syndaemon
2.  add it to a startup session so its started whenever you boot
3.  small edit to xorg.conf

ciao

---

