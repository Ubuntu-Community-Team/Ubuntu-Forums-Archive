---
title: "External HD Woes"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by Ozwego on 2007-07-02
Hey, so I have ubuntu installed on my external drive.  I made the costly error of overwriting my mbr my first try, have since fixed that.  Now I have grub and ubuntu all on the same drive.  The only problem is, that when I first boot my computer, the drive is not detected.  So now matter what order I have my BIOS in, I only get the option to boot from cd or my internal drive.

When I connect the drive in windows, it says "Generic USB drive detected" -- but I am unable to interact with it in anyway.  It shows up in my device manager, but I can't do anything else with it.

Before I put ubuntu on it, the drive showed up and I was able to use it.  And I also have other external drives that are being used just fine in windows.  

So, any suggestions?

---

### Post by koshari on 2007-07-02
if you want to run ubuntu from a removable drive and DONT have a bios that allows for booting of a removable device the only practical way i can see is to make a small partition on your internal hard drive (with windows on it) and install grub on that.

you will still need the grub bootloader on hd0 partition however.

the better option is to install the drive internally, as a second drive as there wont be any trouble with grub seeing the removable drive as being not present if the drive is disconnected.

---

### Post by Ozwego on 2007-07-02
Sorry I didn't specify that did I -- my computer is able to boot from usb drives, and does detect my other external drives on boot.  Except for the drive that I have ubuntu installed on.

---

### Post by Ozwego on 2007-07-03
Nobody has anything I can do to get my drive to show up?

It shows up when I'm using the live install CD, but other than that I can do anything with it.

---

### Post by troseph on 2007-07-03
Do you have legacy USB enabled in your BIOS?

---

### Post by mysticrider92 on 2007-07-03
Ubuntu will probably have put an Ext3 partition type on the external drive, and Windows doesn't have drivers for that. As long as you aren't using Vista [these]("http://www.fs-driver.org/") drivers will allow Windows read and write access to the drive.

---

### Post by Ozwego on 2007-07-05
> **mysticrider92 said:**
> Ubuntu will probably have put an Ext3 partition type on the external drive, and Windows doesn't have drivers for that. As long as you aren't using Vista [these]("http://www.fs-driver.org/") drivers will allow Windows read and write access to the drive.

Thanks for that -- the drive now shows up in Windows.

But I am still not getting it to show up on my boot options.  Am only getting the choice between either my dvd drive, or internal notebook HD.  The thing that is getting me is that if I have my second external drive connected it shows up in my boot options, but if I have the external drive that has ubuntu on it connected I get nothing. 

My boot order has usb drives at the top.  And also how do  I check to see if I have legacy usb in my bios?  Is that just that if I can even boot from USB drives?

---

