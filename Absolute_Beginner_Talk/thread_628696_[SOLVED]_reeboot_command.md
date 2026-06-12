---
title: "[SOLVED] reeboot command"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by Bheegerji on 2007-12-01
Whats the command to Rebot, Suspend, Hibernate and Shutdown?

---

### Post by mikewhatever on 2007-12-01
Open the terminal and type <man reboot>. Do the same for shutdown and halt.

---

### Post by fenian on 2007-12-01
reboot= sudo reboot

---

### Post by XVII on 2007-12-01
> **fenian said:**
> reboot= sudo reboot

I believe that this would be better than man reboot.

---

### Post by Dr Small on 2007-12-01
```
sudo reboot
```
```
sudo shutdown -r now
```

---

### Post by mikewhatever on 2007-12-01
> **XVII said:**
> I believe that this would be better than man reboot.

First, reboot!=sudo reboot, no way. Second, man reboot provides useful info on syntax and options instead of spoon feeding.

---

### Post by Dr Small on 2007-12-01
> **mikewhatever said:**
> First, reboot!=sudo reboot, no way. Second, man reboot provides useful info on syntax and options instead of spoon feeding.
I thought you had to use sudo in order to use reboot ?

---

### Post by mikewhatever on 2007-12-01
> **Dr Small said:**
> I thought you had to use sudo in order to use reboot ?

I thought so too, that's why reboot!=sudo reboot. Different privileges.

---

### Post by fenian on 2007-12-01
Most of the opttions for reboot (-n,-h,-i) are handled automatically by the linux kernel.sudo reboot does the same thing as rebooting from the GUI.

---

