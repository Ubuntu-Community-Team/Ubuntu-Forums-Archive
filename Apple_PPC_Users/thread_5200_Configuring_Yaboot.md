---
title: "Configuring Yaboot"
date: 2004-11-16
forum: Apple PPC Users
---

### Post by Viro on 2004-11-16
How do I configure yaboot so that it automatically boots the linux partition from the hard drive instead of providing me the option of booting from CD and then prompting me to hit enter to boot the linux partition?

---

### Post by oakz on 2004-11-16
Remove the "enablecdboot" line from /etc/yaboot.conf. I am not sure if it will prompt you for an OS since there is then only one choice. As far as the "boot:" prompt, the "timeout" value in /etc/yaboot.conf is the delay in booting the default image, in tenths of a second, so try setting it to 1.

-oakz

---

### Post by trash on 2004-11-16
you do need to run 'ybin' after changing things in yaboot

---

### Post by Viro on 2004-11-16
Will making this change mean that I can't boot from CD-ROM anymore?

---

### Post by trash on 2004-11-16
If holding 'c' or option key doesn't work on a reboot, then i guess you will have to edit yaboot again:)

---

