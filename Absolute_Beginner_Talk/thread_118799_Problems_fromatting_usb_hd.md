---
title: "Problems fromatting usb hd"
date: 2006-01-17
forum: Absolute Beginner Talk
---

### Post by drumlight on 2006-01-17
Hi 
I've got a usb harddrive that I am trying to format with a linux filesystem using fdisk, have also tried GParted but am having the same issues.  I don't seem to be able to do very much to it in linux.  When I try to erase the existing partions i recieve a message warning me that the kernel uses the old partion table and that the new one will be available after reboot.
After rebooting the drive appears empty until i try to create a new partion when the old partion reappears, putting me back where I started trying to delete the existing partion. For instance currently fdisk reports> /dev/sda1               1       15017   120624021   83  Linux
 but upon mounting I see the old fat32 partion with all the existing data.
I have also tried starting with the disk unformatted, by using windows to delete all the partions. In this case I am unable to create the disklable, recieving a message that I am unable to write to the device.
Anyone with any help, is the process of formatting different for usb devices?
Where  might I be going wrong?

---

