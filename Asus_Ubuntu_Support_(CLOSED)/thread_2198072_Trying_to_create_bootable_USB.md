---
title: "Trying to create bootable USB"
date: 2014-01-06
forum: Asus Ubuntu Support (CLOSED)
---

### Post by kneebreeated on 2014-01-06
I've got an ASUS U57A running Ubuntu 12.10, a PNY micro sleek 8GB USB flash drive, and an image of 'ubuntu-12.04.3-desktop-i386.iso' that I'm trying to use with the Startup Disk Creator to make a bootable USB drive. When I tell the SDC to Erase the Disk it gives me the following error message:
 
```
org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, 
the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```

please help a poor soul out.

---

### Post by sammiev on 2014-01-06
I prefer to use [UNetbootin]("http://unetbootin.net/"). To erase a USB I like Gparted and can be added from the software center. Besure to select your USB and not your HD when erasing or formatting.

---

### Post by C.S.Cameron on 2014-01-06
I usually format my flash drives FAT32 before using Startup Disk Creator.
I prefer SDC to UNetbootin myself, UNetbootin is sort of ugly.

---

### Post by kneebreeated on 2014-01-07
I tried using Gparted and unetbootin. I was able to successfully create a bootable usb flash drive, however it won't work on my ASUS only on a TOSHIBA I had on hand.

---

### Post by kurt18947 on 2014-01-07
> **kneebreeated said:**
> I tried using Gparted and unetbootin. I was able to successfully create a bootable usb flash drive, however it won't work on my ASUS only on a TOSHIBA I had on hand.

I have a somewhat similar situation with booting live USB.  I could create a live USB that a Thinkpad notebook would boot, a homebrew desktop would not.  Both machines were set to 'look' at USB-HDD before internal hard drive.  It *appears* - based on limited testing that if I press a "boot from this device" key (F12 in my case) I can boot live USB devices on the desktop.  Why does it appear necessary to manually select the USB device when BIOS is supposed to look for bootable USB devices before the internal hard drive?  I have no idea but that seems to be the case.

---

### Post by kneebreeated on 2014-01-07
> **kurt18947 said:**
> I have a somewhat similar situation with booting live USB.  I could create a live USB that a Thinkpad notebook would boot, a homebrew desktop would not.  Both machines were set to 'look' at USB-HDD before internal hard drive.  It *appears* - based on limited testing that if I press a "boot from this device" key (F12 in my case) I can boot live USB devices on the desktop.  Why does it appear necessary to manually select the USB device when BIOS is supposed to look for bootable USB devices before the internal hard drive?  I have no idea but that seems to be the case.

My case differs in that even after going into the BIOS and deleting all other booting options it won't boot from the usb.

---

### Post by kurt18947 on 2014-01-07
> **kneebreeated said:**
> My case differs in that even after going into the BIOS and deleting all other booting options it won't boot from the usb.

The only other suggestion which I doubt will help would be to first format the USB stick to FAT32 using Windows, rather than Gparted, startup disk creator or the original format.  Like I say, I doubt it'll make a difference but it might be worth a try.  Beyond that, have you tried another USB drive?  I wonder if there's something odd about the PNY stick and your Asus.

---

