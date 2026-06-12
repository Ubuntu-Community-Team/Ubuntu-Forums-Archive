---
title: "Broadcom Wireless 802.11g"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by _SteveM on 2006-03-16
Hi, 

Im wanting to install ubuntu on my laptop, however to get on the internet my laptop connects to my wireless router. 

I was wondering if anyone has a Wireless Broadcom device and has gotten it to work within ubuntu?

If the answer is yes then i'll be switching asap :-D 

Thanks.

---

### Post by katarot on 2006-03-16
i have got a broadcom they are really annoying i cant seem to get mines to work with ubuntu 
but other people have had done it so it is possible
dapper has the drive for it but im not upgradeing until it is stable

---

### Post by Bagnaj97 on 2006-03-17
I have a broadcom chipset and it's working flawlessly using ndiswrapper. Have a look at [https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29)

---

### Post by Papa-san on 2006-03-17
[QUOTE=_SteveM]Hi, 

Im wanting to install ubuntu on my laptop, however to get on the internet my laptop connects to my wireless router. 

I was wondering if anyone has a Wireless Broadcom device and has gotten it to work within ubuntu?

If the answer is yes then i'll be switching asap :-D 

Thanks.[/QUOTE]
I am currently fighting with that particular problem, and have been for a week now... I have gotten closer to a solution, but still need a cat5 to go thru ethernet card. Wireless doesn't work. Any of the people who might help will to know which card you have and any info you can dig up on it. I will say that you need to get the driver  .inf and .sys files saved to your desktop!;)

---

### Post by LaBOOdha on 2006-03-18
i have a gateway tablet which I believe uses a Intel pro wireless 2200 b/g 
had to make sure that card was turned on with fn f2 keys in dual xp mode
then had to reinstall Ubuntu this time while making sure my card was on and able to show that it was connecting while installing.
then it somehow worked. NewB me couldn't figure out how to recognize card without  reinstalling.
could this help? didn't try this trick with live DVD though.

---

### Post by stupidel on 2006-03-18
Hi,

I went to the ndiswrapper website listed here and am installing on a amd64 version of ubuntu.  I was able to get as far as the "make deb" line, how do you "make deb"?  is this a command? a file? a directory? what am i suposed to do and with what?  any help here would greatly be apreciated, i feel i am very close to getting my wireless drivers working but i'm stlled at the moment.

Thanks again for your help.

---

### Post by Bagnaj97 on 2006-03-18
stupidel what version of ubuntu are you using? I'm using dapper on amd64 and ndiswrapper worked right away, I'm not sure about breezy though. Don't forget that when you get ndiswrapper installed you need a 64bit windows driver and not 32bit. You can get the 64bit broadcom drivers here (top download) [http://www.linuxant.com/driverloader/drivers.php](http://www.linuxant.com/driverloader/drivers.php)

---

