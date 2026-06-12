---
title: "Wi-Fi on a Live Cd, Should it work?"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by EnergySamus on 2007-12-10
Hello!
I recently used the Live Cd to check out Ubuntu 7.10. Ubuntu is excellent! From the interface to the applications, Ubuntu has something for everyone! But I have an issue. Everything works fine, except my Wi-Fi. Is it normal for Wi-Fi not to work with the Live CD? It is a laptop I am using, plus I travel a lot, so Wi-Fi is crucial! I am looking into switching to Ubuntu too. :confused:

Thanks,
EnergySamus

---

### Post by Don1500 on 2007-12-10
The wi-fi would have to be re-initiated every time you log in. I use Puppy (3.01) on a 1Gig USB stick  for my laptop (Dell D620) and everything works fine.

---

### Post by EnergySamus on 2007-12-10
Thank you, but I am not sure what that means:lolflag:
Will it work once I install Ubuntu?
Sorry, I am just a beginner at the whole Ubuntu thing!

Thanks,
EnergySamus

---

### Post by Don1500 on 2007-12-10
Puppy is another distro of Linux. You install it INSTEAD of Ubuntu. It is very small and you can install it on a USB memory stick. It has many of the same features as Ubuntu and runs the same software (Firefox, Open Office). Like all Linux distros itis free. Here is the link:
[http://www.puppylinux.org/](http://www.puppylinux.org/)

I like Ubuntu better but Puppy gets the job done without bothering my windows install on the laptop. I need the Windows for my work and it can't be online at all. I travel alot, too. This is the best setup for my laptop requirements. On my desktop I have Ubuntu and UbuntuStudio (I'm trying to decide which one I like best.)

---

### Post by erfahren on 2007-12-10
It may take some setting up, but you should be able to get it to work. 

What kind of laptop and what wifi card do you have?

---

### Post by meborc on 2007-12-10
can you tell us what wifi card/chip are you using? there is a lot of information available for different cind of wireless cards :)

ubuntu might work out of the box.. but it also might not... you might need to add some special drivers etc... it all depends on the card

and this off topic thing about puppy :D well... i like puppy... i use it for machines <64M ram... it is cool... but for every day use? and for a linux starter? no

---

### Post by ExpatPaul on 2007-12-10
Wi-Fi should work from the Live CD - it did for me - although you will need to re-enter your network password every time you boot from the CD. This is because the CD doesn't make any changes to your system and, therefore, doesn't save your password.

What messages are you getting when you try to connect with Wi-Fi?

---

### Post by EnergySamus on 2007-12-10
I have an Acer Aspire 3690, 1GB of RAM, Intel Celeron M 1.6 GHz.
My guide says that I have an Acer SignalUp 802.11 b/g.
I don't get an error message.
When I try to connect, I enter my connection's password, but nothing happens!

Does anyone know of this issue?:confused:

Thanks!
Samusgravity

---

### Post by erfahren on 2007-12-10
While in the Live CD go to the terminal (Applications > Accessories > Terminal) and enter:
```

lspci

```
just look in the list for the Ethernet controllers - the wireless specifically - and post what it says

---

### Post by EnergySamus on 2007-12-10
I won't be booting into Ubuntu till later today, I will update on it later!

Thank you for your help!!!
EnergySamus:guitar:

---

### Post by fatality_uk on 2007-12-10
Couple of things for you (and anyone) to try. Before you try this make sure that your WIFI is set to broadcast your SSID

1) When you run the live CD, click once on the network manager icon and if your network is  on the list of available networks, your WIFI chipset has been picked up by 7.10 succesfully, and as such, when you do an install, you should have access to your network straight away.

2) In Ubuntu, there is a program called Keyring Manager. This is designed to store important items securly, like network passwords etc so you don't have to type them in each time. However, there is a known bug in the network-manager = keyring manager relationship. This means that sometimes, a keyring wont be stored and you will have to enter your network password each time you log on. Check the forums for way around this.

I personally use a program call Wicd which is available here [http://wicd.sourceforge.net]("http://wicd.sourceforge.net")

Hope this helps

---

### Post by EnergySamus on 2007-12-10
I'm back! I went into the terminal and got the Wifi writing. Here it is.



05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)



There was also an ethernet adapter one:



06:01.0 Ethernet controller: Broadcom Corporation BCM4401-BO 100Base-TX (rev-02)



Have any idea about what it is? 
Thanks
EnergySamus

---

### Post by LookTJ on 2007-12-10
> **EnergySamus said:**
> I'm back! I went into the terminal and got the Wifi writing. Here it is.



05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)



There was also an ethernet adapter one:



06:01.0 Ethernet controller: Broadcom Corporation BCM4401-BO 100Base-TX (rev-02)



Have any idea about what it is? 
Thanks
EnergySamus
You would have to use ndiswrapper for broadcom devices. Let me go find a link :)

---

### Post by LookTJ on 2007-12-10
Here is what I found. [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29?highlight=%28ndiswrapper%29)

---

### Post by EnergySamus on 2007-12-10
Thanks! This will really help!

EnergySamus

---

