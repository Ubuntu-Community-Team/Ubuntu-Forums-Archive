---
title: "HELP! The network settings manual configuration panel freezes all the time."
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by idefixuk on 2008-03-24
My laptop is a Toshiba Portege 500, and I have Ubuntu 7.10 installed.
The The network settings manual configuration panel freezes all the time and I cannot get online even if the icon shows that I am connected at a good speed. At the moment I am online with another laptop with Windows XP installed. Where I live the internet connection sometimes fails for weeks. Yesterday and today it has been working. Yesterday evening I turned on the Portege and suddenly I was connected with the internal wireless (it had stopped working in the last two months and I needed an external wireless device) and I could browse the internet. This morning I turned the laptop on and, while the icon shows that I am connected to the same broadband at a good speed, I cannot get online or download email. Since October  I have been struggling  to get online with Linux and every time there is a different problem. I also bought a HUAWEI E220 USB modem that works with the 3.com broadband, it worked on the laptop of a friend who has  Xandros installed, it works with Windows, but not on Ubuntu. I followed several instructions on the Ubuntu Forum but without luck. I am not familiar with the terminal, although I am trying to learn) but the instructions are too complicated. I am not completely unfamiliar with programming. I have a BTEC in Computer Studies (it didn’t teach me much!), I know well HTML and I am familiar with PHP and MySql and built several websites but I cannot sort out my problems with Ubuntu that keep multiplying. I am now involved in a new project and, if I don’t sort out my Internet connection by the end of the week, I will be forced to re-install Windows on the Protege.

---

### Post by nitro_n2o on 2008-03-26
I'm not sure why you need manual configurations but you can edit your manual configurations using the terminal which is way easier than any gui 

go edit this file using your favorite editor (i use vim) you may want to use a gui editor like gedit so run the terminal and type this 

```
sudo gedit /etc/network/interfaces
```

the default file should have the word auto perpended to your interface name to make it manual you need to comment the interface you are using and add new config 

for example 
comment auto eth1 
like this 
# auto eth1 

then look here to see an example of static ip address entered manually in the config file, you'll need to change ip address according to your needs 
[http://byeworld.blogspot.com/2008/01/static-ip-address-in-linux.html](http://byeworld.blogspot.com/2008/01/static-ip-address-in-linux.html)

hope that help!

---

