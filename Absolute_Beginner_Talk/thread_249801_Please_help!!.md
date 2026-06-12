---
title: "Please help!!"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by Norfolk 'n' Good on 2006-09-03
Hi

Each time I log on and want to connect to the internet I have to go through the following ritual...

>System
>Administration
>Networking
>Enter Password
>Highlight Ethernet connection
>Select Properties
>Configuration
>select Static IP adress from drop-down menu
>Configuration
>reselect DHCP
>Okay everything
>Connect to internet

As you might imagin, it's a pain!  Could someone please advise me (in ladybird language) how I might configure something or other to get round all this nonsense.

Thank you.

---

### Post by bodhi.zazen on 2006-09-03
Edit /etc/network/interfaces.

In a terminal type
```
sudo nano /etc/network/interfaces
```

Edit or add this line (assuming one network card)
```
# The primary network interface
auto eth0
iface eth0 inet dhcp
```

to exit nano type Ctrl-X, type "Y" to save your edit.

---

### Post by Norfolk 'n' Good on 2006-09-03
:D WOW!  It worked. A very quick response too. I spent ages trying to work this out. 

Thank you very very much  

Kind regards


Mark

---

