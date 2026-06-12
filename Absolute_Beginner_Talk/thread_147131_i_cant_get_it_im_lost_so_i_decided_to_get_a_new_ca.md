---
title: "i cant get it im lost so i decided to get a new card but now im lost there to"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by katarot on 2006-03-19
ok i want a card that works out of the box 
the only problem is that the card says it needs orinoco_cs chipset
and my laptop got a broadcom chip set 
i was just wondering if that would matter or not or do i need a card the uses broadcom

if i need a card that use broadcom can someone suggest a card thar works out of the box 

thanks

---

### Post by Zelut on 2006-03-19
I'm taking a guess here and assuming you're referring to wireless networking?  I'm unclear on what hardware you have.  Do you have a laptop with build-in broadcom chipset, or did you get the card requesting orinocs_cs?

---

### Post by katarot on 2006-03-19
my laptop is a dell inspiron 1300 and the broadcom is built in but i have tried everything to get the internet on ubuntu and it just not working so i have found a card that works out of the box but when i look at the driver/chipset it says
orinoco_cs

and i was wanting to know if that would work on my computer

---

### Post by Zelut on 2006-03-19
Two things..

1) If you've got a broadcom chipset I can almost guarantee that we can get you working with ndiswrapper (uses windows driver, but works great).

2) How do you know that it works 'out of the box' if you haven't tried it?  I'm confused on this part.

---

### Post by katarot on 2006-03-19
i know it works out of the box because in the wiki there is a list of wirleless cards and it tell you what ones dont and what you need to install them and stuff

i have tried everything for broadcom i cant get it maybe you could help me there

---

### Post by Zelut on 2006-03-19
Run the following two commands from your terminal & post the output would you?  We'll find the right driver for you & (I shouldn't do this, it gets me in trouble) get you running by days end.

sudo lspci | grep 802.11
sudo lspci -n

(also take a look at the wireless howto in my signature.. others find it helpful, but I can walk you thru it if you need.)

---

### Post by katarot on 2006-03-19
ok i will take me about 5 10 got to swicth over im dual booting

---

### Post by katarot on 2006-03-19
i got these two but they werent the way you said sorry about that i could not get the command right but i got these of the devices 

broadcom corportion :unknown device 4318
broadcom corporation BCM4401-B0 100Base-TX

i found my usb flash drive so i can copy and paste what you tell me now
 EDIT sorry i just read your guide i will have to go back and redo the steps 
thanks for your patience and help

---

### Post by katarot on 2006-03-19
ok  sorry about that heres what i got

1) 0000:02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:02:03.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)

2)
0000:00:00.0 0600: 8086:2590 (rev 03)
0000:00:02.0 0300: 8086:2592 (rev 03)
0000:00:02.1 0380: 8086:2792 (rev 03)
0000:00:1b.0 0403: 8086:2668 (rev 03)
0000:00:1c.0 0604: 8086:2660 (rev 03)
0000:00:1c.3 0604: 8086:2666 (rev 03)
0000:00:1d.0 0c03: 8086:2658 (rev 03)
0000:00:1d.1 0c03: 8086:2659 (rev 03)
0000:00:1d.2 0c03: 8086:265a (rev 03)
0000:00:1d.3 0c03: 8086:265b (rev 03)
0000:00:1d.7 0c03: 8086:265c (rev 03)
0000:00:1e.0 0604: 8086:2448 (rev d3)
0000:00:1f.0 0601: 8086:2641 (rev 03)
0000:00:1f.1 0101: 8086:266f (rev 03)
0000:02:00.0 0200: 14e4:170c (rev 02)
0000:02:03.0 0280: 14e4:4318 (rev 02)
ok im a bit confused now do i google all these numbers

---

### Post by Zelut on 2006-03-19
No problem, we only need to google the string matching the output from #1 above.  Your output from #1 shows:
"0000:02:03.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)", which is your wireless card.  We match the string of leading numbers to the output from #2 to find the PCI ID.  Thus, "0000:02:03.0 0280: 14e4:4318 (rev 02)"  We then search the known-supported list ([Ndiswrapper Wiki]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List")) for suggested drivers and...

Let me find your driver... (3 minute delay)

issue the following at terminal:
> 
sudo apt-get install ndiswrapper-utils
wget [http://christer.homeip.net/bcmwl5.inf](http://christer.homeip.net/bcmwl5.inf)
wget [http://christer.homeip.net/bcmwl5.sys](http://christer.homeip.net/bcmwl5.sys)
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l (that is an L)


Does that output 'driver present, hardware present'?

---

### Post by Papa-san on 2006-03-19
Hello,
I guess I'm going to bust in on this thread... I am running into the same thing with my Dell... I have run through EVERY wiki, and how to I can find to enable my wireless, but to no avail... (The one I haven't tried yet is the one created in your sig...)

Oh, I have the bmcwl5.inf and .sys, my wife is loading them at our website so you can d/l to your desktop...

As far as googling the numbers, start with the last one on the list... If it is a truemobile 1300 card, (Sounds right...)
```
 john@laptop:~$ sudo ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present

```

---

### Post by katarot on 2006-03-20
i got it thanks i owe you big time  im writing this message from ubuntu just now 
i cant tell you how greatful iam thank you sooo much

---

### Post by katarot on 2006-03-20
papa-san that one defanatly works so go with that one  also dont get the drivers from dell they do not work the ones im using is acer one of there laptops has the same as dell 

this thread might help you
[http://www.ubuntuforums.org/showthread.php?t=142899&highlight=dell+wlan+mini-pci](http://www.ubuntuforums.org/showthread.php?t=142899&highlight=dell+wlan+mini-pci)

here is the drivers i used 
[ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/80211g.zip](ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/80211g.zip)

emm also it didnt work the first time untill i moved all the files which i got from acer 
to a folder in ubuntu

---

