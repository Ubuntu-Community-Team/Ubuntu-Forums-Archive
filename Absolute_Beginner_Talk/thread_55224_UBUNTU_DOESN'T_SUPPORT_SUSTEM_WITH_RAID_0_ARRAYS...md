---
title: "UBUNTU DOESN'T SUPPORT SUSTEM WITH RAID 0 ARRAYS??.. Also problem with ADSL"
date: 2005-08-07
forum: Absolute Beginner Talk
---

### Post by JuanPedro on 2005-08-07
Hello Ubunturers

Well I cannot Install Ubuntu because I have a Raid 0 Array (Via Via 8237) Made with 2 Sata Drives, and the Ubuntu Install CD (5.04) Doesn't recognize it. It only shows up the 2 hard drives. The fact is that I had prepared a new partition for ubunto previously with 20GB and ext3 and the installer hasn't seen it.  

Well.. all of we know windows sucks in some ways.. by the other side I'm a Student at the University and all my programming work must be done under Linux.

What can I do to install Ubuntu onto my Raid Array?  Something can be done?

Ahh another thing. The installer also didn't recognize my internet Connection, that is an ADSL with modem, with username and pass. In windows i just have to install the raspppoe protocol and query the available services on my ethernet. Then create a conection for that service and just dial with it.

What do we ADSL users do with Ubuntu?  

I thought it was easier to install it  

Well.. hope somebody can help me

Thanks

---

### Post by coolblue on 2005-08-08
Oh thats so easy:)
Type sudo /usr/sbin/pppoeconf at terminal
I answered yes to all questions, gave my username & password.....and was online in a jiffy!
I did this in Kubuntu and its works...hope it works in ubuntu too.

---

### Post by ozzie123 on 2005-08-08
It should worked the same under ubuntu because it doesn't mess with GNOME nor KDE files.

---

### Post by poofyhairguy on 2005-08-08
[QUOTE=JuanPedro]Hello Ubunturers

Well I cannot Install Ubuntu because I have a Raid 0 Array (Via Via 8237) Made with 2 Sata Drives, and the Ubuntu Install CD (5.04) Doesn't recognize it. It only shows up the 2 hard drives. The fact is that I had prepared a new partition for ubunto previously with 20GB and ext3 and the installer hasn't seen it.  
[/QUOTE]

SATA is hit or miss. I went and bought a cheap SIS Sata card from newegg after some research- perfect support:


[http://secure.newegg.com/NewVersion/FeedBack/CustRatingReview.asp?Item=N82E16815124020](http://secure.newegg.com/NewVersion/FeedBack/CustRatingReview.asp?Item=N82E16815124020)

PERFECT

(by the way, this is the best way to fix harware problems in Linux)

---

### Post by JuanPedro on 2005-08-09
> (by the way, this is the best way to fix harware problems in Linux)

Buying new hardware? jajajajaja

I think my chipset is common enought and good enought to be supported.. it comes with the Abit KV7 Mobo. 

Any help?  :-|

---

### Post by poofyhairguy on 2005-08-09
[QUOTE=JuanPedro]
I think my chipset is common enought and good enought to be supported.[/QUOTE]

What you think about your hardware or how popular it is does not matter. What does matter is that the hardware has open specs so that Linux can use it. I gave you a link to a card I spend over an hour researching to find. It has open specs, so its supported in Ubuntu and any modern Linux.

If you can find another solution then please use it. If you can't at least this community gave you an option. I think I remember when I researched, things telling me to stay away from what you have now (for Linux support) but I could be mistaken.

---

### Post by npaladin2000 on 2005-08-10
[QUOTE=JuanPedro]Buying new hardware? jajajajaja

I think my chipset is common enought and good enought to be supported.. it comes with the Abit KV7 Mobo. 

Any help?  :-|[/QUOTE]
 If you think it's so common, ask Via for the drivers for Linux.  They're the ones that provided the Windows drivers that made it so "well supported."   

In other words, do you honestly think you could install Windows XP (even SP2) to that RAID-0 array without manufacturer provided drivers?

It REALLY annoys me when people use hardware that isn't supported by Microsoft, and say Windows supports it well, and then when the SAME MANUFACTURER doesn't provide Linux drivers, they bellyache that LINUX sucks because it doesn't have drivers.

I'm going to start my own hardware company, and sell hardware and ONLY provide Linux drivers.  Who do you think people will blame, me or the infallible wonderful all-wise Bill and his siamese twin Paul?

---

