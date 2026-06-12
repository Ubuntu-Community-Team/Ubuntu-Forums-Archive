---
title: "Problems with Java"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by drascus on 2007-06-27
I just got a new error message involving Java. It has worked in the past but then the other day a strange error message popped up. This occurs with some club pogo Games. Here is a screen shot of the desktop with the error message.

---

### Post by Seisen on 2007-06-27
What version of Java are you using?

```
java -version
``` in the terminal

---

### Post by drascus on 2007-06-27
Info from terminal:

java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)

---

### Post by Seisen on 2007-06-27
Maybe if you upgrade your Java it will work. 

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

and then 

```
sudo update-alternatives --config java
``` the select the newest version.

---

### Post by drascus on 2007-06-27
Ok now I get past the error window but then I am told I don't have enough memory which doesn't make any sense to me.

---

### Post by Seisen on 2007-06-27
Can you post the error message?

---

### Post by drascus on 2007-06-27
here you go

---

### Post by Seisen on 2007-06-27
Here is what I found on their website. 

[http://eapogo.custhelp.com/cgi-bin/eapogo.cfg/php/enduser/std_adp.php?p_faqid=1438&p_created=995506659&p_sid=fHZ8hcFi&p_lva=9564&p_sp=cF9zcmNoPSZwX3NvcnRfYnk9JnBfZ3JpZHNvcnQ9JnBfcm93X2NudD0yMTUmcF9wcm9kcz0mcF9jYXRzPSZwX3B2PSZwX2N2PSZwX3NlYXJjaF90eXBlPWFuc3dlcnMuc2VhcmNoX25sJnBfcGFnZT0xJnBfc2VhcmNoX3RleHQ9bm90IGVub3VnaCBtZW1vcnkgYXZhaWxhYmxl&p_li=&p_topview=1]("http://eapogo.custhelp.com/cgi-bin/eapogo.cfg/php/enduser/std_adp.php?p_faqid=1438&p_created=995506659&p_sid=fHZ8hcFi&p_lva=9564&p_sp=cF9zcmNoPSZwX3NvcnRfYnk9JnBfZ3JpZHNvcnQ9JnBfcm93X2NudD0yMTUmcF9wcm9kcz0mcF9jYXRzPSZwX3B2PSZwX2N2PSZwX3NlYXJjaF90eXBlPWFuc3dlcnMuc2VhcmNoX25sJnBfcGFnZT0xJnBfc2VhcmNoX3RleHQ9bm90IGVub3VnaCBtZW1vcnkgYXZhaWxhYmxl&p_li=&p_topview=1")

How much memory do you have and what other applications are running besides firefox?

---

### Post by drascus on 2007-06-27
right now I have 947.2 MB according to the system monitor and I am using about 250 to 300 MB of that. There are no other programs running accept what would normally be running in the background.

---

### Post by Seisen on 2007-06-27
I would say it is something wrong with either your version of Java or their servers than.

---

### Post by drascus on 2007-06-27
OK thank you for all the help I will take it from here.

---

