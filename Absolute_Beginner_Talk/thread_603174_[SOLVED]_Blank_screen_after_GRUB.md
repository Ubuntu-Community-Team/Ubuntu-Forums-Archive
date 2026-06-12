---
title: "[SOLVED] Blank screen after GRUB"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by machavillain on 2007-11-04
The chain of events:

1. I had dual boot of XP and Ubuntu 7.04

2. Used Partition Magic to eliminate Ubuntu partitions.

3. Rebooted; got "error 22" from GRUB - couldn't get to either OS.

4. Installed Ubuntu 7.10 (as dual-boot).

5. Now, XP works fine, but when I select Ubuntu from GRUB, get blank screen.

Any suggestions ?

---

### Post by overdrank on 2007-11-04
> **machavillain said:**
> The chain of events:

1. I had dual boot of XP and Ubuntu 7.04

2. Used Partition Magic to eliminate Ubuntu partitions.

3. Rebooted; got "error 22" from GRUB - couldn't get to either OS.

4. Installed Ubuntu 7.10 (as dual-boot).

5. Now, XP works fine, but when I select Ubuntu from GRUB, get blank screen.

Any suggestions ?

Hi, if you can boot into recovery mode it will be command line. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and answer a few questions and when complete use the command to reboot ```
reboot
``` Hope this helps and good luck!

---

### Post by machavillain on 2007-11-04
Thanks for the quick reply - how do I log in on the command line?

---

### Post by machavillain on 2007-11-04
I did figure out how to log in, but I entered this command, it seemed to work fine, but unfortunately no change.

The message I get before the black screen starts with "Cannot allocate resource region..."

Any more ideas? Thanks again.

---

### Post by machavillain on 2007-11-05
turns out the black screen does eventually turn into the login screen, as described elsewhere - I just didn't wait long enough.

---

