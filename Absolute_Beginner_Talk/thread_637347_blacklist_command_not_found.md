---
title: "blacklist command not found"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by soviet911 on 2007-12-10
hi im trying to blacklist prsim2_pci driver but cant since it tells me
sudo gedit/etc/modprobe.d/blacklist prism2_pci
sudo: gedit/etc/modprobe.d/blacklist: command not found

and same happens when i try to do just blacklist prism2_pci got no clue why it doesnt work and i did instal gedit tool.

---

### Post by Teknyk on 2007-12-10
Are you trying to add prism2_pci to /etc/modprobe.d/blacklist ?

If that is the case just do sudo gedit /etc/modprobe.d/blacklist

and add "blacklist prism2_pci" without the quotes to the bottom of the list. Then save and close the file.

Before you do that though are you following a walkthrough of some sort?
what is the issue you are tring to fix?

---

### Post by soviet911 on 2007-12-10
Thank you that helps and yes im trying to get my wireless card to work and following a tuorial.

---

