---
title: "How do I Un-Installing .DeB Package?"
date: 2005-12-22
forum: Absolute Beginner Talk
---

### Post by nitricacid on 2005-12-22
Say I want to Uninstall this app nerolinux-2.0.0.4-x86.
How would I go about doing it?

I can't remember if you can do it from synaptic or not.
I didn't install it using the synaptic but it shows up on the list when I search for 'Nero'.
(I downloaded (from nero site) & Installed it through 'Terminal>Sudo dpkg -i nerolinux-2.0.0.4-x86.deb')

Thanks

---

### Post by GoldBuggie on 2005-12-22
1) You can uninstall it using synaptic.
2) you can do a sudo apt-get remove <package>
3) you can do a sudo dpkg -r <package>

---

### Post by nitricacid on 2005-12-22
Danke schön :)

---

