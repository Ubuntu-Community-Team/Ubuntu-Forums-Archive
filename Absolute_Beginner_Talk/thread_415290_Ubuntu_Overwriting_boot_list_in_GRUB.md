---
title: "Ubuntu Overwriting boot list in GRUB"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Gentex on 2007-04-20
Recently Ubuntu has been overwriting my menu.lst file in GRUB, replacing the list of available OS with a list of 6-8 ubuntu options.  This leaves me without WinXP as an option.  I have to manually edit the menu.lst to add WinXP and reboot to get into Windows.  Any ideas what might be causing this, or how to fix it?

TIA

Gentex

---

### Post by Bachstelze on 2007-04-20
Remember to add your Win XP option **after** this line :

```
### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by Gentex on 2007-04-20
> **HymnToLife said:**
> Remember to add your Win XP option **after** this line :

```
### END DEBIAN AUTOMAGIC KERNELS LIST
```

I'll check that.  Thanks.

Gentex

---

