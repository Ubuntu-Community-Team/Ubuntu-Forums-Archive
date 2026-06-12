---
title: "Grubby"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by youdidntseenothing on 2007-07-02
can i configure GRUB to make winxp the default? like when i boot, its already highligted as winxp> is it possible to do it from ubuntu? thanks

---

### Post by Inxsible on 2007-07-02
yes you can. 

Look for a line that says  "default 0" without the quotes in /boot/grub/menu.lst. Change that number to the whatever your Windows XP entry is. Make sure you count the title for "Other Operating Systems" also. [COLOR=Red]And the count is 0 based. [COLOR=Black]So if you Windows entry is the 4th, you will have to put in 3[/COLOR][/COLOR]

---

### Post by youdidntseenothing on 2007-07-02
i cant save it
its read only

---

### Post by lisati on 2007-07-02
try from a terminal
```

sudo gedit /boot/grub/menu.lst

```

You might get asked for a password, use the same one you signed in with. You might also have to use the following once you've edited and saved menu.lst to your satisfaction:
```

sudo update-grub

```

---

### Post by youdidntseenothing on 2007-07-02
thankkks

---

### Post by Peter6218 on 2007-10-26
> **lisati said:**
> try from a terminal
```

sudo gedit /boot/grub/menu.lst

```

You might get asked for a password, use the same one you signed in with. You might also have to use the following once you've edited and saved menu.lst to your satisfaction:
```

sudo update-grub

```

Is there anyway to get grub to see more than one other operating system??

just installed feisty and it only found the winXP HD. It's over on the RAID card plus another HD with win98. I'd like to be able to access 98 as well.

We really need a little program to scan machines and vreate a better grub menu.lst. One that you can set priorities on and will find other OS's?

---

