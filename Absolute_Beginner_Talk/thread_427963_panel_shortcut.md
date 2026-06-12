---
title: "panel shortcut"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by supersonicdarky on 2007-04-29
i made a shortcut in the panel to a virtual maching but it isnt working. when i paste the code into terminal it loads

qemu -hda ~/c.img -m 320 -soundhw sb16 -localtime &

tried both application and application in terminal

?

---

### Post by starcraft.man on 2007-04-29
> **supersonicdarky said:**
> i made a shortcut in the panel to a virtual maching but it isnt working. when i paste the code into terminal it loads

qemu -hda ~/c.img -m 320 -soundhw sb16 -localtime &

tried both application and application in terminal

?

Ummmm, do you mean that you made a shortcut for a virtual machine program? In other words you made a shortcut to a wine program... I find its easiest to execute it via wine. It's easy enough to just make a script that execute the terminal command : 

```
wine <program>
```

that should do it no?

---

### Post by supersonicdarky on 2007-04-29
not not a wine prog, i make a shortcut to [qemu](http://fabrice.bellard.free.fr/qemu/).

---

