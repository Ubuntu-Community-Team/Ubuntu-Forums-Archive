---
title: "macbook pro 8.2 no wireless on Ubuntu 10.04.2"
date: 2011-10-23
forum: Apple Hardware Users
---

### Post by Alhasan257 on 2011-10-23
I'm a new user to linux and I'm totally LOST.
on my macbook pro8.2 using the CD im not able to boot any linux operating systems like 11.04 natty, 10.10 maverick. i was only able to book 10.04.2 which im not able to get the ethernet and wireless working so its a waste of space in my hardisk at the moment.
when i try to install 11.04 or 10.10 after the ubuntu picture comes it tries to load and i get this error:
 
Busy Box v1.13.3 (Ubuntu 1:1.13.3-1ubuntu9) built in shell (ash)
Enter 'help' for a list of built in commands.

(initramfs) Unable to find a medium containing a live file system
 but the 10.04 lucid got installed 
PLEASE help me out in some way to get my linux sorted out. i just wanna know how to start up ethernet in my 10.04.02 or to install 11.04. please sort me out.
i also tried to upgrade the 10.04.02 to 10.10 but it shows me some error saying some packages are missing download them.but for that i need internet.
i need internet to install few open source softwares for my studies
i need to sort out the wifi. 
thanks :)

---

### Post by TheFamousJonathon on 2012-01-23
The only bootable Ubuntu version is the 10.04.3 LTS. Which means, you will have to install the 10.04.3 and then upgrade within versus installing a fresh copy onto your MacbookPro8,2. 

Also, for your wireless.... 
You will need to get the following:

[LIST]
[*]compat-wireless: go to [Linux     Wireless]("http://wireless.kernel.org/en/users/Download#Where_to_download_bleeding_edge")     and download compat-wireless-2.6.tar.bz2
[*]the latest version of     [bw43-fwcutter]("http://bu3sch.de/b43/fwcutter/b43-fwcutter-015.tar.bz2")     (version 015)
[*]Broadcom's [proprietary     driver]("http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2")     to extract the firmware
[/LIST]
Refer to: [http://homepage.uibk.ac.at/~c705283/archives/2011/09/04/linux_support_for_broadcom_4331_wireless_chip_macbook_pro_81/index.html](http://homepage.uibk.ac.at/~c705283/archives/2011/09/04/linux_support_for_broadcom_4331_wireless_chip_macbook_pro_81/index.html)

I know it says support for MacbookPro8,1, but it also works 100% on the MBP8,2 (Which I am talking currently using).

Let me know if you need additional help.....

---

