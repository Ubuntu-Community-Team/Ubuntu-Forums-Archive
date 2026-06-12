---
title: "Install Ubuntu 24.04 on MacBook Air 6.2 with Intel CPU -&gt; Hard disk not visible"
date: 2024-06-28
forum: Apple Hardware Users
---

### Post by tairborne2024 on 2024-06-28
Hello everyone. 


As there are no more updates from Apple for my old MacBook Air, I would like to install Ubuntu as the only OS on it. 


I have created a USB stick with Ubuntu and can start the installation with it. However, when partitioning, only the stick and not the hard disk is shown as a device. I have tried various constellations in the MacOS partitioning tool, but so far without success. 


The entire hard disk can be used for Ubuntu. I don't need any data or the old MacOS. 


The FAQ here in the forum says something about an "unjurnaled" file system. However, this is not available for selection in the tool. 


What can I do?
Thank you!

---

### Post by tairborne2024 on 2024-07-01
Update:  I have tried a lot of different configurations but the disk is still not visible in the Ubuntu live system or installation. 
If I boot with a Windows USB stick, I can easily see and config the disk -  What makes Microsoft better here?

---

### Post by ajgreeny on 2024-07-01
When you boot to the live Ubuntu USB system chose to try Ubuntu without installing and from that live system (assuming you get to a full GUI) open gparted to see if that can find the disk.Using that you can create a new partition table, leaving only unallocated space and then try to install Ubuntu again.

The installer should see the disk and free space and then be able to install the OS.

---

### Post by tairborne2024 on 2024-07-01
Hi ajgreeny and thanks for your reply. 
Unfortunately, the internal hard disk is not visible in gparted or in disks. Only the USB stick is displayed.

---

### Post by tairborne2024 on 2024-07-02
Hello together,

here you can see screenshots from 

[LIST]
[*]- the macOS recovery terminal, with the partition from the windows installer and from
[*]- the gparted and disks app from Ubuntu.
[/LIST]
[IMG]https://drive.google.com/file/d/1Uz2f9CLnTX8chvZFTBofkeKi77agWRFH/view?usp=sharing[/IMG]
Thanks!

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293931&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=293932&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=293933&stc=1[/IMG]
[IMG]https://drive.google.com/file/d/1Uz2f9CLnTX8chvZFTBofkeKi77agWRFH/view?usp=sharing[/IMG]
[IMG]https://drive.google.com/file/d/1Uz2f9CLnTX8chvZFTBofkeKi77agWRFH/view?usp=sharing[/IMG]

---

