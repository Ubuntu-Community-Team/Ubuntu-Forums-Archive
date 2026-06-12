---
title: "How to reinstall Windows 7 on Asus Eee PC 1005PE Netbook with Ubuntu 11.10"
date: 2012-01-09
forum: Asus Ubuntu Support (CLOSED)
---

### Post by KingChewbert on 2012-01-09
Hello,

when I had initially bought my Asus Eee PC 1005PE Netbook, Windows 7 was already pre-installed. No installation disc came with it.
After a year, I decided to install Ubuntu operating system - and unfortunately, did not keep the Windows partition. So, there is **no Windows partition** (NTFS) on my Netbook.
I have also upgraded my Ubuntu to Ubuntu 11.10, which is the current operating system running on this Netbook.

Now, I am considering to get back to Windows 7.
I know how to make a bootable USB from which I "could" boot, but what I do not know is which kind of Windows 7 I do need to have on this bootable USB device in order for my Ubuntu-Netbook to correctly boot from it.

I have tried Windows 7 Starter Edition, have created the bootable USB device containing the .ISO file -
further, I have set up the BIOS settings in a way to boot from the removable device first -

 .. but it just would not boot from the USB device :( I do see that the Netbook is trying to boot from the removable device first (takes longer until it starts Ubuntu) - but, it just would not come up with any Windows screen. After a while, it keeps starting Ubuntu 11.10.

I know how to look up the existing partition table in Terminal, etc. .. so if you need any of this information please, let me know.

 Would appreciate any help and support.
 Thank you very much.

---

### Post by KingChewbert on 2012-01-09
Quote:
"I have an Asus Eee PC 1005PE, 2GB of RAM, Intel Atom N450, 1.66 GHz, 1 core, two logical processors. Windows 7 starter."

 I have exactly the same Asus Netbook (just upgraded to 4GB RAM) and have installed Ubuntu, recently also upgraded onto Ubuntu 11.10 - both running very well. My problem is just how to get Windows back on ..

---

### Post by rajeshux on 2012-01-09
> **KingChewbert said:**
> Quote:
"I have an Asus Eee PC 1005PE, 2GB of RAM, Intel Atom N450, 1.66 GHz, 1 core, two logical processors. Windows 7 starter."

 I have exactly the same Asus Netbook (just upgraded to 4GB RAM) and have installed Ubuntu, recently also upgraded onto Ubuntu 11.10 - both running very well. My problem is just how to get Windows back on ..

Did u mean to say you are unable to find windows 7 entry on ubuntu boot menu, or whether it is missing with new upgradation of ubuntu 11.10.  If you have active windows os partition with no boot entry on ubuntu grub menu, you can use sudo update-grub to get the windows back on the grub list.

:), 
rajesh-UX.

---

### Post by KingChewbert on 2012-01-10
- if I may, I have a very similar problem -

Hello,

when I had initially bought my Asus Eee PC 1005PE Netbook, Windows 7 was  already pre-installed. No installation disc came with it.
After a year, I decided to install Ubuntu operating system - and  unfortunately, did not keep the Windows partition. So, there is **no Windows partition** (NTFS) on my Netbook. (Have checked the partition table in Terminal already)

I have also upgraded my Ubuntu to Ubuntu 11.10, which is the current operating system running on this Netbook.

Now, I am considering to get back to Windows 7.
I know how to make a bootable USB from which I "could" boot, but what I  do not know is which kind of Windows 7 I do need to have on this  bootable USB device in order for my Ubuntu-Netbook to correctly boot  from it.

I have tried Windows 7 Starter Edition, have created the bootable USB device containing the .ISO file -
further, I have set up the BIOS settings in a way to boot from the removable device first -

 .. but it just would not boot from the USB device :sad:  I do see that the Netbook is trying to boot from the removable device  first (takes longer until it starts Ubuntu) - but, it just would not  come up with any Windows screen. After a while, it keeps starting Ubuntu  11.10.

I know how to look up the existing partition table in Terminal, etc. ..  so if you need any of this information please, let me know. Also, I have a separate Windows laptop with Automated Installation Kit installed, etc. all I need is step-by-step instructions and the information how to make the bootable USB stick work.

 Would appreciate any help and support.
 Thank you very much.

---

### Post by coffeecat on 2012-01-10
@KingChewbert, I have merged the two posts you made on other people's threads with your own thread, together with the one reply you had received. Please do not hijack other threads and please note this from the forum [Code of Conduct](http://ubuntuforums.org/index.php?page=policy):

> Do not cross post, or post the same thing in multiple locations.

---

### Post by KingChewbert on 2012-01-10
**Coffeecat**,

I am very sorry - thank you very much for merging the two posts & I sincerely apologize for my mistake.

It will not happen again - promise.

 Kind regards,
 King Chewbert

 * * * 

**rajeshux**

thank you for your reply - I will check once more, but I fear that I have completely deleted the Windows partition, now only having the Ubuntu partition on my Netbook.

 will inform once checked :) .. thank you for the help!

---

### Post by C.S.Cameron on 2012-01-10
An EEE's BIOS sees a flash drive as just another hard drive so your flash drive should be set as first hard drive.

Will your W7 flash drive boot other computers?

If not use gparted to format the flash NTFS and set the boot flag, then copy the DVD or extract the W7 iso to it.

---

### Post by KingChewbert on 2012-01-11
Hello - happy to report that I made it work.

 Like suggested earlier, yes - the problem was plain simple that my Asus Eee PC had a problem to boot appropriately from the Bootable USB drive.

 In the end, what has worked:

- BIOS Settings (F2) and change to: "Boot from 1st: Removable Device"

- Confirm with F10

- immediately after confirming (OK) --> **make sure to click: ESC (top left corner on keyboard)**

-------> this helped me to really boot from the removable device.

 I could boot my Windows Premium Home &
 install Windows, also allowing me to change the partitions.

 :KS Thank you very much for your kind help and advice.

---

