---
title: "asus N55 and installing nvidia drivers ?"
date: 2012-08-28
forum: Any Other OS
---

### Post by jolato on 2012-08-28
Hi,

I have an asus N55F, great machine, however nothing but problems with nvidia installation. I first installed sabayon 9, zorin and now mint 13/cinnamon, to discover that each time it displays "no additional drivers".

I tried a manual install, howver rebooting puts me in some 800x600 screen where I can see less then half of the total screen, completely useless. I should revert to original situation, but how ?

My graphics card is GT 550M. Could someone please explain what is the first thing to do to resolve this problem ?

---

### Post by monk0nuggets on 2012-08-28
I've been hoping someone would find the answer for months now.  Still nothing as far as I know.

---

### Post by RaZoRbelarus on 2012-08-28
Nvidia drivers from "additional drivers" are not what you want. To get Nvidia Optimus working you need to install Bumblebee. It allows to use integrated Intel graphics for 2d and not very heavy 3d apps. And when you need more power, just run the app through optirun command and it will use Nvdia graphics. To get Bumblebee enter this commands one by one in Terminal. 
sudo add-apt-repository ppa:bumblebee/stable
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install bumblebee bumblebee-nvidia
And then reboot the laptop.

---

### Post by jolato on 2012-08-28
> **RaZoRbelarus said:**
> Nvidia drivers from "additional drivers" are not what you want. To get Nvidia Optimus working you need to install Bumblebee. It allows to use integrated Intel graphics for 2d and not very heavy 3d apps. And when you need more power, just run the app through optirun command and it will use Nvdia graphics. To get Bumblebee enter this commands one by one in Terminal. 
sudo add-apt-repository ppa:bumblebee/stable
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install bumblebee bumblebee-nvidia
And then reboot the laptop.

For me that would be the next step. First install proprietary drivers.

---

### Post by Perfect Storm on 2012-08-28
Moved to Other OS/Distro Talk.

---

### Post by jolato on 2012-08-29
> **Artificial Intelligence said:**
> Moved to Other OS/Distro Talk.

Why do you move this w/o asking to somewhere it does not belong ??

---

### Post by Perfect Storm on 2012-08-29
> **jolato said:**
> Why do you move this w/o asking to somewhere it does not belong ??

Mint is not a Canonical Product. Ubuntu Forums are for help and support with Ubuntu stuff. Therefore the move.

The staff do not need to ask. This is a moderated forum with guidelines and rules.

---

### Post by jolato on 2012-08-29
> **Artificial Intelligence said:**
> Mint is not a Canonical Product. Ubuntu Forums are for help and support with Ubuntu stuff. Therefore the move.

The staff do not need to ask. This is a moderated forum with guidelines and rules.

Do you mean that Ubuntu does not have this (proprietary nvidia driver) problem Mint has ?

---

### Post by Perfect Storm on 2012-08-29
> **jolato said:**
> Do you mean that Ubuntu does not have this (proprietary nvidia driver) problem Mint has ?

Properly, as Mint is based on Ubuntu. But mint is still not a Canonical product. There's other people behind Mint. You'll find mint forum here: [http://forums.linuxmint.com/](http://forums.linuxmint.com/)

---

