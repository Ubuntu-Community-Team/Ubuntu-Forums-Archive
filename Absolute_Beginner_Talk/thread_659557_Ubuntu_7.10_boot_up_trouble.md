---
title: "Ubuntu 7.10 boot up trouble"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by dillon111222 on 2008-01-05
First my laptop specs are

AMD turion(th) 64 X2 Mobile
Technology TL-50
1.61 GHz, 992 MB of ram

graphics card is GeForce Go 6150its NVIDIA and has 256 mb memory

Ok so i made the live cd to boot up ubuntu 7.10 it burned fine and everything so i booted it up. It takes u to this screen that says install or safe install and some other options. I tried to boot up using the first option. I get to the part where its like all this info coming down the screen then after a few seconds of this  it goes to a black screen. I wait a few minutes try the touch pad click a few things but nothing happens. I ended up having to take the battery out of the laptop to shut it down.

I boot it back up and try going in the safe mode but the same thing happens. Ive tried doing that thing where u type no splash and delete quite but nuthen is working im about to give up on linux =( 

Any help u can give wuld be greatly appreciated.

---

### Post by mattismyname on 2008-01-05
Yikes!  That sounds bad.  There are two things I would try:

1) On the menu when you boot the CD, there is an item "Check CD for defects".  This will read the entire CD and perform a checksum to make sure it is all valid.  This will ensure it was burned properly and your CD drive is reading it properly.

2) On the menu when you boot the CD, there is an item "Memory test".  This will check that your system RAM is storing data properly.

There are other things you can try, but these two would be the most important for now.

---

### Post by dillon111222 on 2008-01-05
Already checked disk for defects ill try the memory thing right now thx

---

### Post by sowelie on 2008-01-05
Sounds similar to an issue I had.  Try hitting F6 after the cd boots when you get to the install menu.  Before the two dashes add noapic.  This should get you into the live environment.  You'll need to do the same thing for your first boot into ubuntu and then install the non free graphical drivers.

---

### Post by dillon111222 on 2008-01-05
well i tried the memory test and theres nuthen wrong with that .... i guess ill try adding noapic now

---

### Post by dillon111222 on 2008-01-05
k so i get in the live enviroment then what do i type in?

---

### Post by sowelie on 2008-01-06
Now you just need to install the OS by double clicking the install icon on the desktop.  Once it is done installing, on your first boot when you see the grub menu you'll have to edit the boot command again by pressing e.  Then add noapic in the same place you added it before.

Then, once you boot into ubuntu, install the proper video drivers and you won't need to use noapic anymore.  Do you have an nvidia card or an ATI card?

---

