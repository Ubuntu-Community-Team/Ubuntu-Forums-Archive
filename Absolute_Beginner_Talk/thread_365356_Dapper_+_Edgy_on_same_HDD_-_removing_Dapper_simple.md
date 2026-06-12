---
title: "Dapper + Edgy on same HDD - removing Dapper simple?"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2007-02-19
I have Dapper and Edgy installed on the same HDD on my laptop. I would like to delete the Dapper partition and merge it with the Edgy partition.

Now I popped the Live Edgy CD into the drive and booted from CD. Then I launched Gnome Partition Manager.

I clicked on the dapper partition (the smaller of the two) and clicked 'delete', then I clicked on the edgy partition and clicked on 'resize/move'. But, I can't resize it to take up the *preceding* space.

What is the most hassle free way of removing the dapper partition and adding the freed up space to the edgy partition?

(Also, if I remove dapper and then reboot, will Grub crash or will it allow me to boot into edgy even though dapper is gone?)

Screen shots of Gnome partition editor attached.

---

### Post by rsambuca on 2007-02-19
If you download the gParted live CD, it will probably work for you since it has a few features that aren't available on the ubuntu version.

[[COLOR="Red"]Link here[/COLOR]]("http://gparted.sourceforge.net/").

As for grub, if you loaded Edgy second, you will be fine, although the Dapper choices will still show up in the menu.  You can manually delete them quite easily in the /boot/grub/menu.lst file.

---

### Post by PartisanEntity on 2007-02-19
Thanks very much for the advice concerning gParted live CD, it took almost 2 and a half hours but it worked beautifully. Dapper is no more.

---

