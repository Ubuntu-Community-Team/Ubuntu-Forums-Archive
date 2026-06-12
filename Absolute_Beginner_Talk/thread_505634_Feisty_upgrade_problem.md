---
title: "Feisty upgrade problem"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by zeusconnection on 2007-07-20
Hi there
Please I need to resolved this problem. I was using LTS (Unbuntu 6.06)  quiet while I have temptation to using Feisty(Ubuntu 7.04) I get the Ubuntu alternate iso image and doing a CD  upgrade everything going well after complete the upgrade I restart the comp I end up on the text mode no GUI.  First I look in the forum and some solution like : 
* sudo /etc/init.d/gdm start

* ctrl + alt + F7

* sudo dpkg-reconfigure xserver-xorg

* ctrl + alt + backspace

*sudo dpkg-reconfigure -phihg xserver-xorg 

* sudo aptitude update

*  sudo aptitude dist-upgrade

* sudo dpkg --configure -a

none of them works
Anyone can help me please :confused:

---

### Post by Seisen on 2007-07-20
Are you using an graphics drivers.

---

### Post by zeusconnection on 2007-07-20
Are you using an graphics drivers
No 
I did not add nothing  just upgrade from LTS to Feisty with the 7.04 alternate  CD

---

### Post by Seisen on 2007-07-20
Try this

```
sudo apt-get -f install
``` maybe not all of the packages installed correctly.

---

### Post by zeusconnection on 2007-07-20
Thanks for the reply 
I run the command : sudo apt-get -f install
it stop with this error message
E:subprocess /usr/bin/dpkg return error code (1)

---

### Post by mikewhatever on 2007-07-20
You can't  upgrade from 6.06 to 7.04 directly. Not sure how you did it, but the right way seems to be 6.06=>6.10=>7.04.
[https://help.ubuntu.com/community/UpgradeNotes?highlight=%28upgrade%29](https://help.ubuntu.com/community/UpgradeNotes?highlight=%28upgrade%29)

---

### Post by MurphysLaww on 2007-07-20
I think I may be having the same issue. If we were not supposed to upgrade directly to feisty, what now?

Mine is saying that it can't start xwindows. 

Is it due to something happening to the Nvidia drivers not having upgraded correctly?

---

### Post by zeusconnection on 2007-07-20
thanks for the guidance
I did read this document  before do the upgrade but I came a cross the alternate CD and 
I realize I miss understand how the process  work that why force this upgrade
I do not know if it have any way to resolved that instead of a clean installation :confused:

---

