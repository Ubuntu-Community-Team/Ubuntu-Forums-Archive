---
title: "Mubuntu - mate+ubuntu"
date: 2012-12-20
forum: Any Other OS
---

### Post by ptavatar on 2012-12-20
Just for MATE lovers... :p

Yesterday i released 1st Alpha of my new distro: Mateu
Today i released 2nd Alpha;

Visit now: [http://mateu.pt.vu](http://mateu.pt.vu)

Ubuntu with classical MATE!
[]("http://mateu.pt.vu")

---

### Post by Stinger on 2012-12-20
Nice ! I do like MATE (and Gnome)

I'll give it a whirl  ):P

PS. please consider using a color without a pattern so that the comments on your website are easy readable ;)

---

### Post by click4851 on 2012-12-20
very nice....

---

### Post by wladypauly on 2012-12-20
If gnome-session-fallback support is going to be dropped, as I heard a couple of weeks ago, I think I will turn to Mate, everything else seems a bit user-unfriendly :)

---

### Post by Rebelli0us on 2012-12-20
You can install MATE 1.4 as startup option in Ubuntu. The following from [http://mate-desktop.org](http://mate-desktop.org)


```
**Ubuntu Quantal Quetzal (12.10) repository**
Add ONE of the following repos to /etc/apt/sources.list via the following command: 
sudo add-apt-repository "deb http://packages.mate-desktop.org/repo/ubuntu quantal main"
OR
sudo add-apt-repository "deb http://repo.mate-desktop.org/ubuntu quantal main"
or using a text editor of your choice add the ONE following mirrors to /etc/apt/sources.list: 
deb http://packages.mate-desktop.org/repo/ubuntu quantal main
deb http://repo.mate-desktop.org/ubuntu quantal main

**MATE Installation (Oneiric/Precise/Quantal)**
Then run the following command to update your repositories and install MATE: 
sudo apt-get update
sudo apt-get install mate-archive-keyring
sudo apt-get update
# this install base packages
sudo apt-get install mate-core
# this install more packages
sudo apt-get install mate-desktop-environment

```


Or you can install Mint MATE 14 -- same thing.

---

### Post by ptavatar on 2012-12-21
|

---

### Post by ptavatar on 2012-12-21
> **Rebelli0us said:**
> You can install MATE 1.4 as startup option in Ubuntu. The following from [http://mate-desktop.org](http://mate-desktop.org)


```
**Ubuntu Quantal Quetzal (12.10) repository**
Add ONE of the following repos to /etc/apt/sources.list via the following command: 
sudo add-apt-repository "deb http://packages.mate-desktop.org/repo/ubuntu quantal main"
OR
sudo add-apt-repository "deb http://repo.mate-desktop.org/ubuntu quantal main"
or using a text editor of your choice add the ONE following mirrors to /etc/apt/sources.list: 
deb http://packages.mate-desktop.org/repo/ubuntu quantal main
deb http://repo.mate-desktop.org/ubuntu quantal main

**MATE Installation (Oneiric/Precise/Quantal)**
Then run the following command to update your repositories and install MATE: 
sudo apt-get update
sudo apt-get install mate-archive-keyring
sudo apt-get update
# this install base packages
sudo apt-get install mate-core
# this install more packages
sudo apt-get install mate-desktop-environment

```


Or you can install Mint MATE 14 -- same thing.

It's more easy if you download mabuntu and install it directly.
Xubuntu, kubuntu, lubuntu desktop, can be installed as option, but they are distros too ;)

---

### Post by LuvLinuxOS on 2012-12-21
Congrats!!!):P

---

### Post by Stinger on 2012-12-21
I've tried making a bootable usb drive using the dd command, but the drive won't boot.

Which usb-creator tool do you recommend for Linux ?

---

### Post by Rebelli0us on 2012-12-21
> **ptavatar said:**
> It's more easy if you download mabuntu and install it directly.
Xubuntu, kubuntu, lubuntu desktop, can be installed as option, but they are distros too ;)

Yes, MATE 1.4 installs on top of Ubuntu 12.10 and shows up as an option in the login menu. There are some bugs when it's done that way. Some mysterious intermittent hang of the start menu for ~2 mins on bootup, and some display bugs in Nautilus or Caja. I hope you're fixed those in Mubuntu. Nice name Maboonter ;)

---

### Post by ptavatar on 2012-12-22
> **Rebelli0us said:**
> Yes, MATE 1.4 installs on top of Ubuntu 12.10 and shows up as an option in the login menu. There are some bugs when it's done that way. Some mysterious intermittent hang of the start menu for ~2 mins on bootup, and some display bugs in Nautilus or Caja. I hope you're fixed those in Mubuntu. Nice name Maboonter ;)

Yes, uninstalled nautilus (no bugs), just caja
But it has a bug with gtk3, trying to fix it to alpha3.

---

### Post by ptavatar on 2012-12-22
> **Stinger said:**
> I've tried making a bootable usb drive using the dd command, but the drive won't boot.

Which usb-creator tool do you recommend for Linux ?

Use unetbootin and choose ISO option: 

[http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")

If you use windows, Universal USB Installer is better:

[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/")

---

