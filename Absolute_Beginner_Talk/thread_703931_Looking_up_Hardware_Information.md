---
title: "Looking up Hardware Information"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by spacefreak86 on 2008-02-21
Is there a way to look up what motherboard type and model you have? I know I've got a Gigabyte mobo because I was the one to install it, but I don't remember what socket it was or the number of PCI / PCI express slots it has in it.

---

### Post by overdrank on 2008-02-21
> **spacefreak86 said:**
> Is there a way to look up what motherboard type and model you have? I know I've got a Gigabyte mobo because I was the one to install it, but I don't remember what socket it was or the number of PCI / PCI express slots it has in it.

HI and the command ```
lshw | less
``` may help
Edit even better ```
 sudo apt-get install sysinfo

```

---

### Post by Presto123 on 2008-02-21
Well, for the socket, you could probably look up what kind of CPU you have and should get the socket number that way.

Otherwise...I usually just open the case if I forget something like that *shrugs*.

---

### Post by spacefreak86 on 2008-02-22
Solved. System info worked perfectly! Thank you.

---

### Post by vinutux on 2008-02-22
Plzzzzzzzzzzzzzz make u r post solver using [COLOR="Red"]**"thread tools"**[/COLOR]

---

