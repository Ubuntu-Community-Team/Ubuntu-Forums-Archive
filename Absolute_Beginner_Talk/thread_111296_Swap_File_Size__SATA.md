---
title: "Swap File Size / SATA"
date: 2006-01-02
forum: Absolute Beginner Talk
---

### Post by mitdxiw on 2006-01-02
I will be installing Breezy on my new PC that I am building in a couple weeks. I will have a SATA 3.0 gb/sec 250gb hard disk that will be used. I just have a couple quick questions:

1) how big should I make my swap file? 2gb?
2) do I need to have the SATA drivers on a floppy for the installer to recognize the drive, like you have to in windows xp?

---

### Post by mazelado on 2006-01-02
Not sure about the SATA portion of your question, but the recommended size for the swap partition is typically twice the amound of RAM in your system. For example, if you have 1 GB of RAM, you should have about a 2 GB swap partition. You can make it larger if you like, but I would recommend against making it any smaller.

---

### Post by poofyhairguy on 2006-01-02
[QUOTE=mazelado]Not sure about the SATA portion of your question, but the recommended size for the swap partition is typically twice the amound of RAM in your system. For example, if you have 1 GB of RAM, you should have about a 2 GB swap partition. [/QUOTE]

Only if you need hibernate/suspend support. Otherwise a GIG of swap is always enough.

If your SATA controller is supported by Ubuntu than it will just work, without a floppy. You will just be able to install to the drive. 

If you SATA controller is not supported by Ubuntu, than there is no way to make it work. Unlike Windows, Ubuntu's drivers come with it. So if it lacks a driver, there is no way to get it. Its kinda hit or miss.

If yours does not work out of the box, your options are to wait until the next release to install Ubuntu- hoping it works then- or buying a controller card you know works with Linux like this one of mine:

[http://www.monoprice.com/products/product.asp?c_id=104&cp_id=10407&cs_id=1040702&p_id=2667&seq=1&format=2&style=](http://www.monoprice.com/products/product.asp?c_id=104&cp_id=10407&cs_id=1040702&p_id=2667&seq=1&format=2&style=)

I hope yours works. Have a nice day.

---

### Post by mitdxiw on 2006-01-03
Is there anyplace I can get a list of supported SATA devices? I dont want to partition my drives, instlal windows and then go to install ubuntu and have a nasty surprise.. this is kind of disappointing.. I've been really psyched and research a lot into Ubuntu. Theres no way to get the driver externally?

---

