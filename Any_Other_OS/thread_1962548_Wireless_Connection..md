---
title: "Wireless Connection."
date: 2012-04-21
forum: Any Other OS
---

### Post by hugom on 2012-04-21
Hi there,

I'm pretty new to Linux so thought I'd try out Distros like ubuntu and linux mint. I'm actually using LINUX MINT DEBIAN EDITION and would like some help connecting to wireless.

So, I have installed LMDE and when i click the network icon in the bottom right there is no option for wireless. So I try and install the driver. There is an option under administration that allows you to install Windows Wireless Drivers. So I go to the Toshiba website, navigate to my make and model and download my network driver. 

I try to install it with Windows Wireless Drivers but i get an error saying ... module could not be loaded. Error was: Fatal: module ndiswrapper not found.

I've been trying to get this sorted a few days now but I don't know what to do. I really want to give Linux a good try but for that I need wireless connectivity. I have asked on Linux Mint Forums but have got no help from anyone so asking here.

I have a broadcom 802.11n network adapter if that helps.

Thanks.

---

### Post by leclerc65 on 2012-04-21
Install **ndisgtk** using Synaptic then run it.

---

### Post by hugom on 2012-04-21
Hi there, 

I tried that thanks but it said I already have it installed. So i reinstalled it but I continue to get the same error message...

---

### Post by leclerc65 on 2012-04-22
In the search field of Synaptic, type 'ndis', do you see the 3 modules ticked like this screen ?

---

### Post by hugom on 2012-04-24
Thanks for the help. I just installed Linux Mint 12 and it worked right after installation.

---

### Post by The Rnegade on 2012-05-02
> **hugom said:**
> Hi there,

I'm pretty new to Linux so thought I'd try out Distros like ubuntu and linux mint. I'm actually using LINUX MINT DEBIAN EDITION and would like some help connecting to wireless.

So, I have installed LMDE and when i click the network icon in the bottom right there is no option for wireless. So I try and install the driver. There is an option under administration that allows you to install Windows Wireless Drivers. So I go to the Toshiba website, navigate to my make and model and download my network driver. 

I try to install it with Windows Wireless Drivers but i get an error saying ... module could not be loaded. Error was: Fatal: module ndiswrapper not found.

I've been trying to get this sorted a few days now but I don't know what to do. I really want to give Linux a good try but for that I need wireless connectivity. I have asked on Linux Mint Forums but have got no help from anyone so asking here.

I have a broadcom 802.11n network adapter if that helps.


Thanks.

check synaptic to see if everything needed is installed, also remember that the driver you use has to be the same architecture as your operating system is

my mistake, i should have read all the responses before replying, i see the problem is solved

---

