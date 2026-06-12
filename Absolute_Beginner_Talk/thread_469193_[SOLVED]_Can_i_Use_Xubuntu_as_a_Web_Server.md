---
title: "[SOLVED] Can i Use Xubuntu as a Web Server"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by wasing on 2007-06-09
I have a while to figure out what i am going to do with my first home buillt computer but i think i am going to use it as a webserver... but while thinking this i did not see a version of xubuntu for the OS but Ubuntu does have one including all the stuff i need to create a a web server so what i was wondering was...

can i use xubuntu to create a web server and also get the software for servers from xubuntu or do i need the ubuntu server os that comes with the  LAMP Software Package

The computers specs are

700mhz proccesor
soon to be 256mb of ram (2x 128MB)
5GB hardrive (I have two but i was also not sure if i could use the second cable connector to connect a second 5GB harddrive) 
Aopen MK33 Motherboard
CD-ROM drive
Floppy Disk Drive
200 Watt Power Supply
Also has ethernet card which i why i was going to use it as a very basic web server

yes i know these specs are horrible but for my first computer and all of the parts (Except the RAM) were free so i can't complain at all... this is also why i wanted to use xubuntu because it looks very efficent for the small system i have.

... i was also thinking about purchising a harddrive off ebay if i really needed a larger one but nothing more than 100GB and use it as a file server if the webserver doesn't work out

---

### Post by Portable_Jim on 2007-06-09
Yes you can. You just need to install apache. The newer version of apache is called httpd.
```
sudo aptitude install httpd
```
See [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Apache_HTTP_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Apache_HTTP_Server)
for a better explanation on how to install.

If you don't want apache, you can choose lighter versions sich as mini-httpd and mini-httpd.

Hopes that helps.

---

### Post by louieb on 2007-06-09
I have Ubuntu server on a P3 433mhz 256mb ram runs  just fine. It does have  a 40 gig drive.
The easy way to tell if the second drive will woks first check the jumper set as slave. plug it in to the middle connector of IDE cable. Red stripe on cable toward power connector. 
Get the [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php") and boot it up. If GParted sees both drives your good to go.
Get the server cd and add the xubuntu desktop 
or xubuntu cd and add the LAMP software. 

Just do a forum search there a plenty of howtos  on both. 
Heres one thread [HOWTO: Leightweight Gnome - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=298818&highlight=xorg+gdm+gnome-core")

---

