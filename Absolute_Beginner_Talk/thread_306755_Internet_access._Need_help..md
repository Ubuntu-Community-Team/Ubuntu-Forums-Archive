---
title: "Internet access. Need help."
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by klittzzer on 2006-11-25
I recently partitioned my hard drive in order to install Ubuntu alongside Windows on my laptop. I managed to perform the above tasks at the first attempt. I cannot, however, log on to the internet via my ISP whilst running Ubuntu. I have followed these:

[https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm](https://help.ubuntu.com/community/UsbAdslModem/ueagle-atm)

[http://ubuntuforums.org/showthread.php?t=201127&highlight=sagem](http://ubuntuforums.org/showthread.php?t=201127&highlight=sagem)

to the letter yet have had no sign of being able to connect. I think I have managed to correctly install the drivers and firmware that I downloaded from:

[http://download.gna.org/ueagleatm/ueagle-atm-1.3.tar.gz](http://download.gna.org/ueagleatm/ueagle-atm-1.3.tar.gz)
[http://eagle-usb.org/ueagle-atm/non-free/](http://eagle-usb.org/ueagle-atm/non-free/)

I dunno? If anyone can point me in the right direction I would appreciate it. Please don't assume I am able to write code cos I can't.

Where can I enter my ISP details on Ubuntu?
Like I said, I have followed those instructions to the letter but never seem to arrive at the same place that the tutorials deem I should. 

My ISP is Tiscali.co.uk
Modem is Sagem Fast 800

Again, help will be most welcome. I would love to be able to ditch windows but my experience of Ubuntu has hitherto been pretty dissapointing purely because of the fact that I have spent around 12 hours tring to get an internet connection. Both of the lights are on on my modem yet when I enter the command which is supposed to cause them to flash then rest full on doesn't induce the flash.

Please please help me out.
Thanks
Klittzzer

---

### Post by Geebird on 2006-11-27
Klittzzer
I also tried all the links and followed them to the letter, my finger bleed with all the typing, but I had no luck either...
That is until today. I re-read all the postings and everyone said try an ethernet modem.  So this morning I went and got one. 

[http://www.novatech.co.uk:80/novatech/specpage.html?LIN-ADSL2M](http://www.novatech.co.uk:80/novatech/specpage.html?LIN-ADSL2M)

It works like a charm. I wish I'd got one a week ago! 
Well worth 18 quid. (They were a lot more on a well know auction site)
So my advise is splash out and get one ...it'll save a lot of head scratching and sleepless nights. Best of luck.

---

### Post by apral on 2006-11-28
I had the same problems!If you have the dns & the static IP address of your ISP(if not call them & ask nicely) then click system(top left corner),then down to administration,then networking & click.You should have a listing -eth0 - that is active.Click on it so it changes colour then click properties(on the right)..Static IP address entries only(only way I could get it working).Make sure it is enabled.Click OK.Make sure that dns only has the address of your ISP.This is what I needed to make the internet work.Best of luck & ask for more if needed.:)

---

### Post by apral on 2006-11-28
Forgot to mention that it was done with a dlink router hooked up to USB so it is possible.:)

---

