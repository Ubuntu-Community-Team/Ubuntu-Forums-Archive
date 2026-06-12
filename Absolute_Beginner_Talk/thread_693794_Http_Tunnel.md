---
title: "Http Tunnel"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by faixan on 2008-02-11
Hi,
i'm using a university LAN, which blocks most of the media websites like youtube, stage6 etc, most of the media files and above all torrents and P2P.
i tried to install several http tunneling softwares using synaptics, i don't know whether they're installed or not 'cuase i didn't get any error message during or after installations, but i can't find any of them under any menus, 
any one please suggest any http tunneling app. for Ubuntu 7.10 Gust Gibbons.
also, can ,
htc 
be of any use, i tried to look in htc -help but i couldn't find what it was about...

thank you.

---

### Post by LowSky on 2008-02-11
So you want us to help you break your internet agreement with you university?

FYI: just type the name of the program that you installed  in a terminal window and it should just startup

---

### Post by dca on 2008-02-11
Put http tunneling software into google search and I'm sure out of the first ten would be the wiki which would include locations of where to get..
 
I don't recommend using this on school networks or a place where you work because something may gain access to your network through your computer which can be traced back to you...

---

### Post by faixan on 2008-02-11
i've already tried google, i installed httptunnel but it's not under any menu, and i don't think that there's any problem with breaking down the agreement if it doesn't allow me to download video lectures and tutorials regarding my studies...

---

### Post by jken146 on 2008-02-11
> **faixan said:**
> it's not under any menu.

Please read LowSky's post.

---

### Post by faixan on 2008-02-11
this is what i've just done....
sudo apt-get install httptunnel -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
httptunnel is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
still nothing in the menus... 
:(

---

### Post by LowSky on 2008-02-11
why are you typing the install command?
just type```
 httptunnel
```

it doenst have a GUI menu... you could always make your own its very simple

---

### Post by faixan on 2008-02-11
httptunnel
bash: httptunnel: command not found

this comes out :(

---

### Post by jken146 on 2008-02-11
Please post the output of ```
whereis httptunnel
```

---

### Post by Dr Small on 2008-02-11
Here's my type of tunneling:
[http://php.8ez.com/drsmall/blog/wp-content/bypassfirewall_sshtunnel.png](http://php.8ez.com/drsmall/blog/wp-content/bypassfirewall_sshtunnel.png)

But Tor can be used as a tunnel too:
[http://php.8ez.com/drsmall/blog/?p=155](http://php.8ez.com/drsmall/blog/?p=155)

---

### Post by faixan on 2008-02-11
:~$ whereis httptunnel
httptunnel:
:$

this is the output....

---

### Post by lespaul_rentals on 2008-02-11
It will probably have to be run as root.

I seriously doubt this will work; most HTTP tunneling software is for the server, so you install it on a computer outside the restricted proxy then tunnel through it.  There'd be no point in tunneling through your own connection, as you will still be behind the proxy.  I might be completely wrong, though.

---

### Post by LowSky on 2008-02-11
Dr. Small that is one messed up way to get into the internet from work. 


All I did was get real chummy with IT and ask for less restricted access...lol

faixan try this

[www.http-tunnel.com/html/support/overview.asp](www.http-tunnel.com/html/support/overview.asp)

[www.httptunnel.org](www.httptunnel.org)

---

### Post by Dr Small on 2008-02-11
> **LowSky said:**
> Dr. Small that is one messed up way to get into the internet from work. 


All I did was get real chummy with IT and ask for less restricted access...lol

faixan try this

[www.http-tunnel.com/html/support/overview.asp](www.http-tunnel.com/html/support/overview.asp)

[www.httptunnel.org](www.httptunnel.org)
Actually, that diagram is quite simple and "shows" the process of tunneling via SSH.

Dr Small

---

### Post by LowSky on 2008-02-11
> **Dr Small said:**
> Actually, that diagram is quite simple and "shows" the process of tunneling via SSH.

Dr Small

I meant, "messed up" from the ethical stand point as your diagram was quite simple to understand...LOL

Using your own computer to route your internet is very ingenious and cheeky at the same time, I had a friend that did that because his mom would restrict his access, so he would piggyback onto another friend's network , through the same method, so he could look at his unprivaleged material...

---

### Post by lespaul_rentals on 2008-02-11
> **LowSky said:**
> I meant, "messed up" from the ethical stand point as your diagram was quite simple to understand...LOL

How is that "messed up" ethically?

---

