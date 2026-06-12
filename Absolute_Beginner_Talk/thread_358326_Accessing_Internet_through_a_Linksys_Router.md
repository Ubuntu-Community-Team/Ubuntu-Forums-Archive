---
title: "Accessing Internet through a Linksys Router"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by grs on 2007-02-10
Ok, just got the internet running fine on Xubuntu but I have to plug directly into the broadband modem. I would like to have it so that the PC plugs into my Linksys Router that then will allow my laptop acces the internet via wireless network card. I do have portfowarding setup on the router so I can use Bit Torrent on the laptop. Can someone explain the setup process of this for me. Thanks

---

### Post by bionnaki on 2007-02-10
you probably have to setup your wireless card first. what make/model do you have?

---

### Post by grs on 2007-02-10
The router is a Linksys WRT54G, I can't tell you the network card model, it's built into the mainboard, which is for an Intel P III processor. Is that any help? The Xubuntu desktop guide says for LAN I should have the connection settings at DHCP which it is.

---

### Post by %hMa@?b&lt;C on 2007-02-10
> **grs said:**
> The router is a Linksys WRT54G, I can't tell you the network card model, it's built into the mainboard, which is for an Intel P III processor. Is that any help? The Xubuntu desktop guide says for LAN I should have the connection settings at DHCP which it is.
what does 
lspci |grep Network 
give for an output

---

### Post by grs on 2007-02-10
lspci |grep Network

I don't know what that mean? How do I look it up?

---

### Post by Happy_Man on 2007-02-10
Go to your terminal (applications --> accessories --> terminal) and type:

```

lspci |grep Network

```

---

### Post by Skidpad on 2007-02-10
...be advised that you don't actually have to "type" commands that are posted in the forum, or elsewhere...you can copy & paste into the terminal...

(One little tidbit that new users may not realize yet)

---

### Post by nickoli_02 on 2007-02-10
I have the same model router. Are you trying to set up port forwarding so you can download torrents with the new PC or are you having difficulties with the router DHCPing with the new PC (ie it won't connect)?

---

### Post by grs on 2007-02-11
ok, I typed:-

lspci |grep Network

into the terminal and I got nothing, just a new prompt line appeared, I am new to Linux so if theres more I should type in relevent to my PC please explain.

As I was typing this I have been typing variations  of the line into the terminal, most did nothing, but now the internet appears to be working. I hate when that happens.


nickoli_02,

I already have port fowarding setup to use BitTorrent on a laptop running Win XP PRO (that runs fine), the desktop running Linux Xubuntu doesn't have BitTorrent loaded on to it, the problem is that it won't connect to the internet, I just thought the settings for portfowarding may be having an effect on the connecting.

---

### Post by nickoli_02 on 2007-02-11
Ah ok. Does your Xubuntu computer connect to the router? Try pinging the router IP. If that works try pinging google or something.

```
ping -c 10 <addr>
```

<addr> is the IP or address you want to ping. Your router IP is most likely 192.168.1.1, that's the default.

---

### Post by warlock_handler on 2007-02-21
> **nickoli_02 said:**
> Ah ok. Does your Xubuntu computer connect to the router? Try pinging the router IP. If that works try pinging google or something.

```
ping -c 10 <addr>
```

<addr> is the IP or address you want to ping. Your router IP is most likely 192.168.1.1, that's the default.

yes thats right just 10 mins back i configured my linksys router to connect to my uBuntu machine and also enable the wifi so my cousin can connect to the net with her win xp laptop using the same internet connection using my router's LAN...

192.168.1.1 is the default router address so for linksys you can use this in firefox and it will let you configure the router too.... so once you put all your ISP info etc you are set to go...

a small tip now since my ISP doesnt let me connect a router and to my net cable, I have also spoofed my MAC address while configuring the router ( ie. 192.168.1.1 in my browser ) to my default machine ie. uBuntu.

hope this helps...

---

