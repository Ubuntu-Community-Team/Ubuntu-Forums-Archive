---
title: "Help needed with wireless connection,"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by Error47 on 2007-06-04
I don't know if this topic has already been started. I am trying to figure out how to get my wireless internet to work.  I am using 7.04. Is there any way I can search for open wireless networks. I know my network name because I am home now, I typed that in, along with my password, and it could not connect. It does not give me any error messages or anything, it just stops trying to connect. I am not sure what wireless card I have, It came built in with my presario 3000 laptop. I think it is realtek or something like that. Also If I am not home, and I do not know the network name, I would like to know how to search for wireless networks near me.  Does anyone have a guide or something that could help me with this problem?

---

### Post by daimaru on 2007-06-04
just installed 7.04 on my toshiba p100-something, got no sound :) but wireless works. only have to click the connection button in the menu and i see all the available wireless networks. chooose the on i want select wep or wap , enter pass ... works.
is your wireless card recognized by ubuntu ? does it show up in iwconfig?

---

### Post by 00ber n00b on 2007-06-05
im having the same problem.  my friend can get a connection sitting next to me and i dont see any wireless networks.  i have an internal broadcom 4306,  hp dv 1000

---

### Post by jimrz on 2007-06-05
> **00ber n00b said:**
> im having the same problem.  my friend can get a connection sitting next to me and i dont see any wireless networks.  i have an internal broadcom 4306,  hp dv 1000

there a tons of posts on these forums on how to get broadcom cards working. just run a forum search for "broadcom 4306" and you should findhow others were able to solve the issue. I don't have any experience of this, since both of laptops have other wifi chipsets, but have seen many of these posts.

search is your friend.

EDIT: duh...just saw this is your 1st post...welcome aboard. try this [[COLOR="Sienna"]**link**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+4306") for info on your chipset.

---

### Post by Inxsible on 2007-06-05
As for searching the wireless networks around you, make sure you are not on a wired connection. then click the network icon near the system clock in the top right corner of the screen. you will see a bunch of networks that are around you.

---

### Post by Error47 on 2007-06-06
I don't see these things you are talking about. I do not know what wireless network card I have. 

Someone mentioned "iwconfig"

This is what I get from that...
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.442 GHz  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I have a compaq presario 3000, and I can't find it on the compaq website either. It is either that broadcom , or some other thing I saw called realtek, although that may be for the sound or someething, I don't even know.

---

### Post by Error47 on 2007-06-06
Nevermind, realtek is my soundcard. Can anyone tell me what the code I put above means, I can't get my wireless to work..

---

### Post by Error47 on 2007-06-11
I still don't know what to do. I can't find any info on my Presario 3000. One of my friends told me about a program called ndwrapper . Where you can install windows drivers on linux. I lost the instructions he gave me, so I would like to know how to use this program if it can work in ubuntu.

---

### Post by jimrz on 2007-06-11
> **Error47 said:**
> I don't see these things you are talking about. I do not know what wireless network card I have. 

Someone mentioned "iwconfig"

This is what I get from that...
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.442 GHz  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I have a compaq presario 3000, and I can't find it on the compaq website either. It is either that broadcom , or some other thing I saw called realtek, although that may be for the sound or someething, I don't even know.

looks like you, also, have broadcom 4306 card. see the link I put in response to 00ber n00b earlier in this thread regarding the same chipset

---

### Post by nbayiha on 2007-06-12
Actually i have the same problem , when i put iwconfig , i have
Code:

lo        no wireless extensions.

eth0      no wireless extensions.

and when i open my
/etc/network/interfaces i have this
Code:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

what am i suppose to modify or to add to this , cause there is a lot of thread about making my wirelless card work but the problem is i can't follow them if my system don't even see my wireless card.

And help is really needed.

PS; actually i'm using hp dv6040us and my wireless is Broadcom 4311 but like my wireless card isn't seen

---

### Post by nbayiha on 2007-06-12
Actually i have the same problem , when i put iwconfig , i have
```


lo        no wireless extensions.

eth0      no wireless extensions.

```

and when i open my
/etc/network/interfaces i have this
```


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

```

what am i suppose to modify or to add to this , cause there is a lot of thread about making my wirelless card work but the problem is i can't follow them if my system don't even see my wireless card.

And help is really needed.

PS; actually i'm using hp dv6040us and my wireless is Broadcom 4311 but like my wireless card isn't seen

---

