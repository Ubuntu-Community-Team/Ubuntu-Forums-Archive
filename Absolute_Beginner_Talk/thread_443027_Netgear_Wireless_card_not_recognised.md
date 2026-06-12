---
title: "Netgear Wireless card not recognised"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by timr92 on 2007-05-14
I just got a Netgear Wireless PC Card (WG511) and ubuntu 7.04 doesn't recognise it. It is a PCMCIA card and in an old Toshiba tecra 8000. Anyone know how i can get it working.

---

### Post by sethdotcom on 2007-05-14
ndiswrapper

get the correct driver for the card for windows and use it under ndiswrapper
I cant believe Ubuntu didn't detect it, it has gotten a lot better in hardware detection since Ubuntu 7.04
is this wifi card older?

---

### Post by timr92 on 2007-05-14
I don't get it. :( can u tell me exactly what to do. I didn't post in "absolute beginners talk" for no reason.

---

### Post by sethdotcom on 2007-05-14
> **timr92 said:**
> I don't get it. :( can u tell me exactly what to do. I didn't post in "absolute beginners talk" for no reason.
 

go to synaptics package manager and search for ndiswrapper and select all of the names that come up and then you have to get the .inf driver for your wifi card

do you have your windows drivers for it?

---

### Post by timr92 on 2007-05-14
thats all? and it will work even if the card doesn't appear anywhere in the network stuff?

---

### Post by sethdotcom on 2007-05-14
> **timr92 said:**
> thats all? and it will work even if the card doesn't appear anywhere in the network stuff?

get your .inf driver for your card

---

### Post by timr92 on 2007-05-14
and what do i do with it?

---

### Post by timr92 on 2007-05-14
> **sethdotcom said:**
> go to synaptics package manager and search for ndiswrapper and select all of the names that come up and then you have to get the .inf driver for your wifi card

do you have your windows drivers for it?

yes, i have the drivers, what version of windows does it need to be for?

---

### Post by aeiah on 2007-05-14
it would help if you can find out what version your wireless card is. there's at least three versions. im assuming you have one of the newer ones but try to confirm, because they swapped chipsets somewhere along the way

---

### Post by sethdotcom on 2007-05-14
> **timr92 said:**
> and what do i do with it?


just search for a .inf file you should come up with something, are you in windows right now?
after you install ndiswrapper you click system then administration then there is a program called windows wireless drivers then you browse to where ever you have your .inf driver located and it will install your wireless card

this should work but it does not work for all hardware

---

### Post by timr92 on 2007-05-14
> **aeiah said:**
> it would help if you can find out what version your wireless card is. there's at least three versions. im assuming you have one of the newer ones but try to confirm, because they swapped chipsets somewhere along the way

It says WG511 v2

---

### Post by sethdotcom on 2007-05-14
> **timr92 said:**
> It says WG511 v2

are you in windows right now and did you find the .inf file?

just search for .inf wherever you have your drivers

---

### Post by timr92 on 2007-05-14
> **sethdotcom said:**
> are you in windows right now and did you find the .inf file?

just search for .inf wherever you have your drivers

I have them all on the laptop, which one do i use. There is Win 98, 2000, ME, and XP

---

### Post by sethdotcom on 2007-05-14
> **timr92 said:**
> I have them all on the laptop, which one do i use. There is Win 98, 2000, ME, and XP

go with xp

you have the .inf file right, not the .exe but the .inf right?

---

### Post by aeiah on 2007-05-14
check post number 16 here

[http://ubuntuforums.org/showpost.php?p=1721250&postcount=16](http://ubuntuforums.org/showpost.php?p=1721250&postcount=16)

if you're having problems with the xp ones, as these apparently work

---

### Post by timr92 on 2007-05-14
> **sethdotcom said:**
> go with xp

you have the .inf file right, not the .exe but the .inf right?

Yes, i have all of the inf's

---

### Post by Tux Aubrey on 2007-05-14
How are you going with this?  If you are having trouble, reply and I'll give you a step-by-step guide.  I have a Netgear wg511 version 2 working very well on feisty using ndiswrapper and have the CD and everything here for reference.

---

### Post by timr92 on 2007-05-14
> **aeiah said:**
> check post number 16 here

[http://ubuntuforums.org/showpost.php?p=1721250&postcount=16](http://ubuntuforums.org/showpost.php?p=1721250&postcount=16)

if you're having problems with the xp ones, as these apparently work

Ok, thanks

---

### Post by sethdotcom on 2007-05-14
if you need further assistance we are all here ready to help you
Ubuntu is all about support

---

### Post by timr92 on 2007-05-14
Tux, i PM'd u, can u step me through it there.

---

### Post by aeiah on 2007-05-14
it would be best for others if the solution is posted here, for when people do searches in future :)

thanks

---

### Post by Zeedok on 2007-05-14
This probably won't be helpful to you, but can you exchange the card you've got for a slightly different model??

You see I learned the hard way how using ndiswrapper etc can be frustrating - I never could get my USB WiFi dongle to be recognised (even though someone had the same one working previously etc).

In the end I bought the NetGear WG511**T**, which has an atheros chipset and uses the MadWiFi native linux drivers (therefore doesn't need ndiswrapper) and Feisty recognised the new card and installed my network automatically, on my Tecra 8100! 

Have a think about it - I'm yet to sell my now superfluous dongle, but the card only cost $40 - sensible investment . . .

---

### Post by timr92 on 2007-05-14
still not working.
I have:

Downloaded & Installed ndisgtk, ndiswrapper-common & ndiswrapper-utils-1.9

I had the drivers at /home/timothy/Drivers/Wireless/Windows XP

It wouldn't work via System > Administration > Windows Wireless Devices, so i tried it in a terminal:

It wouldn't work, so i put all of the files from that Windows XP folder into /home/timothy

sudo ndiswrapper -i /home/timothy/WG511v2.INF

It has worked and when i do ndiswrapper -l it says it is all good

But, there are no lights on it, in Windows Wireless Devices it says it is not connected & It is not in my Network Settings.

can anyone shed some light on this 4 me?

---

### Post by timr92 on 2007-05-14
> **Zeedok said:**
> This probably won't be helpful to you, but can you exchange the card you've got for a slightly different model??

You see I learned the hard way how using ndiswrapper etc can be frustrating - I never could get my USB WiFi dongle to be recognised (even though someone had the same one working previously etc).

In the end I bought the NetGear WG511**T**, which has an atheros chipset and uses the MadWiFi native linux drivers (therefore doesn't need ndiswrapper) and Feisty recognised the new card and installed my network automatically, on my Tecra 8100! 

Have a think about it - I'm yet to sell my now superfluous dongle, but the card only cost $40 - sensible investment . . .

I dont think so, it was internet purchase, but thanks anyway.

---

### Post by timr92 on 2007-05-14
> **timr92 said:**
> I dont think so, it was internet purchase, but thanks anyway.

I mean, i don't think i will be able to exchange it. If i cant make do with what i have got, i will have to get another one, different model.

---

