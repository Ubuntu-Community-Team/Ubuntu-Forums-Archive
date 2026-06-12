---
title: "Install Grub after Windows"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by paladinhugo on 2006-04-09
Hello all!

I've installed Windows XP after installed Ubuntu and now my pc boots directly from Windows XP. How can I install grub again so that I can boot from Ubuntu again?

---

### Post by mlind on 2006-04-09
You need to boot using Ubuntu CD and enter rescue mode to reinstall GRUB.
see [Ubutu wiki]("https://wiki.ubuntu.com/SystemAdministration#head-2f326435bdb2aef79861d039744b03887dfa3dfd")

---

### Post by patrick295767 on 2006-04-09
knoppix live cd

then

fdisk /dev/hda -l

mkdir /mydisk

mount /dev/hda1 /mydisk

cd /mydisk/boot

blabla ....

grub-install 

which is in the /boot of you linux installed on the /dev/hdax 
x = value between 1 to ...

---

