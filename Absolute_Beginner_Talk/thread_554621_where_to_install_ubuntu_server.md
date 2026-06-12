---
title: "where to install ubuntu server"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by Graham Power on 2007-09-19
good  day 
 I have a network of 7 computers mix windows and ubuntu some on lan some wireless ,2x pda's and 3x psp2 .1x wireless router with 4 lan ports and 1x adsl modem .
this network is mainly used for gaming,email,video streaming,music streaming,wed browsing and network file shearing .I want to install a ubuntu server for storage of large shared files,printer sharing,control of Internet traffic for each computer and in the future have it share some files to the web 
Now for my questions 
1. Where do I install the server ? Between the adsl modem and the wireless router , on the lan side of the router or by wireless ( my guess is between modem and router )
2. Can anyone be able to give me a good link to setup this server as above 

Thank all ubuntu/linux people good work

---

### Post by stalker145 on 2007-09-19
> **Graham Power said:**
> 1. Where do I install the server ? Between the adsl modem and the wireless router , on the lan side of the router or by wireless ( my guess is between modem and router )
2. Can anyone be able to give me a good link to setup this server as above

1. You can set up your server in either location. It is much simpler, and a bit safer, to set it up on the LAN side, though - that is after your router and on your network. And for fastest speeds, keep your server wired.

2. [Here's a good place to start]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06"). The setup is for Dapper and may not have everything you need, but I'm sure HowToForge will have the answer... somewhere.

Check back if there are any more questions.

---

### Post by Jimmyfj on 2007-09-19
I'd suggest that you install the server behind your router. If you want to use the server for any private, or corporate files you do not want to expose the server to the internet.

---

### Post by Graham Power on 2007-09-19
thanks for both of your help just  question
If I put the server on the lan side how does it control the internet access of the other computers eg internet bandwith usage per computer
thanks again

---

### Post by stalker145 on 2007-09-19
> **Graham Power said:**
> thanks for both of your help just  question
If I put the server on the lan side how does it control the internet access of the other computers eg internet bandwith usage per computer
thanks again

Ahhh, now it gets more complicated. If you wish to actually control the access by other computers, I believe you will be wanting to set this up as a firewall/DHCP/proxy server (never done it, hence, I *believe*). I'm pretty sure, though, that you will need to have two NIC's in your server - one attached to your LAN and the other to the WAN/MODEM.

What comes to my mind is this:

```
LAN --> Server --> MODEM
    |    |
Router __|
```

Man, that's an ugly diagram - hopefully it gets the thought across.

---

