---
title: "Having problems with Grub"
date: 2006-02-05
forum: Absolute Beginner Talk
---

### Post by benjiej on 2006-02-05
I have been having problems with Grub the last 4 days not installing on my /dev/hdb1. I have tried everything in these forumns. Does this command look correct "Verbatim" to get the /boot to work on my second HD?
"sudo grub-install --root-directory=/boot /dev/hdb1"

Thanks in advance for the help
Benjie

---

### Post by bartbes on 2006-02-05
It's because you have to install GRUB on your MBR (Master Boot Record) which is on your **first** drive (most likely hda1)

---

### Post by benjiej on 2006-02-05
When I install Grub on my MBR it Deletes the Windows XP Pro and gives me an error 17 which is the wrong HD mounted. After quite a bit of research I was able to determine that I can create a /boot on a second HD but I am new to Linux and no nothing of the command Syntax. That is the reason I needed to know if the command is correct Verbatim.

---

### Post by bartbes on 2006-02-05
it is correct, and it only overwriter the Boot record of Win XP Pro not everything

---

