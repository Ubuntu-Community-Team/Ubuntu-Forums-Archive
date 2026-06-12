---
title: "PPPoE on ubuntu"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by Thaeberius on 2006-05-21
Hello, I'm a newbie to linux but i seem to have gotten the hang of it... One issue i haven't got to the end to... My ISP uses PPPoeE and i can't get ubuntu to connect to the internet wich is a bummer. Can anybody help? And one other thing... is it possible to view ntfs or fat32 partitions in ubuntu? 

Thanks, Thaeberius....

---

### Post by Yoriko on 2006-05-21
What is your ISP?
check if your modem is supported by [eciadsl](http://eciadsl.flashtux.org/) driver, and follow the documentation on there. I use it with a BT voyager 105.

for NTFS look [Here](http://www.ubuntuforums.org/showthread.php?t=142481&highlight=ntfs+mount+howto)

and to mount a FAT device, I'm guessing it is a USB, if you have gnome-vfs-daemon running (automatically on gnome, need to add gnome-volume-manager on startup for other wm's, KDE has its own IIRC) it should automount for you.

---

### Post by Thaeberius on 2006-05-21
Well, I have a standard ethernet card... I proceed in the same way like a dial-up connection... only instead of a modem, the connection is made through a ethernet card (network card)... 

Hope I'm not a handfull, but please bare with me...

---

### Post by ouphe on 2006-05-21
Check this link:
[http://www.ubuntuforums.org/showthread.php?t=91249]("http://www.ubuntuforums.org/showthread.php?t=91249")

---

### Post by priority1 on 2006-05-21
This might help     [https://wiki.ubuntu.com/ADSLPPPoE](https://wiki.ubuntu.com/ADSLPPPoE)

---

### Post by RRS on 2006-05-21
Do you have a seperate DSL modem that you connect to from your ethernet card?

These are often provide by your ISP as part of the initial service package and usually handle the PPPoE connection and you can then connect to it using DHCP.

Follow [this guide]("http://easylinux.info/wiki/Ubuntu#Windows") to you mount your NTFS and Fat partitions.

Let us know if you have anymore questions.

---

### Post by perce on 2006-05-21
There is a cute application called pppoeconf to help you to set up a pppoe connection. Run it from a terminal as root:
sudo pppoeconf

It is quite self-explanatory, whenever it asks you for things you don't understand, just leave the default values.

---

### Post by Thaeberius on 2006-05-23
Thanks a lot... I FINALLy managed to get ubuntu to go online, hooray!
Thanks a lot... you finally helped me ditch windows. Thanks a lot!

---

