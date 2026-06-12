---
title: "Difficulties with usb booting on an Asus Maximus IV Gene mobo."
date: 2012-02-16
forum: Asus Ubuntu Support (CLOSED)
---

### Post by Asclepias on 2012-02-16
Hello hello. 

Thanks in advance for any help. 

I recently built my own computer as a reward for quitting smoking. I'm using an Asus Maximus IV gene (with a 2500 i5, m4, 16gigs corsair ram, and a geforce evga560) and am having inconsistent booting issues. I have used unetbootin, usb installer, and universal usb installer currently. Older distros boot fine like U10.04lts, Mint 9, and Crunchbang 10 works great. But these don't have ethernet support out of the box. 

But, if I install mint12 or xubuntu11.10 it will pause at a

"[#] sd 0:0:0:0 [sda](the usb drive) attached SCSI removable disk"

After waiting or playing with buttons, it will start scrolling something with a udevd[#]: timeout: killing '/sbin/modprobe -bv pc with a long strong of numbers recursively. 

I have tried multiple usb sticks. I just bought a Sandisk 4gb cruzier. And DuckDuckGo has not yielded any real useful information. 

I know its an esoteric question, but I'm stumped. I don't really want to purchase a dvd-drive to try that method, but I will if I need to (windows is driving me CRAZY).

---

### Post by @gu79 on 2012-02-17
Congratulations for quitting!

Have you tried booting with nomodeset or acpi=off options? 

([**How to set NOMODESET and other kernel boot options in grub2**]("http://ubuntuforums.org/showthread.php?t=1613132"))

---

