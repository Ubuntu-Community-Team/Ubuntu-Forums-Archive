---
title: "Problem installing on tx1020ea (grub)"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by Bajsefg on 2007-11-05
Iv'e tried installing ubuntu 7.10 on my hp tx1020 with windows xp on it. 
And when I install ubuntu, grub will mess up so I can't dualboot my windows.

So I want to be able to use both xp and ubuntu. But I haven't got it working.
I guess that grub overwrite the MBR and remove the windows entry from there, but I don't have a clue how to make it work.

//Bajsefg

---

### Post by meierfra on 2007-11-05
You need to add windows to your grub menu.

Open a terminal in ubuntu (Applications->Accessories->Terminal.

Type

```
sudo fd
```

and 

```
cat /boot/grub/menu.lst
```

and post the output. Then we will be able to tell your how to edit "menu.lst"

---

