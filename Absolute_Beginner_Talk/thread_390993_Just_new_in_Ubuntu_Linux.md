---
title: "Just new in Ubuntu Linux"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by afonulinx on 2007-03-22
Hi guys!

need you hlep!

I'm just new in ubuntu linux. I downloaded the new release 6.10 and try to install it to the new computer I have. 

After the installation it restart the system and the ubuntu splash appear for just 1% and I get the error message:

" Busy box V 1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)"
" Enter 'help' for a list of built-in commands."

"/bin/sh: can't access tty, job control turned off"
(initramfs)

Do you have any ideas on how to solve this problem? 

Thank you.

---

### Post by arochester on 2007-03-22
Look here: [https://launchpad.net/ubuntu/+source/initramfs-tools/+bug/67256](https://launchpad.net/ubuntu/+source/initramfs-tools/+bug/67256)

---

### Post by afonulinx on 2007-03-26
Thank you arochester for the info. however when I tried the command:

"sudo update-initramfs -u -k 2.6.17-10-generic"

It give me the error " /bin/sh: sudo: not found"

Is there things to be done to install sudo?

Hope your help.

---

