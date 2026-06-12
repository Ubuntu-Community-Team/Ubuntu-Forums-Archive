---
title: "Startup Programs"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by valkarin on 2007-01-24
I am running Ubuntu 6.06 on a desktop and would like to remove gnome power managment from my startup sequence.  It is not listed in the **System-> Administration-> Services** program.  What file would this be in and how do I edit out the power manager?

---

### Post by compiledkernel on 2007-01-24
[http://doc.gwos.org/index.php/Speed_up_boot](http://doc.gwos.org/index.php/Speed_up_boot)

it is noted to be careful using this howto. It can cause system breakage if your not careful. That being said, sysv-rc-conf should be able to help you turn off what you want to turn off.

---

### Post by housam on 2007-01-24
Try this : system>>pref.>>sessions>> startup programs

---

### Post by tombott on 2007-01-24
I'm running Edgy 6.10 but hopefully this will be the same for 6.06

System - Preferences - Sessions

Click the Startup Programs tab,and in there you should find 'gnome-power-manager' highlight it and select Disable

Hopefully that sorts you

Tom

---

### Post by valkarin on 2007-01-25
Installed sysv-rc-conf.  It did the trick.  Thanks to everybody for their suggestions.

---

