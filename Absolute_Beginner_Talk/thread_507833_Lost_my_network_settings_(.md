---
title: "Lost my network settings :("
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by ROUBOS on 2007-07-23
Hi,
I had my Ubuntu feisty system running at home fine on the  US.Robotics Router.
Now I moved it to work which has a SAGEM Router and I cannot get internet on it.

Internet is normally just auto detected and works fine as long as the cable is plugged in.

Do not know what's going on. Any help will be greatly appreciated.

Looking for a network setup wizard with no luck :(

---

### Post by dca on 2007-07-23
Sounds to me like at home, your router issues IP addresses (dynamic) and at work, you need to have a static IP address that generally your admin issues.  In other words, the settings in network manager need to be config manually, not set to automatic...

---

### Post by ROUBOS on 2007-07-23
yes.
I do setup the setting to

IP:                        192.168.2.10
                             255.255.255.0
default gateway: 192.18.2.1


no luck though

---

### Post by Somarius on 2007-07-23
> **ROUBOS said:**
> Hi,
I had my Ubuntu feisty system running at home fine on the  US.Robotics Router.
Now I moved it to work which has a SAGEM Router and I cannot get internet on it.

Internet is normally just auto detected and works fine as long as the cable is plugged in.

Do not know what's going on. Any help will be greatly appreciated.

Looking for a network setup wizard with no luck :(
Hmm.. have you checked if your SAGEM router authentication information in your router's GUI its equal your US.Robotics Route?? is both of your routers on bridge mode?? need more details plz

---

### Post by ROUBOS on 2007-07-23
The only difference is that the US.Robotics had  an IP of 192.168.1.1
and the SAGEM has 192.168.2.1

Don't know what else to look for

---

### Post by dca on 2007-07-23
What about DNS settings?

---

### Post by Somarius on 2007-07-23
do basic troubleshooting...check cables and filters... SAGEM isnt prob authenticating because of that...access your SAGEM's gui by entering to you router's default gateway IP address on Firefox and check your authentication info... 

can u post your LED status??
is your router 
SAGEM F@st&#8482; 1500 ADSL router?
if so check[SAGEM F@st&#8482; 1500 ADSL router]("http://php.internet.is/veirur/ADSL/Sagem(Tv%20over%20adsl)/Fra%20framleidanda/288053220-03_SAGEM_Fast1500-en.pdf")

---

### Post by ROUBOS on 2007-07-23
This SAGEM is crap.
Will get a USRobotics. 

Don't know sorry guys. I've been so busy working since 8am and it's now 10pm. I can't stay here no more. Will have to look at it tomorrow. Sorry.

But I did check my cable on the laptop I'm writing to you from and it's working fine.The light on my Network card on the Ubuntu machine is on when I plug the cable in as well.

I do access the router (not from the Ubuntu box) by typing 192.168.2.1
Do I have to enter Public IP and DNS info? I did not have to do it for my USRobotics router at home.

Anyway, thanks for your help but I'm tired right now and just need to go home and have a  shower.

I'll look into it tomorrow.

---

### Post by ROUBOS on 2007-07-23
yeah its a fast 1500 WG router....

CRAP... .US.Robotics is much better in my opinion. Better interface and all. Look at the Sagem mobile phones for example... horrible

---

