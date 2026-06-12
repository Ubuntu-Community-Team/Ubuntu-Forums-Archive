---
title: "sound gone!"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by crav on 2007-05-02
after attempting to get dvds working [ [http://ubuntuforums.org/showthread.php?t=430292](http://ubuntuforums.org/showthread.php?t=430292) ] My computer has absolutely no sound! I'm killing myself over this! Does anyone know what went wrong?

---

### Post by igknighted on 2007-05-02
> **crav said:**
> after attempting to get dvds working [ [http://ubuntuforums.org/showthread.php?t=430292](http://ubuntuforums.org/showthread.php?t=430292) ] My computer has absolutely no sound! I'm killing myself over this! Does anyone know what went wrong?

Type the command 'alsamixer' in the terminal and make sure the important sound channels are not muted.  If you change anything, use the command 'sudo alsactrl store' to save the settings (after you quit the mixer).  If this still doesn't work, right click the volume changer on you panel and see if the device got set incorrectly.

---

### Post by crav on 2007-05-03
```
sudo: alsactrl: command not found

```
still no sound. any ideas?

---

### Post by igknighted on 2007-05-03
my apologies, its 'sudo alsactl store', but if the change didn't have any effect, no reason to save it

---

### Post by crav on 2007-05-03
I think the problem is that the bar on the far right (see previous attachment) has been disabled. How do I reenable it?

---

