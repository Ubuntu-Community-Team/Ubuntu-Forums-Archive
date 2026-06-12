---
title: "help! kubuntu crashed"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by mendingo84 on 2006-10-16
i just crushed my kubuntu... i opened konsole,pressed CTRL+ALT+F1 then didn't know how to exit there so i restarted my computer and...surprise...kubuntu won't boot! booting process freezes while "mounting root filesystem". any sugestions?

---

### Post by pbaehr on 2006-10-16
1) For future reference, to restart from the console:
```
sudo shutdown -r now
```
2) Can you boot to the recovery console? You should be able to select it from Grub if you haven't modified your menu.lst file.

If you can get to the recovery console, let us know and someone may be able to help you from there. Using your Live CD is also an option.

---

### Post by mendingo84 on 2006-10-16
i am able to get in recovery console and i even entered kde now...any further instructions plz...?

---

### Post by Bachstelze on 2006-10-16
Now try to reboot in normal mode and see if it works ;)

---

### Post by mendingo84 on 2006-10-16
wow...:)...this made me feel stupid :D...ok, so...if not asking to much, can someone tell me what just happened? :confused:

---

### Post by pbaehr on 2006-10-16
I doubt anyone will have a firm explanation. Every now and then these things happen. Just be glad it's working again!

---

### Post by Bachstelze on 2006-10-16
Probably the filesystem was a bit upset by the harsh reboot, so it couldn't be mounted during a "normal" boot. The "recovery" boot forced the filesystem to be checked and repaired the error, letting the filesystem clean again for a normal boot sequence.

---

