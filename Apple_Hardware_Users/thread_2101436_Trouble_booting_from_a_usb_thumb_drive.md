---
title: "Trouble booting from a usb thumb drive"
date: 2013-01-04
forum: Apple Hardware Users
---

### Post by Nokeo08 on 2013-01-04
Hey guys,

I have a late 2008 2.4Ghz Intel Core 2 Duo MacBook 5,1 W/8GB 1067 MHz DDR3 and I would really like to dual boot my machine. SO last night I downloaded Ubuntu 12.10 64 bit and followed the instructions to make my SanDisk Cruzer Glide 64GB flash drive a bootable drive. I plugged it in rebooted my mac, held down option and waited. My internal drive, recovery partition, and thumb drive showed up. I picked the thumb drive and selected the option to try ubuntu out before I install. I was thrilled to see that everything worked out no problem. It sounds like my mac need some extra drivers to make the WiFi work, so I didn't install it then because it was late and I needed a direct connection to download the extra stuff anyway. I went to bed and woke today to do the install. I turn my mac on and did the same thing as last night, picked the same options and now all I get is a black screen with some lines up in the top left corner.

I tried again. Same result. I tried on my other usb port. Same thing. Tried Fedora. Same thing. I tried remaking the bootable usb drive in the terminal. Same thing. Next I tried a Transcend JF V30 2GB thumb drive I found in a drawer. Same thing. No matter what I try I get the same result. I don't understand why it won't work as nothing has changed from last night and it worked perfectly then. How can I fix it?

---

### Post by Isaacmarritt on 2013-01-08
no idea about your usb if you cant get it working maybe use a blank disc but here is the driver i used for my mac to get the wifi working:KS

---

### Post by Isaacmarritt on 2013-01-08
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by sudodus on 2013-01-08
> **Nokeo08 said:**
> I don't understand why it won't work as nothing has changed from last night and it worked perfectly then. How can I fix it?

Something has changed, otherwise it would work ;-) Did you make the flash drive with persistence?

Either the flash drive or the system in the computer has changed.

I would guess that the file system of the flash drive was damaged, when you shut down the computer. It is important to unmount it, 'software eject', which means that open files and buffered data will be written before it is unmounted (not available to read/write operations). And after that it can be unplugged physically.

In this case it should be safe to ***run the shutdown command properly*** and leave the flash drive in the computer until it is switched off.

If something like that happened, it will probably work if you re-format the drive and after that re-install Ubuntu.
--
But if Apple has designed its system to stop booting into other operating systems, it will be more difficult to solve. Then you need to get around that obstacle.

---

### Post by sudodus on 2013-01-08
> **Isaacmarritt said:**
> [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
If there is a switch or an entry in the BIOS menu to turn off the wifi, then try if that makes it boot from the flash drive!

---

