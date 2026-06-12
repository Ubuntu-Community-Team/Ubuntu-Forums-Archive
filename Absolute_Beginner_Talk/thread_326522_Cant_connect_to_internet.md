---
title: "Cant connect to internet"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by mastergunner on 2006-12-27
I just finally got a Linux OS working on my computer and it was Ubuntu. I have one prob which is I cant connect to the interent. I use a USB cable modem. Can someone help me out with what I am suppose to do. Again I am a total newb and am really lost.

---

### Post by kepos on 2006-12-27
First you have to tell us which modem do you have?

---

### Post by halitech on 2006-12-27
a little more info will go along ways to help. what make/model of USB modem and who do you have your internet with?

---

### Post by mastergunner on 2006-12-27
It is a Scientific Atlanta Webstar Series 2000 and I have Road Runner. Could I have screwed up something during the install?

---

### Post by mastergunner on 2006-12-27
Can anyone else help?

---

### Post by mastergunner on 2006-12-27
HELP anyone?

---

### Post by JohnBortion on 2006-12-27
what happens if you open a terminal and type in ifconfig?

---

### Post by mastergunner on 2006-12-27
I get something dealing with eth0. Now I having nothing going through an ethernet. This is a USB modem.

---

### Post by JohnBortion on 2006-12-27
Is there an ethernet port in your modem?  It may simplify things if you can plug into the ethernet port.  You obviously have an ethernet port in your computer.
Please forgive me if I offend.  Ethernet looks like a big phone jack.  It's an older technology that's well supported by linux.  You have an ethernet port in your computer,
and probably you have one in your modem.  When they installed your modem they should have given you an ethernet cord that would connect your computer to your
modem.  I guess they gave you a usb cord too.  What you want to do is find that ethernet cord and try to use it.  It would be more reliable.

---

### Post by mastergunner on 2006-12-27
I tried that and still couldnt get on the internet.

---

### Post by Frak on 2006-12-27
There is a person named BrokeBody, that will hopefully be able to help you, I've requested his assistance to this thread.


Regards

Frak

---

### Post by JohnBortion on 2006-12-27
You tried it through ethernet?

---

### Post by halitech on 2006-12-27
acording to what I can find on the websitre for the modem, there are 4 different models that have 2100 in the name but all of them include a USB and Ethernet connections. If you can find it, hook up using ethernet and you will have ALOT less troubles

Edit: I see you have tried using Ethernet, I'm not sure on RR but you may need to register your MAC address with RR before you can get online. Check your IP using the ifconfig and let us know what it is

---

### Post by BrokeBody on 2006-12-27
> **Frak said:**
> There is a person named BrokeBody, that will hopefully be able to help you, I've requested his assistance to this thread.

Broke here. : )

OK, i have the same cable modem as you mastergunner. Setting it up on Ubuntu is simple...

Just connect your cable modem to your network card via straight UTP cable (which comes with any network card for LAN when you buy it) and that's it. :p No, typing in terminal, no scripts, drivers... nothing! Just connect them together.

I had the same problem when I connected my cable modem via USB cable, but then I bought D-Link network card (about 5 bucks :p ) and I connected them together. NO VIA USB PORTS! - Via network card. ;)

I just install Ubuntu and my cable internet is already up and running. :rolleyes:

Buy any D-Link network card and it will work. ;)

---

### Post by mastergunner on 2006-12-27
Broke I tried that and it didnt work. My motherboard has a network hook up and I have used it in the past. I hooked the ethernet cable from the modem to the computer booted up Ubuntu and it still didnt do anything? Really could use the help.

---

### Post by halitech on 2006-12-28
lets go back to basics for a minute. when you plug the RJ45 cable into your computer and the modem, do you have link lights on showing you have a connection between the modem and the computer? Do you have a connection showing as active on the modem to road runner?

---

### Post by k1001001 on 2006-12-28
Maybe try [disabling IPv6]("http://www.ubuntuforums.org/showthread.php?t=323747"). Directions are on post #3 of that thread. 

When I first switched to Ubuntu and brought my computer home, I could connect to my router, but Firefox had a lot of trouble loading pages (it took in excess of a minute to load Google) and Gaim wouldn't work at all. The problem was my crappy DSL modem didn't support IPv6. Once I disabled IPv6, my internet was up and working like normal. I don't know what IPv6 is, or what it does, but I assume it doesn't hurt to disable it. Anyways, if you are having similar symptoms, you might want to try it.

---

### Post by BrokeBody on 2006-12-28
Just curious, do you have integrated network card on ASUS motherboard? :-k

---

### Post by mastergunner on 2006-12-28
Halitech that is a negative I dont. In Device Manage the network adaptert says it is operating properly.

---

### Post by BrokeBody on 2006-12-28
Go to System->Administration-> Networking and then select "Wired connection", then go to properties and set up your IP adress' parameteres if you have a static or real IP adress. If not, choose DHCP (Automatic Configuration) and check "Enable" button.

---

### Post by mastergunner on 2006-12-28
OK I found my old Linksys ethernet card and popped it in. I have a blinking light BUT I get limited or no connectivity message. It says coonnected at 100MPS. Now Brokebody am I suppose to do that in Linux or XP? Also how do I know if I have DHCP?

---

### Post by BrokeBody on 2006-12-28
[QUOTE=mastergunner]Brokebody am I suppose to do that in Linux or XP? Also how do I know if I have DHCP?[/QUOTE]

The instructions I gave you are for Ubuntu. For XP is a bit different, but the principle is everywhere the same.

Call your Internet service provider and ask them if you have Static IP adress or Automated (DHCP). If you have Static IP adress, they MUST tell you which one is it, and give you all the parameters needed. It's their job to tell you and give you that. Afcourse, before asking them, check if it's Automated (DHCP) already and see if it's working - It must work if it is over DHCP. If not, call your ISP and ask for your IP adress and parametres for it.

---

### Post by mastergunner on 2006-12-28
WOLLA I have it and through the USB Modem. Thanks Broke Body your post #20 sort of did it. I went to network and then activated eth1 and I had internet. WOW something so simple I feel like an idiot. Now how do I get my HP Laserjet 1020 to work? I went to printers and added it but it doesnt work.

---

### Post by BrokeBody on 2006-12-28
> **mastergunner]WOLLA I have it and through the USB Modem. Thanks Broke Body your post #20 sort of did it. I went to network and then activated eth1 and I had internet. WOW something so simple I feel like an idiot.[/QUOTE]

So, nowdays it also works via USB.  said:**
> Now how do I get my HP Laserjet 1020 to work? I went to printers and added it but it doesnt work.

*bump* : )

---

