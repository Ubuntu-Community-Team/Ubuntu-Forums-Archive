---
title: "Problem with connecting to Windows VPN (pptp)"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by cursebg on 2007-04-04
so i found some threads about that problem and a howto but there always is involved having an internet connection. in my case i want to connect through VPN to my server so i can have internet access. and that's a problem. if someone could tell me what to download throgh windows i'd be very very thankful  :) :KS

---

### Post by Skrynesaver on 2007-04-04
What happens when you start you Ubuntu box on the LAN?
Do you get handed a DHCP address?

---

### Post by cursebg on 2007-04-04
> **Skrynesaver said:**
> What happens when you start you Ubuntu box on the LAN?
Do you get handed a DHCP address?

dunno, i'll check

---

### Post by cursebg on 2007-04-04
no i don't

---

### Post by cursebg on 2007-04-04
seems like i'll have to deal with it by myself 
thanks anyway

---

### Post by Skrynesaver on 2007-04-04
Sorry, sometimes I have to go and earn a crust ;) what you need is the pptp client, instructions are available here
[http://pptpclient.sourceforge.net/howto-ubuntu.phtml](http://pptpclient.sourceforge.net/howto-ubuntu.phtml)
hope that helps

---

### Post by cursebg on 2007-04-04
> **Skrynesaver said:**
> Sorry, sometimes I have to go and earn a crust ;) what you need is the pptp client, instructions are available here
[http://pptpclient.sourceforge.net/howto-ubuntu.phtml](http://pptpclient.sourceforge.net/howto-ubuntu.phtml)
hope that helps
thanks man!

---

### Post by cursebg on 2007-04-04
> **cursebg said:**
> thanks man!
ops this does not work again... this requires internet access... i need the VPN to obtain internet access
someone pls just tell me what should i download via Windows and what to do with it PLS!!!

---

### Post by cursebg on 2007-04-04
can't anyone help me??? :( :( :( :( :(

---

### Post by Skrynesaver on 2007-04-05
In Windows download the rpm package from here (select the apropriate package for your architecture i have assumed i386) [http://sourceforge.net/project/showfiles.php?group_id=33063](http://sourceforge.net/project/showfiles.php?group_id=33063)
copy over to your debian installation and convert to the debian package format using alien
```
alien -d pptp-1.7.1-3.i386.rpm
```
you should now have a file called pptp-1.7.1-3.i386.deb to install the package file directly do
```
dpkg -i pptp-1.7.1-3.i386.deb
```

---

### Post by cursebg on 2007-04-07
thanks man! i'll write as soon as i log in from Ubuntu!

---

