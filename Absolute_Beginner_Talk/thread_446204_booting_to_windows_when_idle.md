---
title: "booting to windows when idle"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by Jacks_Colon on 2007-05-16
This seems like a trivial problem but I cant find the answer. I am dual booting windows xp and ubuntu and when the option for an OS appears it boots to ubuntu when idle. Is there a way to make it boot to windows when idle?

---

### Post by icechen1 on 2007-05-16
> **Jacks_Colon said:**
> This seems like a trivial problem but I cant find the answer. I am dual booting windows xp and ubuntu and when the option for an OS appears it boots to ubuntu when idle. Is there a way to make it boot to windows when idle?

Yes you have to edit a file:
In a terminal
```
gksudo gedit /boot/grub/menu.lst
```
and change the number in default from 0 to where your windows entry is in the list(go to the bottom of the file to see your list).If is 3 then you tape 2
If you find this confusing,there is a less confusing tread in the forums,you can search it.

---

