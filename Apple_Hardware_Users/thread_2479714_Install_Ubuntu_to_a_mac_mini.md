---
title: "Install Ubuntu to a mac mini?"
date: 2022-10-04
forum: Apple Hardware Users
---

### Post by geordiejohn on 2022-10-04
Hello I have got a mac mini which is really slow and I was thinking of installing Ubuntu on it,to dual boot it looks complicated so I thought of a full install if it's not too hard to do if anyone can help please? 
Thank you.

---

### Post by MAFoElffen on 2022-10-04
I have an old MAC Pro that I have set up as dual boot. For a MAC dual boot, you just need to use the Disk utility to shronmk the partition to leave run to install to...

To install as a full install is easier...

The only main/big trick to install on MAC hardware is that you need to make sure that you have the USB LiveCD burned with a GPT partition table, and has UEFI boot. If you do not do that, then the MAC hardware will not recognize it as a Boot deivice. If making the bootable USB from Windows, then use those options in Rufus.

Next is that you hold down the option key as it boots, so that it looks for bootable devices...

Are you going to burn the USB from Windows? Linux? Or MAC?

---

### Post by ajgreeny on 2022-10-04
Moved to Apple Hardware Users.

---

### Post by geordiejohn on 2022-10-05
I burnt the usb from a chromebook. 
Thank you.

---

