---
title: "connect to XP simple network"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by bennyb on 2007-04-26
can someone give me some hint where to go next? I cannot connect to my home network of a desktop XP box and a laptop XP box using Feisty. I have tried all the obvious steps, I assume it's supposed to be a snap to do. 

The saga so far: 1) yes, I have shared XP folders, 2) yes, I've stopped firewalls 3) the XP boxes communicate shares happily, 4) if samba is installed, it works fine, 5) many reinstalls of feisty to try with the most "pristine" of installs. 6) connect to server...> service type: windows share > browse network shows the windows network, then the workgroup name then the dreaded folder contents cannot be displayed popup.

Thanks for any insight. . .

---

### Post by sailor2001 on 2007-04-26
go to automatix2 and download the ntfs crossover

---

### Post by bennyb on 2007-04-26
hmmm, thanks but I only see an app in automatix2 that mounts LOCAL partitions & that don't seem like the right one. The only "crossover" is one  affecting commercial apps. Do you have a more specific title?

---

### Post by gilda on 2007-04-26
4) if samba is installed, it works fine

What's samba? samba is a software that allows you to connect a Linux computer to a Windows using NetBIOS to share folders and drives between both OS.

You will need this compatibility layer for the separate  OS's to network properly. 

One of the other things you may want to check is that in you /etc/hosts file that you declare the "Computer Names" of your windows boxes 

Like where you have the line

(This defines the current system)
127.0.0.1     yourNixBox

(Define extra systems on your network,
they need to have a static IP to be defined this way.)
192.168.0.5   winBoxOne
192.168.0.6   winBoxTwo 

Change the IP's as needed do not copy this line for line its an example

This only Matters if you are on a Static Network not a DHCP based network.

---

