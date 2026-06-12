---
title: "Help needed installing mrv8k PCI Drivers"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by Killy1 on 2007-12-23
For the past couple of days I have been trying to install the drivers for my PCI WLAN, it is a marvell 88w8335 Libertas. I have found the .inf file and have used ndiswrapper to install it. After I enter the line:

sudo ndiswrapper -i mrv8335.inf

i get the following line 

cannot open mrv8335.inf no such file or directory  /usr/sbin/ndiswrapper -1.9 line 181

The when I enter 

ndiswrapper -l 

i get

mrv8335 : invalid driver

I have stored the driver files in a file called 'drivers' on my desktop, following the steps given in Keir Roberts book Beginning Ubuntu. And have also used the instructions on the webpage wifi/driver/mrv8k ([https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k?highlight=%28WifiDocs%2FDriver%29](https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k?highlight=%28WifiDocs%2FDriver%29)). But with no progress past what Ive stated above.

I would really appreciate some help with this, as my head is spinning with all the different instructions on this topic. I am new to Linux this week, so not sure if Im using the corrects terms, Thanks.

---

