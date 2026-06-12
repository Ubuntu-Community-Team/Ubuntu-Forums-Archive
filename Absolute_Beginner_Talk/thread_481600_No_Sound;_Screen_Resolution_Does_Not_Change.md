---
title: "No Sound; Screen Resolution Does Not Change"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by GG_HTPC on 2007-06-22
Hi Everyonne,
I am absolutely new to Ubuntu. I just installed 7.0.4 from LiveCD but I am facing (basic) problems. I am wondering if anyone can help. Thank you in advance.

a) No sound on SPDIF out of my sound card (integrated Realtek882). ASUS motherboard driver CD has the linux drivers (realtek-linux-audiopack-3.5-6b.tar.bz2) but how do I install it or do I need to install it seperately?

b) I have nVIDIA GeForce 7950 PCI card hooked up to a HDTV. After installing Ubuntu to my HDD and enabling the "nVidia Restricted Driver", I can not change my resolution any higher than 800x600. I tried installing the configuration packages but Ubuntu gave errors. Do I need to download the drivers fron nvidia site and install them to enable configuration utilities?

Thank you again.

---

### Post by netyire on 2007-06-23
I may be able to help you with B. The settings for X (the display) is stored in "/etc/X11/xorg.conf", when I first installed 7.04, I did experience a problem with changing the screen's refresh rate.

Could you please post your xorg.conf file. Thanks!

---

### Post by phr0ze on 2007-06-23
Yes, your refresh rate in your xorg is not high enough. Only set to values your display can handle. You will need to set both horiz and vert

---

### Post by clarkpoon on 2007-06-23
> a) No sound on SPDIF out of my sound card (integrated Realtek882). ASUS motherboard driver CD has the linux drivers (realtek-linux-audiopack-3.5-6b.tar.bz2) but how do I install it or do I need to install it seperately?

But How to Install Applicatons? i'm also new to Ubuntu :) don't know how to install Drivers coz i don't hav Internet drivers installed. so plz help me. i'm so borred from windows family OS's!

Thanks

---

### Post by phr0ze on 2007-06-23
Your internet doesn't work? That should always be your first goal cause everything else uses the internet.  Once you have the network setup you should go to System -> admin -> synaptic to install your software/drivers/etc.

---

### Post by phr0ze on 2007-06-23
Ohh, and Asus may have updated that driver too, so get the latest one from the web page.

---

### Post by clarkpoon on 2007-06-23
> **phr0ze said:**
> Your internet doesn't work? That should always be your first goal cause everything else uses the internet.  Once you have the network setup you should go to System -> admin -> synaptic to install your software/drivers/etc.

I Don't know How to Setup Network Connections :( Plz help me...

---

### Post by GG_HTPC on 2007-06-25
I tried installing the nvidia packages from Admin tools. Now the desktop will not start. I just get a DOS style screen :-(

---

### Post by GG_HTPC on 2007-07-02
Thank you everyone. I was able to fix the resolution problem. I had to enable the nvidia drivers from Restricted Drivers Menu.

---

