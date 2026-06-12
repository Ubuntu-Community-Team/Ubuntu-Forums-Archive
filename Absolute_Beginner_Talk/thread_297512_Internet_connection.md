---
title: "Internet connection"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by iuliska on 2006-11-11
Hello,

I have just installed Ubuntu 6.06 on my computer. Everything works perfect except for ... my internet connection.I can't connect to the internet. Fortunatelly I also have windows xp installed on my computer so I can surf a little. On windows I have an ethernet cable connection. I tried to set my Ip with ifconfig but it still didn't work( ifconfig eth0 <IP> netmask<> up)I tried to ping [www.google.com](www.google.com) but it said (ping:unknown host [www.google.com](www.google.com)) so...:-k can anyone tell me what to do ???How can I connect to the internet?(Please try giving examples and presenting everything step by step...I am a beginner](*,) ) Thks a lot:-D

---

### Post by taurus on 2006-11-11
How do you connect your box to internet?  Do you connect it thru a router and is it a USB?  Need a little more about your network setup here.

---

### Post by podunk on 2006-11-11
This is sort of anj odd one - Ubuntu usually gets you on the internet through a ethernet card seamlessly.

Maybe you need to log into your router and enter your log on info (username for your IPS and password)? 

With my router I type in the IP of my router in a web browser in the form xxx.xxx.x.254. This is the same as default gateway address found in Networking.

---

### Post by iuliska on 2006-11-11
I connect through a router but it is not USB,it's normal cable like for the phone

---

### Post by iuliska on 2006-11-11
How do I log into my router...and how can i know my router?:mrgreen:

---

### Post by loclei on 2006-11-11
how to make 
```

ping google.com

```
give me a reply
i connect thru my ehter card to a proxy that looks like "ip: port"
thx

---

### Post by derrylynne on 2006-11-11
I have the same problem. I have tried to connect through the router. Works fine on windows as all the info is in the router - my isp - password etc. I wired it to the ethernet card and it does not work. I am also new to this so need step by step talk through

---

### Post by loclei on 2006-11-11
> **derrylynne said:**
> I have the same problem. I have tried to connect through the router. Works fine on windows as all the info is in the router - my isp - password etc. I wired it to the ethernet card and it does not work. I am also new to this so need step by step talk through
maybe you should look for ppoe setup

---

### Post by derrylynne on 2006-11-11
> **loclei said:**
> maybe you should look for ppoe setup

I tried that too. Neither did that work. It seems to be a common problem with people trying to come over to Lynux not being able to get an internet connection. They then go away. So Bill wins and once again Lynux loses possible converts...

---

### Post by podunk on 2006-11-11
To get to your router you may have to read the manual. :-) Or you could go to the website for the router company and try their support page.

One thing that might work is type
```
ifconfig
```

and you should get back something that looks like this:
inet addr:192.168.1.97  Bcast:192.168.1.255  Mask:255.255.255.0

Open a browser and try typing in the Bcast address numbers, be sure to include the periods. If you get a page not found change the last set of numbers to either 
.254
or
1
and see if you can get tot the log in page.

Another place to get help with this is to call your DSL provider - most of them have 24/7 support.

---

