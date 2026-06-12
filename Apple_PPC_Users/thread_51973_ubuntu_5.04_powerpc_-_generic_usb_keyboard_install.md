---
title: "ubuntu 5.04 powerpc - generic usb keyboard install issues"
date: 2005-07-25
forum: Apple PPC Users
---

### Post by mm01 on 2005-07-25
I have a iMac G3 266mHz/32mB RAM All-in-one (strawberry color). It was purchaced from eBay with no keyboard or mouse so I went to Wal-mart and got a generic usb keyboard and a logitech usb optical mouse. The system works fine... I recently installed OS 8.6 on it and it runs beautifully. Today I tried installing ubuntu. I get a 'boot:' prompt and it seems to work normally. Unfortunatly my usb keyboard does not work so i cant finish booting the system. I even downloaded the LiveCD and tried running it but have the same problem. The keyboard works just fine after the system boots into OS.

Any help would be appreciated...
Thanks...

---

### Post by autocrosser on 2005-07-25
Well-I use to have a Blue & White G3--it had the same issue when trying to boot from any CD--Problem is that it needs to see the Mac keyboard to "really" work properly-- Thats why you can't type during openfirmware--I see Mac keyboards of that vintage all over eBay for 10-15us--you can use any mouse you want to---If you were to be able to check typing, you would find that the keyboard won't work until the USB extension loads in OS 8 thru OS9--Sorry about that--- :-? 

The newer Macs will "see" any USB unit in openfirmware--needs to be later than 2000--

Cheers!!
Dean

---

### Post by mm01 on 2005-07-26
Yeah... I kind of figured that I would end up having to lay down some more money. I was just shooting in the dark. Thanks for letting me know.

---

### Post by f_elz on 2005-07-26
interesting. my iMac 333 g3 has the same problem I cannot enter "boot" or "install" into my mac to get the disc to install. I have an apple pro extended kb (I think it's called that) and a pro keyboard. I get no response. Sucks, I really want to put Ubuntu on it. :mad:  :-|

---

### Post by mm01 on 2005-07-26
Good news!

I had a [Linksys Compact USB 4-Port HUB](http://www.amazon.com/exec/obidos/tg/detail/-/B0000658CH/102-4604990-9888143?v=glance) in a box of random parts. On a hunch, I decided to try the keyboard and mouse through the hub. To my surprise it worked! Maybe it picked up the hub before the keyboard then recognized what it was probing?

---

### Post by zxee on 2005-07-26
In searching the ppc forum for my issue I found this thread. I didn't want to start a new topic, and hope someone checking here has an idea on this...
I have a 500Mhz imac G3 DV SE with a imac keyboard and a macally mouse. The keyboard works fine but the mouse doesn't-no cursor movement at all. Maybe I'll buy a linksys usb hub, but what is the issue here? Why can't a usb mouse be recognized? I tried editing my xorg.conf but haven't had any luck. The mouse has an led light and it lights up but it's just a plastic paperweight as far as usability goes. Much thanks for any ideas!!! Oh and yes the mouse works in OS 9.

---

### Post by autocrosser on 2005-07-27
Cool--Is the Linksys a powered hub?? If so, it is likely that firmware is "polling" the hub early in the boot process--sounds like a good answer to me--I still like the "stock" keyboard, but--if it works :wink: run with it--

As for the Macally mouse--I use a Logitech Trackman with scrollwheel (trackball-type) --it is great in both MacOS & Linux--And that it was $29 was even better-- 

I'm not sure why a Macally unit won't work--you might goto Xorg & see if there is a answer there---

Of course, the best answer for everyone would be to use the iMac keyboard with a Linksys hub off of it---I bet that works great----

Cheers!!
Dean

---

### Post by zxee on 2005-07-27
I found out that the macally, while recognized during hardware detection, isn't supported.  :mad:  a microdaft usb mouse is-whatever.
I don't know if I messed up xorg, but I can't really log-in to the system. It is so slow that it's unbelievable-takes more than five minutes from entering password to opening gnome. When I 1st installed it didn't seem to take that much time  :???: 
I really like ubuntu on my athlon ( only 1Ghz ) but on ppc it's thumbs down all the way.

---

### Post by autocrosser on 2005-07-27
Hi Xzee--about your slow login time--try setting up another user to see if the same thing happens--If it changes things--you have a problem in your user dot files -- if not, then you have deeper problems---it sounds like a pref file is messed up--- :???: 

Sorry about your mouse--if you look in some of my prior posts, you will find a site that includes "almost" every USB device made & if it works in Linux--I'm at work so I can't link it right now--That is where I look to see if what I want will work or not--

---

### Post by zxee on 2005-07-28
[QUOTE=autocrosser]Hi Xzee--about your slow login time--try setting up another user to see if the same thing happens--If it changes things--you have a problem in your user dot files -- if not, then you have deeper problems---it sounds like a pref file is messed up--- :???: 

Sorry about your mouse--if you look in some of my prior posts, you will find a site that includes "almost" every USB device made & if it works in Linux--I'm at work so I can't link it right now--That is where I look to see if what I want will work or not--[/QUOTE]
 Thanks again for the response. When I'm having problems figuring things out I get "cranky'
I really like ubuntu-and this is a great forum.
So to set the record straight. What finally worked was to remove the last xorg.conf that was created by dpkg-reconfigure... went back to the first one from the install, and used the cheapo ( not really a microsoft ) just some off brand pc usb mouse-which works in OS 9 and ubuntu very well.
Except for a panel problem, which I created a new topic on, ubuntu is performing fine.
thanks

---

### Post by autocrosser on 2005-07-31
Glad to see you have it under control--I'm posting the website that has helped me with USB devices-- [http://www.qbik.ch/usb/devices/](http://www.qbik.ch/usb/devices/)

Has a fairly complete listing of devices & if they "really" work in Linux or not ;-)

---

