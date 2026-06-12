---
title: "Network devices"
date: 2005-12-16
forum: Absolute Beginner Talk
---

### Post by leomps on 2005-12-16
Hi, I have instaled UBUNTU.Now it is saying no network devices installed,Can u help me how to instal ethernet and wireless.

---

### Post by alamba on 2005-12-16
What machine are you using? Model number? What manufacturer of ethernet?

Akshay

---

### Post by leomps on 2005-12-16
IM using Compaq presario 2500

---

### Post by alamba on 2005-12-16
Do have ubuntu installed now? Go to system>>admin>>networks...do you see your cards listed there?

Connect your ethernet cable and click on activate next to the entry for your ether card in the link above.

Then open a terminal screen and type ifconfig...post the result.

Akshay

---

### Post by leomps on 2005-12-16
[QUOTE=alamba]Do have ubuntu installed now? Go to system>>admin>>networks...do you see your cards listed there?

Connect your ethernet cable and click on activate next to the entry for your ether card in the link above.

Then open a terminal screen and type ifconfig...post the result.

Akshay[/QUOTE]

yes all my cards are listed there.
In terminal screen im able to see wlan0 with some more information.like link encapsulation : Ethernet then mac adreess and other things.But still it is showing no network devices available.

---

### Post by alamba on 2005-12-16
Then u're good to go buddy...just click on the activate link in system>>admin>>networking for the wireless or ether connection and as long as you have DHCP u're up...incase you don't have DHCP u'll need to put in the ip address, subnet, gateway, etc.

Akshay

---

### Post by leomps on 2005-12-16
[QUOTE=alamba]Then u're good to go buddy...just click on the activate link in system>>admin>>networking for the wireless or ether connection and as long as you have DHCP u're up...incase you don't have DHCP u'll need to put in the ip address, subnet, gateway, etc.

Akshay[/QUOTE

But still it is showing me the same.We are running DHCP here but it is not comming up.

---

### Post by alamba on 2005-12-16
Are you talking about the wireless or the ether connection? 
If its wireless:
Go back to system>>admin>networking
Click on the wireless link
Click on configure
Put in the WAP name and other details 
Click on activate
Run ifconfig on terminal screen

You should have an IP now...ping to the nearest router/switch/etc

Akshay

---

### Post by leomps on 2005-12-16
[QUOTE=alamba]Are you talking about the wireless or the ether connection? 
If its wireless:
Go back to system>>admin>networking
Click on the wireless link
Click on configure
Put in the WAP name and other details 
Click on activate
Run ifconfig on terminal screen

You should have an IP now...ping to the nearest router/switch/etc

Akshay[/QUOTE]


ifconfig is not showing me any IP.When i try to ping it says network unreachable.

---

### Post by alamba on 2005-12-16
Alright...lets start over. 

Are you talking about the wireless or the ether connection? 

Akshay

---

### Post by leomps on 2005-12-16
[QUOTE=alamba]Alright...lets start over. 

Are you talking about the wireless or the ether connection? 

Akshay[/QUOTE]

wireless...

---

### Post by alamba on 2005-12-16
ok...and u see it in the networking gui. Did you click on configure and put in the AP name and WEP encrytion key etc?

Akshay

---

### Post by leomps on 2005-12-16
[QUOTE=leomps]wireless...[/QUOTE]


Thx Akshay.Its working now....


Can i have ur yahoo id for more help...If u dont mind.

Manpreet Singh.

---

### Post by alamba on 2005-12-16
see the contact page on [www.lambaweb.com](www.lambaweb.com)

has all my contact points. feel free to shout out anytime.

what fixed it? what were you missing? its a good idea to always summarize the solution in the end for other's who have a similar problem.

Akshay

---

### Post by leomps on 2005-12-16
[QUOTE=alamba]see the contact page on [www.lambaweb.com](www.lambaweb.com)

has all my contact points. feel free to shout out anytime.

what fixed it? what were you missing? its a good idea to always summarize the solution in the end for other's who have a similar problem.

Akshay[/QUOTE]

There was some issue with my wireless settings.I was configuring wrong SSID.
Now it is working fine.

---

