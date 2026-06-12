---
title: "Look out! Linux Newbie here"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by chevyss on 2006-03-22
Hi Ubuntu, 
A friend gave me a live CD.I have been using this live CD for about a week. I got the guts enough to install Ubuntu. Everything went perfect. I installed it many diferent ways. 
However, I know I know, I do have a problem getting hooked up to my NIC card. I see it listed and it is being recognized but I am at a bit of a loss on how to get it to work... So far that is my only issue. I think it is simple? 
I am running a Speed Stream Modem with a Linksys wireless B router. The Nic card is a Linksys. 

I hope this clears my problem up.

Thanks!

---

### Post by John.Michael.Kane on 2006-03-22
[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?highlight=%28card%29%7C%28network%29](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?highlight=%28card%29%7C%28network%29)
[https://wiki.ubuntu.com/WiFiHowto](https://wiki.ubuntu.com/WiFiHowto)
[http://www.linux-wlan.org/docs/wlan_adapters.html.gz](http://www.linux-wlan.org/docs/wlan_adapters.html.gz)

---

### Post by IYY on 2006-03-22
If it worked correctly on the LiveCD:

System > Administration > Networking, select your device and click Enable. If it's already enabled, try disabling it, and then enabling it again.

---

### Post by chevyss on 2006-03-22
Hey!,
IYY and SD-Plissken I will do just that. 


Thank you VERY much.

---

### Post by chevyss on 2006-03-24
I guess Linksys wireless model that I have is not compatable with Linux. Oh well what do you do.
I have not found the page yet but is there a compatability list of routers and NIC's for Ubuntu Linux? 

Thanks.   :D

---

### Post by taurus on 2006-03-24
Well, I have Linksys Wireless G WPC54G Notebook Adapter (802.11g) and it is working just fine in Ubuntu (HP laptop) using ndiswrapper.

---

### Post by PFI_Optix on 2006-03-24
I think your wireless card uses the RTL8180L chip, same as my Ashton Digital. I had the same problem when I installed yesterday...I found this thread:

[http://www.ubuntuforums.org/showthread.php?t=96989](http://www.ubuntuforums.org/showthread.php?t=96989)

Worked like a charm.

edit: check your device manager. It should show the card connected to the PCMCIA slot and indicate what kind of device it is. That's houw I found out what driver I needed to find.

---

### Post by dus10 on 2006-08-02
Hey, need help with my Ashton usb stick.  Which driver do I need?  Yes, it may be already explained, but I'm a total noob.

---

