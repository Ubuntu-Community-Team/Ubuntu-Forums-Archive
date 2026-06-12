---
title: "Ubuntu Installation"
date: 2008-02-20
forum: Apple Intel Users
---

### Post by Noob1234 on 2008-02-20
Hey guys,

Im currently running lepord and i want to install ubuntu so i can mess around with it and see if i like it.  The catch is that i dont want to get rid of OSX right now because im in school and i dont want to get rid of all my docs by way of a fresh format.

Can somebody run me through how to setup ubunto so that i can either select ubuntu or OSX at startup?

thanks
-Kyle

---

### Post by cyberdork33 on 2008-02-21
What kind of Mac do you have?

Installation is not too bad.
[LIST=1]
[*]First install [rEFIt]("http://refit.sourceforge.net/").
[*]Run Disk Utility and use the '+' tool to add a partition to your disc and size it to what you want for Ubuntu (this will shrink your OSX partition to make room). Don't worry about the format, just pick one (HFS+ is fine).
[*]restart, booting up the Ubuntu Live CD (did you see the refit menu?)
[*]Once you get into the desktop, start the partition editor from the menus.
[*]choose the partition you just made with disc utility and delete it. (This is likely the last partition on the disc. There will be an EFI partition, and your OSX partition in front of that.
[*]Exit the partition Editor and start the installer
[*]When given the option of where to install, choose "install in the free space"[/LIST]You shouldn't have an issue from there as far as getting things installed. Once you say what kind / version of a Mac you have, I can give you more info on configuring things to work properly.

---

### Post by Noob1234 on 2008-02-21
I have the latest macbook, 120gb HD INtel processor, 1gig ram, core 2 duo 2.16.

v10.5.1

-Kyle

---

### Post by cyberdork33 on 2008-02-21
[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

---

### Post by Noob1234 on 2008-02-21
am i running 32/64 bit?

-Kyle

---

### Post by cyberdork33 on 2008-02-21
> **Noob1234 said:**
> am i running 32/64 bit?
Please search a little for questions. There are 2 other topics on the front page of this forum discussion 32bit vs 64 bit... Either version will work fine, it is a matter of choice.

There is a advantages / disadvantages thread here. You can use that to make a decision on which you want:
[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

---

### Post by aztechclan on 2008-02-22
OSX Leopard comes with bootcamp installed.  I used that to resize my partition and reboot-install linux.  Then you just have to hold down the option key on boot to access OSX again.

---

### Post by cyberdork33 on 2008-02-22
> **aztechclan said:**
> OSX Leopard comes with bootcamp installed.  I used that to resize my partition and reboot-install linux.  Then you just have to hold down the option key on boot to access OSX again.
You can do the same thing in Disk Utility with Leopard

---

