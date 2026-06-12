---
title: "Ubuntu on MacBook Pro Late 2011"
date: 2012-02-12
forum: Apple Hardware Users
---

### Post by Keithodulaigh on 2012-02-12
Hello,

Has anyone been able to install Ubuntu on the above version of a Mac _without_ using bootcamp or refit?

When I place the Ubuntu 11.10 disk in the machine, it gets as far as letting me choose the language then I get "initramfs unable to find a medium containing a live file system" . I searched for information about that problem and was told to place a USB key with the Ubuntu image flashed in the machine at the same time. I got that info from [http://forums.macrumors.com/showthread.php?t=1168202](http://forums.macrumors.com/showthread.php?t=1168202)

I have also tried creating a partition on a hard-drive and putting the Ubuntu ISO on the partition then booting from that but that only lets me as far the GRUB console, which is worse.

Thanks,
Keith

---

### Post by 2F4U on 2012-02-12
Are you sure that the downloaded iso file is ok, e. g. does the checksum match? It could also be a badly burned cd. While I don't have a 2011 MacBook, my MacBook from 2008 refused to boot from a usb key with Ubuntu on it. I could only boot from a liveCD.

---

### Post by Keithodulaigh on 2012-02-13
Hi,

Thanks for the reply. 

I have tried re-downloading and re-burning the ISO. Same problem.

I've also tried the Ubuntu server ISO and although it doesn't have a "try without installing" feature, it did seem to get farther. (I clicked on recover a broken system and it got as far as probing the keyboard for the correct locale. I cancelled it after that because I didn't want it to do anything with my hard-drive.)

---

### Post by Keithodulaigh on 2012-02-19
Any more ideas?

---

### Post by Keithodulaigh on 2012-02-21
Bump!

---

### Post by rtz2rbbl on 2012-02-22
I had this problem when installing Mint. The only workaround that I found is this...

Burn the iso to a cd/dvd. 
Burn the exact same iso to a flash drive either using unetbootin or dd. 
Plug in the the flash drive, turn on the computer and boot from the disk. 

That way the disk will find the live system on the USB rather than trying to get it from the disk. 

HOWEVER....good luck actually getting the system to install and boot. I haven't managed that part yet.

EDIT: try booting in compatibility mode, when you chose that option form the menu, hit tab to edit the boot parameters. When you do that, add nomodset to the end so that it looks like this nomodeset --

---

### Post by Keithodulaigh on 2012-02-24
Okay, I've just tried the daily build for 12.04. It booted up without any problems. I will wait for the final build before I try and install it.

Thanks for the replies.

---

