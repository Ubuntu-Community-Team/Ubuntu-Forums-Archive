---
title: "Dial Up Network Connection"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by edsacavite on 2006-04-13
Hi Everyone,

I am new to Linux and Ubuntu, I've been using Windows all these years.

I received the free CD of Ubuntu 5.1 several months ago. The first time I tried it, it seems run slower than Windows so I did not push through switching it with Windows. I tried it again today and it still seems slow but my main concern now is that I can not establish a dial up connection to my ISP (internet service provider). I tried the Evolution Assistant but to no avail.

Will appreciate all help I can get. Thanks a lot.

Edsacavite

---

### Post by mandrakethepenguin on 2006-04-13
First of all, who is your ISP? And did you use the Live CD or the Install CD? Also, you would need a certain software called Gnome-PPP that you can obtain by using a terminal. To install it, go to **Applications -> Accessories -> Terminal** and type in ```
sudo apt-get install gnome-ppp
``` Enter your root password hit the letter Y when apt-get has loaded and it will install.  Gnome-PPP is a dialup manager for ubuntu and should help you configure your dial up connection.

---

### Post by towsonu2003 on 2006-04-13
if you are using an internal (built-in) modem, it might be a winmodem... can you see your modem in system>administration>networking? 

if it's not there, check out second link in my signature.

if it's there, check out the second link in my signature, only the part about wvdial. It's easy to setup and it gives some output so you'll know more or less why you can't connect.

---

### Post by brentroos on 2006-04-13
*

---

### Post by towsonu2003 on 2006-04-13
[QUOTE=brentroos]You're going to need an external serial modem. You can [buy one on Ebay]("http://search.ebay.com/search/search.dll?sofocus=bs&sbrftog=1&catref=C6&frpp=50&maxrecordsreturned=300&from=R10&satitle=external+serial+modem&sacat=-1%26catref%3DC6&bs=Search&fsop=1%26fsoo%3D1&coaction=compare&copagenum=1&coentrypage=search&fgtp=&sargn=-1%26saslc%3D2&sadis=200&fpos=ZIP%2FPostal&ftrt=1&ftrv=1&saprclo=&saprchi=") for very little $$. After that, install gnome-ppp and select the appropriate serial port (i.e. ttys0), and you should be good to go. 
[/QUOTE]
I'm not sure it's a good idea to tell someone who just started to try this to go buy something. I remember this from when I was too new. Whenever I asked for help with modem, someone came and suggested me to buy a serial modem. It kinda gets frustrating, when you are trying a free operating system. 

On the other hand, winmodem support in linux simply sucks (despite the efforts by linmodems.org people). so, catch 22... 

If you've got a winmodem in there, I would try to configure it. You'll get frustrated, but it's cheaper and you'll learn a couple of things (like being confortable with the command line etc)

now, I'm curious whether you've got a winmodem or not ;)

---

