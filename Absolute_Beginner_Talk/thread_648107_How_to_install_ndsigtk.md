---
title: "How to install ndsigtk"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by Killy1 on 2007-12-23
I am trying to install the drivers for my PCI WLAN, after getting an invalid driver message for the .inf file, I was advised to use the graphical inerface for ndiswrapper, ndisgtk (i am using ndiswrapper 1.9). I have downloaded the .deb file for this and now dont really know how to install it.

My PCI card is a Marvel 88w8335 Libertas and have got the drivers for this.

---

### Post by blueridgedog on 2007-12-23
This site tells how to manually install a .deb file:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

I have little linux exp on wireless configuration though...

---

### Post by Killy1 on 2007-12-23
Thanks, I will have a look and see how I get on. I have found a post which looks like it may solve my problems.

---

### Post by Killy1 on 2007-12-26
Tried to install the .deb file for ndisgtk using the commands show in this website, but no success. Ive decided that I first need to know if Ive got the right .inf file for the driver. Below is a copy of a post I did outlining the little progress Ive made and the problems Im having. Any advice would be most welcome:

For the past couple of days I have been trying to install the drivers for my PCI WLAN, it is a marvell 88w8335 Libertas. I have found the .inf file and have used ndiswrapper to install it. After I enter the line:

sudo ndiswrapper -i mrv8335.inf

i get the following line 

cannot open mrv8335.inf no such file or directory /usr/sbin/ndiswrapper -1.9 line 181

The when I enter 

ndiswrapper -l 

i get

mrv8335 : invalid driver

I have stored the driver files in a file called 'drivers' on my desktop, following the steps given in Keir Roberts book Beginning Ubuntu. And have also used the instructions on the webpage wifi/driver/mrv8k ([https://help.ubuntu.com/community/Wi...cs%2FDriver%29](https://help.ubuntu.com/community/Wi...cs%2FDriver%29)). But with no progress past what Ive stated above.

Thanks for reading, and look forward to any support I can get.

---

