---
title: "Ever increasing ETHX"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by Skarlso on 2008-03-18
Hi!

I have an interesting problem!

I just freashly installed Ubuntu. I have various problems, like... It can't detect my video card normally. The Hardware list is full of unknow stuff and i tryed to refresh everything. I also have the latest glx-new direvers from nvidia. Still it is unknown.

AND.

To that comes that every time i reboot, the EHT increases by one... Currently i'm at eth13... WTF?? I never ever experienced something like this with other distros. Is this normal? I think not... I think it's maybe connected to the fact that it can't detect my video card, because on windows i can see that its and nvidia network adapter which is kind of strange... Any thougths on this one??

Any help is very very well appriciated! Thank you!

Gergely

---

### Post by PmDematagoda on 2008-03-18
What Nvidia VGA card are you using?

---

### Post by Skarlso on 2008-03-18
I'm using a laptop card : nvidia GeForce 8400M G card.

Btw i tryed reinstalling ubuntu and i've got the same. Currently i'm at eth04

---

### Post by Skarlso on 2008-03-18
Also i tried to install some packages for myu video card, but nothing seams to help. Also i know that this is a problem that is very rare. It should not happend but it happnes. :(

---

### Post by Skarlso on 2008-03-18
Does nobody have any ideas? :(

---

### Post by Skarlso on 2008-03-18
Why does it find a new Network card by every boot?

---

### Post by Delkster on 2008-03-18
Could you post output from the following commands:
```
dmesg
```
```
lspci
```

---

