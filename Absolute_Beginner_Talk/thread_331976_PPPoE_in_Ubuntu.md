---
title: "PPPoE in Ubuntu"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by pmcastillo on 2007-01-05
I have:

* ZTE ZXDSL 831 Series ADSL Modem
* C-NET PRO200 Ethernet Card
* Ubuntu 6.06

I tried to follow the guide on How to configure the PPPoE 
I run, "sudo pppoeconf", But I gave me an error:

```
Sorry, I scanned 1 interface, but the Access Concentrator of your provider did not responed. Please check your network and modem cables. Another reason for the scan failure may also be another running pppoe process which controls the modem.
```

Then tried it to run again, but this time, I picked no, and it gave me another error message:

```
modconf: command not found
```

I got a Linux Driver for my Ethernet Card (I don't know if I have a Linux Driver for my ADSL Modem), but I don't know how to install it.

Can someone enlighten me?

---

### Post by pmcastillo on 2007-01-06
I got two screenshots here.. maybe this could help

[[IMG]http://img72.imageshack.us/img72/1621/screenshot9dr9.png[/IMG]](http://img72.imageshack.us/my.php?image=screenshot9dr9.png)

[[IMG]http://img154.imageshack.us/img154/4707/screenshot6ys9.png[/IMG]](http://img154.imageshack.us/my.php?image=screenshot6ys9.png)

What's the problem with here? ](*,)

---

### Post by swatkatzin on 2007-01-31
Guys

am having exactly the same problem. Mine is a Huawei MT800 ADSL modem.

The screen shots are the same in my system too. i mangaed to isntall rp-pppoe and enter my id and password but the connection gets timed out and never connects.

Am sure most of you know how  to fix this...i have searched extensively in this forum and have got thus far....pls help me configure internet

---

### Post by pmcastillo on 2007-03-18
Any answers guys?

---

### Post by agredam on 2007-05-27
I have **exactly **the same problem. Please help us!!!

---

### Post by pmcastillo on 2007-05-27
Wow! Just 7 more months I this thread will have it's 1 Year Anniversary!!! LOL!

---

### Post by Licurgo on 2007-05-28
In a terminal window What is the output of::p?
$ ipconfig

---

### Post by Apipote on 2007-06-13
Same for me. Ubuntu experts
Help us please

---

### Post by terabite on 2007-06-15
First of all, do your ISPs use PPPOE???
To check this, contact ur ISP.
Or, in windows, goto '**Network Connections**'
Arrange all connections by TYPE.
If ur connection uses pppoe, it would have type as 'WAN Miniport (PPPOE)'.

Also, send the output of:

```
ifconfig
```

---

### Post by terabite on 2007-06-15
I also recommend u try out Roaring Penguin PPPOE... It is a gui tool for pppoe connections.
[URL="http://www.roaringpenguin.com/en/penguin/openSourceProducts/rpPppoe"]
http://www.roaringpenguin.com/en/penguin/openSourceProducts/rpPppoe[/URL]

---

### Post by terabite on 2007-06-15
And im sorry for the late reply guys!
Happy ubuntuing! :)

---

### Post by L1Nux3R on 2007-06-18
btw i faced this problem and i searched alot for that and finally i got the solution as follows :


first open your browser and type your gateway ip like that 10.0.0.2 or 192.168.1.1 whatever it could be 


then after that go through the configuration and search for PPP section and then you will find a line below to check  your WAN configuration 

after clicking  that a window has some configuration to be entered like :

virtual circuit { enabled or disabled }

bridge           { enabled or disabled }

IGMP            { enabled or disabled } 


what we will be aware with the second item bridge. all what u will do is to enable it and below hit the submit button and save ur configuration on reboot after that ur connection will be lost 

then  run :

```
sudo pppoeconf 
```

and  go through  the pppoe operation and u will get it working 


note : if you want to restore your old configuration just press on the Reset button inside the Adsl modem and you will get ur old configuration again 

and sorry for my language as am not native !

---

### Post by pmcastillo on 2007-09-09
Guys, I've finally made it! On my almost 1st Year Anniversary (check my first post's date), I've finally made it! Ok, this is what I've remember what I did:

STEP 1: Download the Latest Ubuntu. (I've downloaded Ubuntu 7.04)
STEP 2: Configure first your "eth0", by giving its IP, Subnet Mask, Default Gateway.
STEP 3: On the "Terminal", type in, "sudo pppoeconf"
STEP 4: The program would detect your ADSL modem. 
STEP 5: As far as I remember, I keep on banging my ENTER KEY ^_^
STEP 6: Oops! DON'T FORGET TO TYPEIN YOUR USERNAME AND PASSWORD
STEP 7: Continue banging the ENTER KEY ^_^
STEP 8: There! You're connected!
STEP 9: To disconnect from the internet, type in "sudo poff dsl-provider"
STEP 10: To connect again to the internet, type in "sudo pon dsl-provider"
STEP 11: Give free beers to everyone for a job well done ^_^

**CONCLUSION:** Maybe it's the latest version of Ubuntu that made detecting my ADSL modem possible.

[CENTER][IMG]http://img179.imageshack.us/img179/209/screenshotih4.png[/IMG][/CENTER]

---

