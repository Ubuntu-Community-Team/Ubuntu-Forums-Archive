---
title: "internet connection"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by davyC on 2007-05-11
Would appreciate some help from any techies please. My existing internet connection is through a cable modem to my home PC and have always used Windows XP.as my OS. I've downloaded and installed Ubuntu on my PC. I now have the option of running either Windows XP or Ubuntu on start up. Both options load perfectly normally when selected.Windows XP acts perfectly normal when used, including internet access through mozilla firefox. What I can't seem to do is to connect to the internet through Ubuntu. Any Help please?

---

### Post by Bachstelze on 2007-05-11
How is your cable modem connected to your machine ?

---

### Post by davyC on 2007-05-11
ethernet cable

---

### Post by Bachstelze on 2007-05-11
Then it should be fairly easy. Do you know if you're using DHCP or not ?

---

### Post by davyC on 2007-05-11
Yes DHCP

---

### Post by Bachstelze on 2007-05-11
Then do 

```
sudo ifconfig -a
```

to find out what your Ethernet interface is and then do

```
sudo dhclient eth0
```

(remember to replace eth0 with the correct name if yours is different)

---

### Post by davyC on 2007-05-11
sorry to be a bit thick here but how do I do
Then do

Code:

sudo ifconfig -a

to find out what your Ethernet interface is and then do

Code:

sudo dhclient eth0

---

### Post by Dayylin on 2007-05-11
Bring up terminal and type the commands in there.

---

### Post by davyC on 2007-05-11
bring up terminal?

---

### Post by Bachstelze on 2007-05-11
[Where's the terminal ?](http://psychocats.net/ubuntu/terminal)

---

### Post by davyC on 2007-05-11
How do I know what the correct name is 

(remember to replace eth0 with the correct name if yours is different)

---

### Post by Bachstelze on 2007-05-11
```
sudo ifconfig -a
```

paste what you get, we'll tell you...

---

### Post by davyC on 2007-05-11
this is getting complicated - so many commands to remember - bearing in mind that i can't try any or them till i exit windows ( which is whatim using now)

---

