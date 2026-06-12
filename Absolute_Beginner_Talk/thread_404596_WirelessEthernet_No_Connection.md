---
title: "Wireless/Ethernet No Connection"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by nerdshack on 2007-04-08
Okay, I'm very new to Ubuntu and have recently installed it, the problem is that now I have absoloutely no internet connection at all, I've tried through Wireless and Ethernet Cable.
System>Administration>Networking, both my Ethernet & Wireless are active and a network has been chosen. 
Can anyone help me with this very annoying problem?

---

### Post by hnobleson on 2007-04-08
I too am having the same sort of trouble, I am using a mesh desktop with a belkin wireless pci card. 

When i found that my adapters name is eth1 i typed it in the correct field thinking it would work but instead it is perminatly disconnected. 

I have looked in network tools and the os doesn't seem to list the wireless adapter as a network device, despite it being in the device manager list. 

Can anyone help?

---

### Post by mi_were on 2007-04-08
> **hnobleson said:**
> I too am having the same sort of trouble, I am using a mesh desktop with a belkin wireless pci card. 

When i found that my adapters name is eth1 i typed it in the correct field thinking it would work but instead it is perminatly disconnected. 

I have looked in network tools and the os doesn't seem to list the wireless adapter as a network device, despite it being in the device manager list. 

Can anyone help?

First things first is to find out whether the drivers for your card are installed or need to be installed. did the card autoconfig when you using the LiveCD? If it did then you have a simple problem to sort out. If it did not then you will be looking to install the windows driver using ndiswrapper.

Let's have more info. I am sure if you search the forum for belkin wireless cards there is a wealth of information on them and even a quick howto on your particular model

---

### Post by mi_were on 2007-04-08
> **nerdshack said:**
> Okay, I'm very new to Ubuntu and have recently installed it, the problem is that now I have absoloutely no internet connection at all, I've tried through Wireless and Ethernet Cable.
System>Administration>Networking, both my Ethernet & Wireless are active and a network has been chosen. 
Can anyone help me with this very annoying problem?


If both are active check under the properties tab and see if them are enabled and also configured to your router

---

