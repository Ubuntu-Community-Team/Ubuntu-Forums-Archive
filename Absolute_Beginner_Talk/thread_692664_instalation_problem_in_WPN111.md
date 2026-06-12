---
title: "instalation problem in WPN111"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by ankitguptag18 on 2008-02-10
**i installed my netgear WPN111 using the following instruction. But after installing my pc gets Hanged as soon as i plug in the my USB WPN111...and i i try to start my comp with already pluged in then my comp does not start.... i started in night and till morning it did not start....Can any one Help me plzzz I cannot use internet on my comp.....**


)Install newest ndiswrapper + build-essential

2)Get the 3 files in the file I attached and drag them to the desktop

3)now install the drivers with ndiswrapper:

Code:



sudo ndiswrapper -i /home/<username>/Desktop/netwpn111.inf



4)Copy and paste this:

Code:



sudo ndiswrapper load_fw_ar5523 /etc/ndiswrapper/netwpn111/ar5523.bin



5)By now the blue light on the netgear usb should light. Now we need to make sure itll work even when we restart:

Code:



sudo depmod -a

sudo modprobe ndiswrapper

sudo ndiswrapper -m



Add the module to /etc/modules:

Code:



sudo gedit /etc/modules



Copy and paste the following to the bottom of the file. Save it. Close it:

Code:



ndiswrapper

---

### Post by ankitguptag18 on 2008-02-10
I m Using Ubuntu 7.04 feisty.

---

### Post by Erwin Criddle on 2008-03-05
Follow this tutorial:[http://ubuntuforums.org/showthread.php?t=652910]("http://ubuntuforums.org/showthread.php?t=652910")

It should be a lot clearer.

---

