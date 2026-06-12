---
title: "Where is boot?"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by Vuto on 2007-07-31
> Wait, maybe I'm missing something, but why not just reboot, hit Esc to enter the Grub menu, and boot with the 'recovery mode' option? That'll get you to a root console just fine.
Where is the grub menu? and how do you boot?

Thnx

~~~vuto~~~

---

### Post by wormser on 2007-07-31
When you boot the machine after the BIOS screen you should see the GRUB screen with a list of OS to boot into.  If you do not see that list then the default boot time might have been changed to zero.  This will make it boot directly into Ubuntu.  If that is the case then to change the default boot time edit /boot/grub/menu.lst.

```
sudo nano /boot/grub/menu.lst
```

Then just change the time out line to 10.  Now when you boot there will be a list to choose from.

---

### Post by mcduck on 2007-07-31
> **wormser said:**
> When you boot the machine after the BIOS screen you should see the GRUB screen with a list of OS to boot into.  If you do not see that list then the default boot time might have been changed to zero.  This will make it boot directly into Ubuntu.  If that is the case then to change the default boot time edit /boot/grub/menu.lst.

```
sudo nano /boot/grub/menu.lst
```

Then just change the time out line to 10.  Now when you boot there will be a list to choose from.

Even if the time is set to 0 Grub will still pop up a message telling you which key to press to access the Grub Menu. No matter what time you set, this message will always show for 3 seconds (if the menu itself isn't displayed).

---

### Post by Vuto on 2007-07-31
thnx i got it

---

