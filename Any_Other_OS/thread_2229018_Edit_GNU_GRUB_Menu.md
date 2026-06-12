---
title: "Edit GNU GRUB Menu ??"
date: 2014-06-10
forum: Any Other OS
---

### Post by ramakanta on 2014-06-10
[[img]http://s10.postimg.org/j07i9xj2t/grub.jpg[/img]](http://postimg.org/image/j07i9xj2t/)


yesterday i have install Linux mint 17 MATE along side windows 7. but when start it shows GNU GRUB Menu with default start Linux Mint 17 MATE 32-bit, 3.13.0-24-generic . my point is i want to make Windows 7 as default start (in the first in GRUB menu) . is it possible ?? how???

Also i want to remove  some parts which are 

(loader) (on /dev/sda1) - from windows 7 list.

3.13.0-24-generic (/dev/sda5) from Linux Mint list .

How to do this??

---

### Post by oldfred on 2014-06-11
Some will suggest Grub Customizer which is a gui and does make it easy. But it creates its own scripts and greatly modifies grub which can lead to issues later.

If not adverse to manually editing a few files.
       Configuring the Boot Menu in Ubuntu - Boot Order in grub
[http://www.psychocats.net/ubuntu/bootmenu](http://www.psychocats.net/ubuntu/bootmenu)
[https://help.ubuntu.com/community/Grub2/Setup#Specific_Entries](https://help.ubuntu.com/community/Grub2/Setup#Specific_Entries)

            How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

    
       This is so it does not auto add Windows entry, as you will manually copy it into 06_custom. Copy & paste another entry into grub, so it stops auto adding Windows at end of menu.
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true

Copy 40_custom to 06_custom so it is first in order. Scripts are processed in number order.
 sudo cp -a /etc/grub.d/40_custom /etc/grub.d/06_custom
      sudo chmod 755 /etc/grub.d/06_custom

Back up grub file:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
Open grub.cfg so you can copy Windows boot stanza
gedit /boot/grub/grub.cfg

Paste entire Windows boot stanza into 06_custom and edit description only to be what you want:
gksudo gedit /etc/grub.d/06_custom

Then do:
sudo update-grub

---

### Post by ramakanta on 2014-06-13
I have found one application - graphical grub2 settings manager ([https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)) . what about it ??? 

[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

[[IMG]http://s1.postimg.org/bieyrfwhn/image.jpg[/IMG]]("http://postimg.org/image/bieyrfwhn/")
I am confusing about this two download options . what I will used for Mint 17 ???

---

### Post by ramakanta on 2014-06-19
grub-customizer works perfectly . but I am confusing about one option , that I have never use it whish  is  ***install to MBR   ***in File menu . what is the used of this option ??? any suggestion ??? thanks ??? 

[[img]http://s10.postimg.org/oviluxy6t/grub_customiser.jpg[/img]](http://postimg.org/image/oviluxy6t/)

---

