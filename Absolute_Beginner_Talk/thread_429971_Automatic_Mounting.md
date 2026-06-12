---
title: "Automatic Mounting"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by Shack_ on 2007-05-01
I installed Feisty on my desktop. It has two hard drives, one with Windows on it. When I booted up for the first time, I noticed that the Windows drive appeared in File Browser, but in order to mount it from the GUI, I needed to supply an administrator password.

How can I set up Ubuntu so that the drive is automatically mounted and also available to all users?

---

### Post by taurus on 2007-05-01
You probably need to add an entry in /etc/fstab to have it mount automatically upon boot.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

