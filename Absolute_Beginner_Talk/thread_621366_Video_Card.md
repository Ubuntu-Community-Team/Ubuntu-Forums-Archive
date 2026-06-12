---
title: "Video Card"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by ubuntokun on 2007-11-23
my xserver not loading with Ati  Video CARD 7500c any suggestions?

---

### Post by overdrank on 2007-11-23
> **ubuntokun said:**
> my xserver not loading with Ati  Video CARD 7500c any suggestions?

Have you tried booting to recovery mode and reconfiguring your xorg at the  command line. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and answer a few questions and when complete use the command to reboot ```
sudo reboot
``` Hope this helps

---

