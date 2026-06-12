---
title: "Editing grub after taking off kubunu and leaving ubuntu"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by boyturtle on 2007-04-25
Complete Linux noob here and loving it. Installed Ubuntu first on the front end of my sata drive and just for a laugh I thought I'd try Kubuntu as well, only to discover that I couldn't get on with the gui.

Now I want to remove Kubuntu and my cunning plan to do this is to remove the partition with GParted; however, I am concerned that grub will throw a wobbly if I don't  do some programming there  and somehow change the settings. So my question is, how do I do this, has anyone done this before (stupid question) and what do i need to do?

If my cunning plan is not very cunning and there is a  better way of doing this, please let me know

BTW both are v 7.04

---

### Post by Ateo on 2007-04-25
Just reformat the partition you installed kubuntu on.

Check /boot/grub/menu.1st and probably remove any reference of kubuntu (if any).

---

### Post by kpkeerthi on 2007-04-25
boot with the live cd and run ```
sudo grub-install /dev/hdx
```

---

