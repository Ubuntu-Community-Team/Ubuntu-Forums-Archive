---
title: "Sabrent USB 2.0 TV Tuner"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by gregcha117 on 2006-12-23
I am loving Ubuntu except for one small thing, I cannot seem to get it to recognize my tv tuner, if this helps at all the website is [www.sabrent.com](www.sabrent.com) but they have nothing about linux support, I can't seem to get anywhere, under device manager it recognizes it as "tvbox" but nothing actually comes up in tvtime or zapping tv viewer
and i guess it uses the "Trident TV Master 5600 " chipset
can someone help me out please ?

i typed dmesg in terminal (found that somewhere) 
and it came up with this 

[17183848.896000] usb 2-3: USB disconnect, address 3
[17183853.420000] usb 2-3: new high speed USB device using ehci_hcd and address 4
[17183853.560000] usb 2-3: configuration #1 chosen from 1 choice


if that helps at all?

---

### Post by kd7swh on 2006-12-24
I don't know much about tv tuners but you could try mythtv.
They also have forums full of people who do nothing but this stuff.

[http://www.mythtv.org/](http://www.mythtv.org/)

---

### Post by fbifido on 2008-07-10
Can a programmer help with this unit.
i am new to linux and i tried mythubuntu to see if my usb-tv unit will work. I works very good on win xp pro sp2/3. This shows up as "Tv Walker QQ" on my pc under windows xp.
I use the composite connector, not the tuner.


found these site to have the drivers for linux make.

unit:
[http://www.sabrent.com/products/specs/TV-USB20.htm](http://www.sabrent.com/products/specs/TV-USB20.htm)
chipset: TV Master TM5600
Bus 004 Device 004: ID 6000:0001

how-to
[http://www.linuxtv.org/wiki/index.php/Development:_How_to_develop_drivers_for_USB_based_devices](http://www.linuxtv.org/wiki/index.php/Development:_How_to_develop_drivers_for_USB_based_devices)
[http://www.linuxjournal.com/article/4786](http://www.linuxjournal.com/article/4786)
[http://www.linuxjournal.com/article/7353](http://www.linuxjournal.com/article/7353)

trying to write driver for Tm5600/Tm6000/Tm6010
[http://linuxtv.org/hg/~mchehab/tm6010/](http://linuxtv.org/hg/~mchehab/tm6010/)

---

