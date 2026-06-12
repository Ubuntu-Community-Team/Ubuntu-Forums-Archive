---
title: "White screen after logon"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by cristian10 on 2007-10-08
Hi,

I new to this operating system and have been 2 days using it. Suddenly after logon I got a white screen. I have searched a bit around and noticed that there are some issues regarding nVidia graphic cards.

I am using a Toshiba Satellite P25/S477 with nVidia GeForce FX Go5200 graphics card.

How can I fix this? Is it possible to reinstall Ubuntu Feisty from scratch without loosing already downloaded files?

Thanks to any reply. 

If in spanish...better....

Cristian

---

### Post by molly_001 on 2007-10-08
When you boot Ubuntu, and it stops on white screen, hit CTRL + ALT + F1 .

Now Google:
   sudo dpkg-reconfigure xserver-xorg

You need to go through the dialogue and reconfigure your Xserver X Window manager settings.

Also, it is possible to install Ubuntu with /home directory on a separate partition, so that you can keep /home safe, even with totally re-installing Ubuntu on /(root) partition.

---

