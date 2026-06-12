---
title: "Putting Ubuntu On An External HD"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by Tenki on 2007-12-27
I was wondering if I could put Ubuntu on my external hard drive and have it so when my HD is plugged into my laptop that Ubuntu would load instead of Windows or maybe have some sort of dual boot. Something like that.

This is the HD I have. [http://www.westerndigital.com/en/products/products.asp?driveid=261](http://www.westerndigital.com/en/products/products.asp?driveid=261)

---

### Post by yamfox on 2007-12-27
[http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/](http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/)

---

### Post by GeorgiaBoot on 2007-12-27
Here is a How to I wrote with info I found on the web. I did this and it works perfectly. So basically when you plug in your HD and then turn the computer on you will have Linux.



Things you will need:

    * Ubuntu Linux (Free) [http://www.ubuntu.com/](http://www.ubuntu.com/)
    * A External Hard Drive
    * A Windows Machine, should work on Vista as well
    * A Little Time and Patience

Prep work:

    * 1. Download the LiveCD iso and burn to CD. Or have Ubuntu Ship you one for (Free).
    * 2. Prep your USB drive by deleting all partitions, no matter what kind they are.
    * 3. Disconnect your internal hard drive(s). This is Key
    * 4. Change your system BIOS boot priority by whatever procedure required for your specific hardware, to:
    * 1. CD
    * 2. USB
    * 3. Hard drive. 

If you cannot set the USB, because your motherboard is too old, this entire method will not work for you.

    * 5. Connect the USB drive
    * 6. Insert the LiveCD and boot your system
    * 7. When the Gnome desktop is visible and the Boot is complete select the following pull-downs from the menu:

System > Preferences > Removable drives & media.

    * 8. In the Removable drives & media window deselect:
    * * Mount removable drives when hot-plugged
    * * Mount Removable Media When Inserted
    * * Browse Removable Media When Inserted

    * 9. Close this window.
    * 10. Select the Install Ubuntu Icon and run through the install routine steps. When you get to the step regarding the hard drive, the easiest method is to select Use Entire Disk. You can partition out any space you require later.

    * 11. Run the installation. Even though the system says it will install GRUB to (hd0) the only drive connected is the USB drive, and it will place it in the right spot. Choosing sda or anything of that nature is not required by the new install cd.
    * 12. Restart the system when it is done.

Enjoy

---

### Post by Biggy on 2007-12-27
Thank you for this useful post GeorgiaBoot.

:)

---

### Post by Tenki on 2008-01-02
I have a few questions.

How do I disconnect the internal drive? Also, will disconnecting it keep all of my files intact?
How do you change the system BIOS boot priority?

---

### Post by SkylineGT-R on 2008-01-03
Why do I need to deselect "Mount removable drives when hot-plugged", "Mount Removable Media When Inserted", and "Browse Removable Media When Inserted"  I've seen that in a few tutuorials and I'm just wondering what that does.  

I'm brand new to linux..... :)

---

