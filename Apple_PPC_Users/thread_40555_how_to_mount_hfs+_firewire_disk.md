---
title: "how to mount hfs+ firewire disk?"
date: 2005-06-09
forum: Apple PPC Users
---

### Post by secundar on 2005-06-09
So I've decided to wipe my Blue and White G3 tower and install ubuntu. I've installed backuppc so i can use it as a web and backup server for my home network.

In it's previous life It was running Jaguar and I just copied folders over the network manually. So I have a bunch of files already on an hfs+ hard disk (slave). Ubuntu is installed on the master. I also have a FW hard drive for storing more stuff.

When ubuntu came up after installing none of these drives showed up. I checked and hfs support is installed but i can't make it work. The drives don show up with df.

Thanks for your help!

---

### Post by Brian McConnell on 2005-06-09
Make sure yur device is connected and power turned on and then open a terminal and type:
sudo mount -a

you should be prompted for your password and then you should get a desktop icon or an icon in computer or in /media.
If not, please type:
sudo fdisk -l and report the output here.
I assume you're using the Gnome desktop environement.
If so, you should make sure you have gnome-volume-manager installed. Dont know why you've not got it automounted after login. My USB and ieeee1394 drives have always been autodetected by Gnome.

---

