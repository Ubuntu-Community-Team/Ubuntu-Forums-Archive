---
title: "Extra Partition Showing Up"
date: 2008-10-04
forum: Apple Hardware Users
---

### Post by Jondi10 on 2008-10-04
I did a dual boot on my 3rd Gen Macbook Pro with 8.04 but when I boot it holding down the option key the rEFIt boot menu showing OSX and Ubuntu shows up but there's also another drive shows up that says Windows.  When I choose it it boots to Ubuntu also.  Not a different partition of it but the same as the one in the rEFIt menu.  I followed the instructions on the wiki creating a partition with Boot Camp and so on, and it installed with no problems.  Does anyone know why the second drive is showing up and boots to Ubuntu and is there any way to get rid of it without deleting the entire partition and starting over?

---

### Post by cyberdork33 on 2008-10-04
It sounds like you installed Grub to both the MBR and to the Ubuntu partition. You can clear the information in the MBR.
[http://ubuntuforums.org/showthread.php?t=811240](http://ubuntuforums.org/showthread.php?t=811240)

PS You do not hold alt to get to the refit menu. Holding alt will bring you to the default Mac boot chooser.

---

