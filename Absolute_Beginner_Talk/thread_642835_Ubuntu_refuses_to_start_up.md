---
title: "Ubuntu refuses to start up"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by theBatman on 2007-12-17
I installed Feisty a few weeks ( possibly even months, it's been too busy for me to keep track) ago and just finally got around to using it. It worked great for 24 hours, then just suddenly decided not to start. It's stuck at the "Starting up..." message and refuses to go further.I can't even start in recovery mode. This is really frustrating me as my machine is completely crippled now. If I have to reinstall ubuntu then I'm going to say screw it and abandon the whole thing and go to another Linux OS. Please help!

---

### Post by theBatman on 2007-12-17
Also,if this helps, in recovery mode is locks up at this step and gives me a message like: "file DSDT not found"

---

### Post by kpkeerthi on 2007-12-17
[http://ubuntuforums.org/showthread.php?p=3888417](http://ubuntuforums.org/showthread.php?p=3888417)

---

### Post by theBatman on 2007-12-17
Um...that doesn't tell me anything :confused:

---

### Post by kpkeerthi on 2007-12-17
It does. One of the posts suggest you to turn acpi off in the kernel boot line.

---

### Post by kpkeerthi on 2007-12-17
When you are in GRUB. Highlight the kernel line and press 'e'. You will be in 'edit' mode. Go to the end of the line and append **acpi=off**. Press "esc' and press 'b' to boot.

To make the change permanent, edit /boot/grub/menu.lst, locate the kernel boot line and add **acpi=off**.

---

### Post by theBatman on 2007-12-17
Can you explain how I would do this? :confused:

EDIT: Looks like we posted at the same time. Thanks! :)

---

### Post by theBatman on 2007-12-17
> **kpkeerthi said:**
> When you are in GRUB. Highlight the kernel line and press 'e'. You will be in 'edit' mode. Go to the end of the line and append **acpi=off**. Press "esc' and press 'b' to boot.

To make the change permanent, edit /boot/grub/menu.lst, locate the kernel boot line and add **acpi=off**.
Ok, I did this and nothing changed. It's still hanging at the same spot :confused:

---

