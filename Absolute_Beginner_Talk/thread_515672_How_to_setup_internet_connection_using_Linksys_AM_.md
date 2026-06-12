---
title: "How to setup internet connection using Linksys AM 300"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by gaptekboy on 2007-08-02
Dear All,

Currently I'm using Ubuntu 7.04 and I'm trying to connect to internet with [Linksys AM 300](http://www-id.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=ID%2FLayout&cid=1169672136749&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=3674984869B02), but I can't seem to get the modem to work with Ubuntu. The Setup CD only provide installation program for Windows. Please tell me to do it in step-by-step, I'm totally newbie here :???:

Thanks a lot before...

---

### Post by milosz.galazka on 2007-08-02
Hello,

Can you connect to it via ethernet port?

The default ip for this modem is 192.168.1.1 so you can access it using browser.

---

### Post by gaptekboy on 2007-08-02
Well, that's another problem...I connect it with USB. Is it better to connect with ethernet rather than USB? Because I've tested, it works ok with Windows.

Thanks for the reply...

---

### Post by gaptekboy on 2007-08-02
PROBLEM SOLVED!!!

I just follow your direction to go to 192.168.1.1 and see every setting has already been setup before by Windows. Then, from Network Connection Setup in Ubuntu, I just put 192.168.1.1 in the DNS Server and put "Automatic Configuration (DHCP)" in eth0 Interface Settings.

It works even better & faster in Ubuntu... :popcorn:

Thanks milosz.galazka :)

Wow, you're from Poland...hi from me in Indonesia. I thought we almost have the same national flag but ours turned upside down... :lolflag:

---

