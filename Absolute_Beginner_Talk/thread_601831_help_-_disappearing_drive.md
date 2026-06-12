---
title: "help - disappearing drive"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by samcampbell on 2007-11-03
Downloaded and installed 7.10 alternate. First attempt failed with corrupt files at e2fsprogs.
2nd attempt seemed to go fine. I have two drives one with windows xp  installed , the other which was empty is where I installed ubuntu. Now when I start up I get no choose Os page , and the drive has vanished from the control panel. It does still appear in system device manager. Any easily understood solutions welcome. previosly I tried the desktop 7.1 but it hung at keyboard selection. So I am still stuck with WXP

---

### Post by Pumalite on 2007-11-03
Two drives? IDE and SATA?
Did you install with one disconnected?

---

### Post by samcampbell on 2007-11-03
yes IDE and SATA  - no none disconnected. The SATA has wxp the ide ubuntu

---

### Post by Pumalite on 2007-11-03
Boot from Live CD, mount IDE drive, from the terminal:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by samcampbell on 2007-11-03
tried that no sucess. Loading from CD I got a fail for loading hardware drivers, but went on to type as suggested. Shut down to reboot and got Fail in Stopping periodic command. Eventually pressed the restart button and just got the same reboot into XP and the drive still missing. I am giving up for the night. Will try any ideas tomorrow.
sam

---

