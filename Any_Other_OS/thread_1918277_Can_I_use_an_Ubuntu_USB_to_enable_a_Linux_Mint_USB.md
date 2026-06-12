---
title: "Can I use an Ubuntu USB to enable a Linux Mint USB to boot itself?"
date: 2012-01-31
forum: Any Other OS
---

### Post by davidc60 on 2012-01-31
Hi,
 

 I presently have Ubuntu 11.10 installed on an USB and Linux Mint 12 installed on a second USB. I can boot into the Ubuntu USB directly but cannot do so with the Linux Mint 12 USB (it returns a message to the effect that there is no such device). However, I can boot into the Linux Mint USB *_**via the Ubuntu start-up menu. **_*From Ubuntu I have tried 'sudo grub-install /dev/sdc' (sdc being the Mint USB) in order to try to get Mint going directly and although it claims that the installation process was completed and without error, it is still not possible to boot the Mint USB directly. Is there anything else that I can do with the Mint USB **from Ubuntu** in order to get the Mint USB booting up itself without the aid of Ubuntu?
 Thanks,
 davidc

---

### Post by C.S.Cameron on 2012-02-01
What happens if you boot the Mint USB via the Ubuntu USB's grub, remove the Ubuntu USB then run ```
sudo update-grub
``` in terminal?

---

### Post by Perfect Storm on 2012-02-01
Moved to Other OS/Distro Talk.

---

### Post by raja.genupula on 2012-02-01
i am not getting your post .
if you wanna make mint to have a own boot then 
     with any way boot into Linux mint and then your terminal .
    sudo dpkg-reconfigure grub-pc 
   in this process install the GRUB to mint sda or sdb or what ever mint have . 

that will make a own boot for linux mint with Ubuntu as 2nd option but grub will be on Mint only ,

Now remove the USB of Mint and keep USB of Ubuntu then install GRUB in it .

now your Ubuntu will have a GRUB but it dont have Mint option in it up to you mention 
sudo update-grub

but mint will have Both Ubuntu and MInt options .

actually Boot order important thing here . i mean boot priority in BIOS settings . 

Hope that helps.

---

### Post by davidc60 on 2012-02-01
Thanks guys for your helpful replies. The problem is now sorted and also academic because I have also now got my HDD up and running properly again. Thanks again,
davidc

---

