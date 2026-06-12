---
title: "Ubuntu installed on flash drive - Don't want to accidentally wipe entire mac HDD"
date: 2014-07-28
forum: Apple Hardware Users
---

### Post by mondonea on 2014-07-28
Good afternoon, 
     I have recently signed up for a linux class at my university and have decided to install ubuntu onto a jumpdrive to run on my mac.  I have installed 14.4 ubuntu onto the flashdrive and have gotten it to boot fine. I get prompted to choose what drive to install ubunto onto. I only see an option for my entire HDD. I want to make sure I am only wiping the flash drive and not the actual mac hard drive. Do I continue? Any help is greatly appreciated. 


Thank you,
    Anthony

---

### Post by Bucky Ball on 2014-07-28
Welcome. If you are intending to save your settings or anything else on the USB, using Mac or PC, what you are looking for is a persistence install, where Ubuntu is installed to the USB. You are probably trying to create a LiveUSB which allows you to run Ubuntu, but you can't save to it and all changes will be lost when you reboot the system (or unmount the USB). It is essentially a USB installer. 

You can create a LiveDVD or USB, boot from that and install Ubuntu to a USB dongle that way, but you'll get some clues here:

[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)

Hope that helps a bit. Good luck. ;)

(* Note: Running from a USB will be slower. It is pretty easy to install dual-boot and you'll probably be fine with it after a few Linux classes. You can always get help with it on the forums, too, of course. If you choose 'Something Else' when you get to the partitioning section of the install you can partition manually. You'll see the existing partitions there and they are set to 'not use' by default. Just avoid them.)

---

