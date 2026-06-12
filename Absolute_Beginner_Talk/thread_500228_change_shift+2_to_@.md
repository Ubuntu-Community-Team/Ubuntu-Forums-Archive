---
title: "change shift+2 to @"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by Carlkiwi on 2007-07-13
How do I set the keyboard to show @ when I press the shift+2 key. This is what shows on my keyboard. I would also like for the " symbol to be in the regular spot as well

---

### Post by yabbadabbadont on 2007-07-13
In a terminal window run ```
dpkg-reconfigure console-setup
``` Make sure that you have selected the correct values for your keyboard.  If you make any changes, you will probably need to reboot before they will become active.

---

### Post by Carlkiwi on 2007-07-16
**This post could be related to an Ubuntu bug filed at**: /usr/sbin/dpkg-reconfigure must be run as root [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				n a terminal window run
Code:

dpkg-reconfigure console-setup

tried that but,

/usr/sbin/dpkg-reconfigure must be run as root

I am very much a ubuntu virgin and have no understanding on what this means.

Be gentle with me

---

### Post by Outrunner on 2007-07-16
```
sudo dpkg-reconfigure console-setup
```

---

### Post by Carlkiwi on 2007-07-18
Thanks

That works now.

---

