---
title: "Arch Linux urgent help//"
date: 2008-01-27
forum: Arch and derivatives
---

### Post by Dark Star on 2008-01-27
Hi all
Here is a story what I did ..I downloaded the I686 core pack from here [http://www.archlinux.org/download/](http://www.archlinux.org/download/)   Now I burnt in CD and booted trough it .. I went to installation screen by typing /arch/setup now after that I did set file system .. I set my /dev/sda4 as swap and /dev/sda7 as / After that it ask me do set a root partition I skip that ? Am I doiing wrong in that step ? After that I choose packages.. 

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0dd6c6bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sda2            3188        8287    40965750    f  W95 Ext'd (LBA)
/dev/sda3            8288        9607    10602900   83  Linux
/dev/sda4            9608        9729      979965   82  Linux swap / Solaris
/dev/sda5            4406        5737    10699290    7  HPFS/NTFS
/dev/sda6            5738        8287    20482843+   7  HPFS/NTFS
/dev/sda7            3188        4405     9783522   83  Linux

Partition table entries are not in disk order
Note: I don't have Windows Installed Only Arch and Ubuntu ... 

```

I use CD as primary installation and it mount my CD rom.. I select only Core/Base package.. and install it ..The next step is to install Grub it did install Grub but my Ubuntu grub appears when I rebooot.. Thats not a big deal I edited my Ubuntu Grub list and added Arch Entry .. Ok I set up my system and enter root password but there is no option to set up User Account . .I reboot as everything is done and boot through Hard Diskk..

Everything went fine for few seconds after a screen appears and ask to enter Myhost login .. But I haven't set any user account.. What I am doing wrong please let me know. .I am dying to use Arch with KDE mod :D

Thanks for Helping :)

---

### Post by 5-HT on 2008-01-27
No user accounts are created with the install script.
Login as root and create any desired user accouts with 'adduser'

[http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)

---

### Post by Dark Star on 2008-01-27
Now what It opened a console.. Now desktop env.. how to use it  ?Any detailed help would be nice.. though I gng to read that wiki right away but still what to do next ? 

Edit : I setup the username now what ?

---

### Post by Ub1476 on 2008-01-27
I suggest you read the beginner guide, it's very detailed. However, you need to install X and KDE/GNOME/XFCE/Fluxbox whatever. You need to create an xorg.conf file as well, and download drivers for your graphic card. It's all in the beginners guide:)

---

### Post by meborc on 2008-01-27
> **Dark Star said:**
> Now what It opened a console.. Now desktop env.. how to use it  ?Any detailed help would be nice.. though I gng to read that wiki right away but still what to do next ? 

Edit : I setup the username now what ?

arch is not ubuntu... :) you really need to make everything yourself... i would print the beginners guide if i was you

---

### Post by kellemes on 2008-01-27
> **meborc said:**
> arch is not ubuntu... :) you really need to make everything yourself... i would print the beginners guide if i was you


Indeed.. although building is a too big word.
Get online and use "links" or "lynx" to get the Arch [installerguide]("http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide"). The installation of Arch is *very* straightforward and most of the [installerguide]("http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide") you don't really need to *study* in order to get a working system, the defaults are often fine.

Creating a user.
[http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide#User_Management](http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide#User_Management)

---

### Post by Rumor on 2008-01-28
> **Dark Star said:**
> 
Everything went fine for few seconds after a screen appears and ask to enter Myhost login .. But I haven't set any user account.. What I am doing wrong please let me know. .I am dying to use Arch with KDE mod :D

Thanks for Helping :)

As others have said, ALL of this is covered in the[beginner's guide]("http://wiki.archlinux.org/index.php/Beginners_Guide"). 

Your "root" partition step that you skipped was not root, it was for your /boot partition. But since you have booted into Arch, login as root.

update your system by typing pacman -Syu

Install xorg by typing pacman -S xorg

Follow these instructions for installing KDEmod: [http://kdemod.ath.cx/installation.html](http://kdemod.ath.cx/installation.html)

Create your user by typing adduser

Configure your /etc/rc.conf and add kdm to your Daemons array

Reboot, login and then start adding whatever you want to your system.

---

### Post by p_quarles on 2008-01-29
Moved to the shiny new Arch forum. :)

---

### Post by LinuxGuy1234 on 2008-02-09
If I were you I would do:
links [http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)
That covers everything.

Also there's differs from Ubuntu and Arch.
In Ubuntu you install KDE using either:
sudo apt-get install kubuntu-desktop
-or-
sudo apt-get install kde-core
In Arch you do:
pacman -S kde

Xfce:
Ubuntu: sudo apt-get install xubuntu-desktop
Arch: pacman -S xfce4

---

### Post by bwtranch on 2008-02-10
> **LinuxGuy1234 said:**
> If I were you I would do:
links [http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)
That covers everything.

Also there's differs from Ubuntu and Arch.
In Ubuntu you install KDE using either:
sudo apt-get install kubuntu-desktop
-or-
sudo apt-get install kde-core
In Arch you do:
pacman -S kde

Xfce:
Ubuntu: sudo apt-get install xubuntu-desktop
Arch: pacman -S xfce4

Might be better to hold off on the kde for now and use kdemod. There are some compelling reasons why this is true. If you would like to read more about this, a good place is the Arch forum. I am a noob to Arch, but I also like reading forums a lot. The kdemod web site is the place to go for kde. Try installing another DE (Desktop Enviornment) like Gnome  that you are used to and then go with the KDE thing like I did. You won't have any problems that way. The reason for this is is long-winded and they can explain it better than I can. Good Luck!

---

