---
title: "Ubuntu &amp; Vista...make Vista the default boot"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by mikawber on 2007-02-03
I recently installed Ubuntu and Windows Vista Business. I want to know how to boot into Windows Vista by default instead of having to choose through Grub. Is this possible?

Thanks!

---

### Post by PhrankDaChickenGeek on 2007-02-03
Boot into Ubuntu
Open a terminal (App -> Acc -> Term.)

```

cd /boot/grub
gksudo gedit menu.lst

```

This will open the grub config file. Type in your password

Scroll to the bottom of the file and find the line "savedefault" under the Ubuntu boot options
Cut this line and paste it into the same place under the Vista boot options
Save, exit and reboot!

---

### Post by ade234uk on 2007-02-03
As far as I know you will have to use Grub if you still want to use Ubuntu. But you may be able to select which operating system to start as default by modifying it.

---

### Post by Tomosaur on 2007-02-03
You can set grub to boot into Vista by default by working out the number of Vista in the boot menu. The first item in the boot list is 0, second is 1, etc etc. The 'Other Operating Systems' line should be included in the count. Then you need to open the boot config file (in Ubuntu):
```

gksudo gedit /boot/grub/menu.lst

```

And changing the 'default' line from zero, to whichever number Vista is.

Alternatively, check the link in my sig.

---

### Post by meborc on 2007-02-03
i would open the menu.lst file (as directed in the first reply) and then change the default value from 0 (the first line in grub) to 4 (the windows row... in case only 1 kernel version installed...)

you can try switching this number as it changes the default selection of grub menu

EDIT: ahh... i was too slow :)

---

### Post by mikawber on 2007-02-03
thank you all very much for your quick replies! I will try it right now and let you know!

---

