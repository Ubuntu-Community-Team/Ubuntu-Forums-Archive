---
title: "Mac to ubuntu VNC"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by sdubois92 on 2006-10-18
I have a macbook and a ubuntu PC. I take my laptop everywhere I go and a lot of the tim i would like to show off ubuntu to people, work on Open office documents and just plain use my ubuntu box from my mac. I got chicken of the VNC and OSX VNC on the mac. How should I go about cofiguring my PC so that I can connect to it over the Wireless Lan in our house and over the internet.

thanks everyone

---

### Post by jordanmthomas on 2006-10-18
System --> Preferences --> Remote Desktop
and turn it on.

If you have a router at home you will need to make sure it forwards port 5900 to your computer.

(Not sure on the port, maybe 5800)

---

### Post by sdubois92 on 2006-10-18
let me explain myself a little more. I have a Linksys Wireless G router. How do i connect to my ubuntu box from my mac over the internet and over the wireless lan.

---

### Post by jordanmthomas on 2006-10-18
On your Ubuntu PC, type this in a terminal to find your IP:
```
ifconfig
```
Since you have a linksys, it will most likely be 192.168.1.xxx

While on your home network, open a web browser and go to 
[http://192.168.1.1](http://192.168.1.1)
log in

Find the port forwarding section and forward port 5900 to your Ubuntu PC.
I'm not sure how to use your particular vnc program, but you should be able to connect after that by using your IP while on the local network.

Use your router's IP when you are at work or wherever.
ie.  68.123.123.123:5900

---

### Post by sdubois92 on 2006-10-18
Attached is a screenshot of what i think is the port fowarding area. just wondering what exactly i should put in.

---

### Post by jordanmthomas on 2006-10-18
That is the right screen.
In the first line, put 
START 5900      END 5900     IP ADDRESS  (ubuntu's IP)       Enabled?  CHECKED

and save the settings

---

### Post by sdubois92 on 2006-10-18
thanks i got it working! But there is about 10-20 seconds of lag. any suggestions

---

### Post by jordanmthomas on 2006-10-18
Well, it would kind of undo everything you've done here, but I hear good things about freeNX.
VNC has always been slow for me too.  There also may be better VNC servers than the default Gnome one, but I'm not sure.

Also, is this lag over the Internet or over the local network?  There shouldn't be 10-20 second lags on a home network.

---

### Post by sdubois92 on 2006-10-18
this is over lan and im only 20 feet from the router. it does get much faster some times. now how would i connect over the internet if i was away somewhere?

---

### Post by jordanmthomas on 2006-10-18
You would need to know the router's IP.  Usually, it is somewhere close to yours.  

[http://www.whatismyip.com](http://www.whatismyip.com)  and add or subtract one or two from the last number and you will usually get the right one.

I'm not near my router now, (at school), but if you look in its settings it very well may tell you its IP there.

---

### Post by ZiRo on 2008-03-22
I had this problem with Chicken of the VNC on Leopard 10.5.1

I tried another VNC client (JollysFastVNC) and it worked flawlessly.

---

