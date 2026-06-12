---
title: "Can't load mozilla.com or ubuntu.com and other sites as well"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by Teclas5 on 2007-03-17
Hello all, new to linux so forgive a complete noob. Using firefox i can load most web pages but some like mozilla or ubuntu (and some others as well) time out. I tried the ipv6 thing by changing the value to true but still the same problem. I also tried turning off java and javascript along with all extensions and that didn't work either. Any ideas would be much appreciated.

---

### Post by h0ax on 2007-03-17
Hey there -

It would be good if we could get a little more information.
There are just a couple sites that don't work?
You have internet access?
Can you ping the sites that don't load?
(open a terminal type ping [www.mozilla.com](www.mozilla.com)) or others

--h0ax

---

### Post by Teclas5 on 2007-03-17
Sorry for insufficient info. No, several websites wont load (e.g. guitarsalon.com cariboucoffee.com etc.) i do have internet access as i am able to surf most anywhere just that those sites listed and others wont load. As for trying to ping the sites, i tried and it just shows this : icmp_seq=486 Packet filtered, and just keeps doing it over and over in ascending manner. Is that what it is supposed to do?

---

### Post by h0ax on 2007-03-18
Packet filtered ... hmm
Do you have a software/hardware firewall running?

---

### Post by Teclas5 on 2007-03-18
I'm not really sure if i have a firewall or not since i honestly don't know where to check. Is a firewall on by default when you first install ubuntu?

---

### Post by h0ax on 2007-03-18
It would appear that you have a firewall on blocking some addresses.  That's all I can think of off top of my head.
If you selected "security packages" or something - or maybe it is on the default install, I forget.

Run sudo iptables -L 
Any rules setup?

---

### Post by Teclas5 on 2007-03-18
I've tried looking everywhere on my settings to see if i have a firewall and i can't seem to find it. Can anyone show me how? I'm using kubuntu and still trying to get the hang of linux and (k)ubuntu. Many thanks.

---

### Post by Teclas5 on 2007-03-18
I tried a clean install of ubuntu and i still can't see mozilla.com, ubuntu.com and some other websites yet i can surf most. I tried running sudo iptables -L and i got

ernesto@ernesto-desktop:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination     



Can anyone make sense of this?

---

### Post by matchstich on 2007-03-23
> **Teclas5 said:**
> Sorry for insufficient info. No, several websites wont load (e.g. guitarsalon.com cariboucoffee.com etc.) i do have internet access as i am able to surf most anywhere just that those sites listed and others wont load. As for trying to ping the sites, i tried and it just shows this : icmp_seq=486 Packet filtered, and just keeps doing it over and over in ascending manner. Is that what it is supposed to do?

i went to caribou coffee and they say that unless one is using windows and IE, plus be on a high speed internet connection,
the site will not work. this is what i got from caribou coffee

Unsupported Web Browser or Operating System
To ensure all functions of the Caribou Coffee application perform correctly, you may not apply online using an unsupported Web browser or Operating System. You may not proceed with this application unless you use one of the Web browsers and/or Operating Systems listed below.
You must also have JavaScript enabled and an Internet connection at 56 kbps or higher. For more information on enabling JavaScript, see your browser’s Help.
Supported Web Browsers:

* Microsoft Internet Explorer 5.x
* Microsoft Internet Explorer 6.x (Click here to download the latest IE browser)
* Netscape Navigator 7.x (Click here to download the latest Netscape browser)


Please note that “beta” versions of web browsers are not supported. If you are an AOL user, please complete your application with an alternate supported browser after you have opened your AOL network connection.


Supported Operating Systems:

* Windows 98
* Windows 2000
* Windows XP

---

