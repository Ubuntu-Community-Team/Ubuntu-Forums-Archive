---
title: "No bootable device."
date: 2013-01-24
forum: Any Other OS
---

### Post by ooooooooooooooooooooooooo on 2013-01-24
Okay - i did a fresh arch install from ubuntu and everything went smoothly until grub-bootloader would not install. I decided to start over, so i rebooted - i kept the usb hooked up and booted off of it. No bootable device found. Tried with the HDD. No bootable device found. It is on my netbook, i deciced to stop using 12.10 because it was too heavy and i wanted to use openbox on Arch Linux.

My computer is a Gateway LT4008u (Same as Acer Aspire One, Gateway is owned by Acer, its like a Honda - Acura relationship.)


Computer came with Windows 7, should i have used grub? I did on my 7 - ubuntu dual-boot before i ditched windows.

Oh, BIOS setup menu recognizes the device, and i have no way to repair it from there (no option for it) but once i boot, it cant find any devices. How ca i fix this? do i need to reformat the drive with another computer? did i fu- mess up the master boot record?

---

### Post by ooooooooooooooooooooooooo on 2013-01-25
I get this error no matter what i am booting off of, whether it is a usb, cd, or HDD, i think whatever bootloader i am using is bad. Cant repair hard drive or anything from BIOS.

---

### Post by ooooooooooooooooooooooooo on 2013-01-25
Wait... when i plug the USB into my mac to put another installer in it, it says "device not readable..." so i am going to reformat it to MS-DOS and put a ubuntu installer on it. Ill try it in the mac, and then if it is readable, put it in my Gateway and try it.

---

### Post by ooooooooooooooooooooooooo on 2013-01-25
Gateway says: No operating system. Im pretty sure that im supposed to format it to MS-DOS (FAT) right? 
What is the partition type for unetbootin to make an installer that works?

---

### Post by lisati on 2013-01-25
Threads merged: multiple threads for the same problem tends to dilute the community's ability to help.

Please go easy on the bumping: the usual rule (found in the forum [code of conduct]("http://ubuntuforums.org/index.php?page=policy")) is to wait 24 hours.

---

### Post by howefield on 2013-01-26
Thread moved to the "*Other OS/Distro Talk*" forum.

---

### Post by vcrewchief on 2013-02-03
thanks for the link to the new thread.

---

### Post by iamkuriouspurpleoranj on 2013-02-05
With Arch you cannot use UNetbootin.

You want to use "dd":

Be very careful because one false move and you'll wipe your harddrive.

Format your USB to FAT 32. Don't ask why it helps, just do it.

Go to the folder where your iso is and type the following command:
sudo dd bs=4M if=whateverthearchisoiscallingitselfthesedays.iso of=/dev/sdX

Replace X with the device name of your USD i.e. /dev/sdb or /dev/sdc typically. Just make sure it isn't your main drive. In fact, assess the lay of the land by typing lsblk into a terminal before you start.

Then wait a good five minutes after the cursor reappears for your USB to finish, as it is often not finished even though you get a prompt.

But really, this is a beginner question and it suggests that maybe you're not ready for Arch yet. If you want an Openbox distro, CrunchBang is very good and because it's essentially Debian, you'll find much that you recognise from Ubuntu.

---

