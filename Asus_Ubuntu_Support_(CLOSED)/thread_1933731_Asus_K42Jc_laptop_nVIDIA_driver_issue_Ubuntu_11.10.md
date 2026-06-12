---
title: "Asus K42Jc laptop nVIDIA driver issue Ubuntu 11.10"
date: 2012-02-29
forum: Asus Ubuntu Support (CLOSED)
---

### Post by rocky125 on 2012-02-29
I recently bought the asus k42jc laptop. It has two VGA cards, intel and nvidia geforce 310m cuda 1gb. i would have never bought it i knew that before. Anyways, i tried to install windows xp but i couldn't find any supporting driver for nvidia 310m. Asus support site only had driver for windows 7, and the driver from nvidia was incompatible for XP so end up using windows 7 again.

I installed ubuntu 10.04 side by side with win7. I activated the nvidia driver, rebooted. It gets stuck/freezes after the ubuntu loading screen. I thought ubuntu 10.04 doesn't support dual vga laptops. so i tried installing ubuntu 11.10. Ran a full update. This case i got two options on driver to active. 1st was recommend, 2nd wasn't. I activated the 2nd one, reboot. everything seems fine. but the nvidia xserver runs with error. Can't use any effects using compiz manager either. Last option was to activate the 1st choice. But the screen freezes again after reboot. seems like ubuntu hasn't updated this issue on the new version as well. Not sure how am i able to find compatible driver for my laptop. Any help is really appreciated.

---

### Post by Ceriyx on 2012-03-06
Hi rocky125,
I have same laptop and am running 10.04. Solution is to install bumblebee:
[https://github.com/z0rc/debumblebee.git](https://github.com/z0rc/debumblebee.git)
Remove nVidia from your update sources
Good luck,
Ceriyx

---

### Post by rocky125 on 2012-03-08
Thanks, but ur link isn't working. I am searching for other sites regarding bumblebee.

---

### Post by Ceriyx on 2012-03-08
Maybe this:
**[driver - How well do laptops with [B]Nvidia** Optimus work? - Ask ...]("http://askubuntu.com/questions/36930/how-well-do-laptops-with-nvidia-optimus-work")[/B]


Good luck,
Ceriyx

---

