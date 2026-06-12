---
title: "Admin account deleted"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by redon12 on 2007-11-24
I made a new account checked all privileges and then logged there and deleted the first/main account after that all admin privileges were gone  please help
thank you

---

### Post by jordanmthomas on 2007-11-24
You'll need to reboot and select recovery mode from grub.
Once you're logged in there, run
```
gpasswd -a yourusername admin
```
replace yourusername with whatever your name is, of course.
This will add a user to the admin group so they can use sudo.

---

### Post by redon12 on 2007-11-24
how do I select recovery mode

---

### Post by taurus on 2007-11-24
When you first turn on your computer, you would see a message from the BIOS.  Then, you would see a message from GRUB and you have three seconds to press Esc key to bring up the menu.  The second option (usually) is the recovery mode so use the arrow key to highlight it and hit Return to boot from it.

---

### Post by LaRoza on 2007-11-24
> **redon12 said:**
> how do I select recovery mode

In Grub, if it doesn't show, press "ESC" before Ubuntu loads.

---

### Post by mikewhatever on 2007-11-24
> **redon12 said:**
> how do I select recovery mode

It's the second option in the boot menu. If you do not see the menu, hit esq at startup.

---

### Post by redon12 on 2007-11-24
thank you very much everybody problem is solved :)

---

