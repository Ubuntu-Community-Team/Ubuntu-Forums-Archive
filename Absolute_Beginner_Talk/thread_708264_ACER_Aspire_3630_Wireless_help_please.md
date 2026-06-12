---
title: "ACER Aspire 3630 Wireless help please"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by waz101 on 2008-02-26
My Nephew has been very enthusiastic about Ubuntu for quite a while, Unfortunately he has an ACER Aspire 3630 and the wireless does not work under UBUNTU 7.10. He doesn't want to revert to Windows but unless we can get the wireless working it looks like that's the way it's going.

I have tried to install the wireless using this code below that I found whilst spending hours searching for a solution.

> echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper
sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i /home/dave/Desktop/bcmwl5.inf
sudo ndiswrapper -m
sed -e 's/RadioState|1/RadioState|0/' /etc/ndiswrapper/bcmwl5/*.conf
sudo modprobe ndiswrapper


The first problem that we came across was the Ndiswrapper Utils would not install, i managed to resolve this using the Synaptic.

The first line of the script works but after that it all goes wrong, I would appreciate any help, links, anything? that anybody could give me. The only Version of Unix I have ever used is BusyBox in my router (and that was a matter of copy and paste!). 
I really need an Idiots guide I.E "place the driver folder here!"

I have read so many posts and guides that i think my eyes are going to bleed!


Thanks in advance


Waz

---

### Post by sayakb on 2008-02-26
@OP

Did you try the restricted driver manager in Gutsy?

---

### Post by markbusu on 2008-02-26
Use the restriced Driver... Works Perfectly

---

### Post by sayakb on 2008-02-26
@OP

You can find the restricted driver manager under System->Administration

Just tick the checkbox to download the respective drivers.

---

### Post by waz101 on 2008-02-26
Thanks, I will get him to try it later.


Waz

---

### Post by waz101 on 2008-02-26
He has now reloaded everything from scratch, is connected to the router via Ethernet but cannot access web pages or anything else. What does he have to do to get it running so that he can get the restricted driver manager to download the driver?

Thanks

Waz

---

