---
title: "Feisty incomplete shutdown"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by woof603 on 2007-07-30
I have just installed Feisty on an old Dell win98.  Everything works fine except at the end of the shut down the screen shows the ubuntu logo.  The CPU seems to be in sleep mode as pushing the start button brings the computer instantly back to life.  Is this normal?
Thanks.

---

### Post by confused57 on 2007-07-30
> **woof603 said:**
> I have just installed Feisty on an old Dell win98.  Everything works fine except at the end of the shut down the screen shows the ubuntu logo.  The CPU seems to be in sleep mode as pushing the start button brings the computer instantly back to life.  Is this normal?
Thanks.
You can try this, worked for me:
```
sudo nano /etc/modules
```

add this line  to the end of the file:
```
apm power_off=1
```

---

### Post by Gen2ly on 2007-07-30
If that doesn't work, for now you should be able to manually shutdown the computer.  Type:
```
sudo shutdown -r now
```

---

### Post by timcredible on 2007-07-30
that's probably an acpi issue.  try system->administration->services and change the acpi setting (turn it on if it's off, turn if off if it's on).

---

### Post by p_quarles on 2007-07-30
> **Dirk.R.Gently said:**
> If that doesn't work, for now you should be able to manually shutdown the computer.  Type:
```
sudo shutdown -r now
```
That will reboot the system. Try this instead:
```
sudo shutdown -P now
```

---

### Post by Gen2ly on 2007-07-30
Doh, mb

---

### Post by woof603 on 2007-07-30
Thanks for the suggestions.

---

