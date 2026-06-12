---
title: "Difficulty installing Ubuntu from USB on late 2007 MacBook 10.7.5"
date: 2018-11-08
forum: Apple Hardware Users
---

### Post by trixyu on 2018-11-08
Hey everyone, 

Posted this on Reddit a while ago, but it didn't get any replies.  Perhaps I'll get luckier here?

I am having a difficult time installing Ubuntu on my late 2007 MacBook Core 2 Duo from a USB stick. I am limited to using a USB stick, as my CD/DVD drive is no longer working. Additionally, I am running Mac OS 10.7.5 and cannot install Etcher. I have rEFIt installed, but it never detects my USB drive with Ubuntu. My USB drive is a Cruzer micro 4GB USB 2.0 and I have stored plenty of files on it successfully before. I have wiped it clean with Disk Utility and reformatted it into FAT 32, and have tried partitioning it into MBR as well as GUID, both without success. 

Here is the step-by-step protocol that I have been using, directly from Ubuntu's website ([https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick](https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick)). 

1. I downloaded ubuntu.iso. 
2. I converted the .iso to a .img using "hdutil convert /path/to/ubuntu.iso -format UDRW -o /path/to/ubuntu.img" in Terminal. 
3. I insert the USB drive. 
4. In Terminal, I use "diskutil list" to see which device node my USB is actually assigned (ie, /dev/disk1). 
5. I unmount the USB drive with "diskutil unmountDisk /dev/disk1" in Terminal. 
6. I execute "sudo dd if=/path/to/ubuntu.img of=/dev/disk1 bs=1m" in Terminal. 
Note: I have also tried dd'ing the Ubuntu file with both the .img and .dmg tags, using the same above command. I've also tried dd'ing the .iso. 
Note: I have also tried using "/dev/rdisk1" instead of "/dev/disk1." Both commands execute without error, and the flash drive lights up.  Sometimes, the command takes less than a second to complete, other times it takes about 3 minutes to complete... I'm not sure which is better. 
7. I then run "diskutil eject /dev/disk1" in Terminal and remove the USB.

I then re-insert the USB drive and my MacBook tells me it cannot be read with the error "The disk you inserted was not readable by this computer." 

I then restart the MacBook, holding down the option key. There is only my Mac HD or Recovery HD present. No USB drive available. 

I also have rEFIt installed and when booting into rEFIt, there is no USB detected. 

I have also tried partitioning a portion of the SSD that has MacOS installed on it, and making a portion available to ubuntu. I have tried dd'ing the .img and .iso over to this new partition and this seems to work better, as after I've copied over the file to the FAT32 partitioned SSD, I can view a new HD present in rEFIt to boot from, but then it fails to boot into the Linux installer. 

Any ideas? I'd loooove to have my really old MacBook running Ubuntu. 

Thanks

---

### Post by francoisdelabre on 2018-11-09
Hello,

I had the same issue with a late 2006 Macbook. I really doubt booting from a USB key is possible on this computer (worked well from CD though).
Perhaps you should first make sure you are able to boot from USB, without Ubuntu.
Try booting from a USB key with a MacOS Installer (a compatible MacOS version for your Macbook).
If you don't have any compatible MacOS iso, you could try from the Super Grub2 disk or from the rEFInd USB flash drive image file, on a USB key.
If none of these can boot your Macbook, it may be easier to search for a DVD drive.

---

### Post by johnnyc82 on 2018-11-24
I have a mid 2007 macbook and used a different method (seen on this link [https://ubuntuforums.org/showthread.php?t=2266424](https://ubuntuforums.org/showthread.php?t=2266424)). I got the third boot option to show up but after it tells me that it's checking linux and RamDisk it tells me to be patient but the screen changes and it only shows horizontal lines with the fan going really fast. I let it run but after 2 hours the same screen with the lines was there so i had to force it to shut down. Maybe you can get that method to work.

---

### Post by evmost95 on 2018-12-20
Well, first you have to consider that these macbooks are not even USB 3.0. One of the things that can be causing this is the controller/nand chip match-up. Are any of these flash drives 2.0? Also what brands are they?

Alternatively, it could be the method you are making these drives bootable. Have you tried makeusb-nox? [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

If all else fails, you should try the minimal CD on an actual CD and install from internet: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

