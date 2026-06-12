---
title: "No Mouse after new install. Quick-key for prompt?"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by Shack on 2007-07-09
Hey there. I just installed Ubuntu 6.06LTS version and my installation went fine. There's only slight problem with usb-ports coz it seems like none of them is working. I only have usb-mouse so I'm only using keyboards at the moment. 

I have Fujitsu-Siemens computer with, MSI K7T266 Pro2 MS-6380 motherboard. How can I enter terminal with my keyboard, is there some shortcut key?

Thanks.

EDIT: I got to failsafe terminal, but it seems like that my network card is also out of order. Is it that failsafe doesn't load network card drivers? 
What are your suggestions about what to do, I should get my mouse working so I can start easily install software at gnome.

---

### Post by Old Pink on 2007-07-09
To get a terminal, log in as usual and then use [B]Ctrl + Alt + F1

[/B]You'll get a fullscreen terminal, do what you need to do, and then to get back to your GUI use [B]Ctrl + Alt + F7 

[/B]Find your mouse drivers, install them via. terminal or by using only the keyboard in GUI, then use **sudo reboot now** to reboot. :)

---

### Post by Shack on 2007-07-09
> **Old Pink said:**
> To get a terminal, log in as usual and then use [B]Ctrl + Alt + F1

[/B]You'll get a fullscreen terminal, do what you need to do, and then to get back to your GUI use [B]Ctrl + Alt + F7 

[/B]Find your mouse drivers, install them via. terminal or by using only the keyboard in GUI, then use **sudo reboot now** to reboot. :)

Thanks for this. Tought I think I have to install usb port drivers? Coz none of the usb-port seems to respond.
How can I check if the usb-port are active and the fault is not there?

---

### Post by Old Pink on 2007-07-09
> **Shack said:**
> Thanks for this. Tought I think I have to install usb port drivers? Coz none of the usb-port seems to respond.
How can I check if the usb-port are active and the fault is not there?

Go into terminal, like I said above [B]Ctrl + Alt + F1

[/B]Plug something (anything) in, and type **dmesg**

Read the last few lines of output, see if there's anything relevant to what you plugged in. If there is, your USB ports are working. If there isn't, your USB ports might not be working. If you can't tell, type **dmesg** first, have a look then plug something in, **dmesg** again and see if it's changed. :) 

If your USB ports aren't working for sure, why not buy a USB > PS2 adapter, so you can at least use your mouse while you're trying to get them fixed.

Link: [http://search.ebay.com/USB-ps2-converter_Computers-Networking_W0QQcatrefZC6QQfbfmtZ1QQfclZ3QQfromZR10QQfrppZ50QQfsooZ1QQfsopZ3QQftrtZ1QQftrvZ1QQsabfmtsZ2QQsacatZ58058QQsaprchiZQQsaprcloZQQsascsZ2QQsbrsrtZdQQsofindtypeZ0](http://search.ebay.com/USB-ps2-converter_Computers-Networking_W0QQcatrefZC6QQfbfmtZ1QQfclZ3QQfromZR10QQfrppZ50QQfsooZ1QQfsopZ3QQftrtZ1QQftrvZ1QQsabfmtsZ2QQsacatZ58058QQsaprchiZQQsaprcloZQQsascsZ2QQsbrsrtZdQQsofindtypeZ0)

---

### Post by Shack on 2007-07-09
> **Old Pink said:**
> Go into terminal, like I said above [B]Ctrl + Alt + F1

[/B]Plug something (anything) in, and type **dmesg**

Read the last few lines of output, see if there's anything relevant to what you plugged in. If there is, your USB ports are working. If there isn't, your USB ports might not be working. If you can't tell, type **dmesg** first, have a look then plug something in, **dmesg** again and see if it's changed. :) 

Thanks again for your help. I'll try these tips later when I'm back at home. I'll post here when I've tried it.

> **Old Pink said:**
> 

If your USB ports aren't working for sure, why not buy a USB > PS2 adapter, so you can at least use your mouse while you're trying to get them fixed.

Link: [http://search.ebay.com/USB-ps2-converter_Computers-Networking_W0QQcatrefZC6QQfbfmtZ1QQfclZ3QQfromZR10QQfrppZ50QQfsooZ1QQfsopZ3QQftrtZ1QQftrvZ1QQsabfmtsZ2QQsacatZ58058QQsaprchiZQQsaprcloZQQsascsZ2QQsbrsrtZdQQsofindtypeZ0](http://search.ebay.com/USB-ps2-converter_Computers-Networking_W0QQcatrefZC6QQfbfmtZ1QQfclZ3QQfromZR10QQfrppZ50QQfsooZ1QQfsopZ3QQftrtZ1QQftrvZ1QQsabfmtsZ2QQsacatZ58058QQsaprchiZQQsaprcloZQQsascsZ2QQsbrsrtZdQQsofindtypeZ0)


Yes, this was something I was also thinking, but I don't want to give up so easily :)

---

