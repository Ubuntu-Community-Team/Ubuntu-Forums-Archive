---
title: "Triple Boot - XP failing to boot"
date: 2008-02-29
forum: Apple Intel Users
---

### Post by dmitrijledkov on 2008-02-29
I had Leopard installed. I have install rEFIt and created 2 additional partitions (EFI - Machintosh HD - Ubuntu - Windows).

Then I have installed Windows and cood boot into Windows using both apple native EFI and rEFIt.
halts.
Then I installed ubuntu and grub. Now whenever I click on windows grub gets fired up and windows xp starts to boot up and then just.

But I really need Windows to be bootable. My menu.lst:
```
title           Microsoft Windows XP Professional
root            (hd0,3)
savedefault
makeactive
chainloader     +1

```

Please help.

---

### Post by cyberdork33 on 2008-02-29
See the multiboot guide in my signature. It would be helpful if there was some kind of error message or something when you try to boot windows. If there is nothing, you might need to boot form the install disc and do a repair.

---

