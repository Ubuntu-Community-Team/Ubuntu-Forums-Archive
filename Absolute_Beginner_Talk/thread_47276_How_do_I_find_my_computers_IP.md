---
title: "How do I find my computers IP ?"
date: 2005-07-08
forum: Absolute Beginner Talk
---

### Post by weasel fierce on 2005-07-08
What do you do in Ubuntu to find your own IP ? 

I need to figure out how to set my router up, so it forwards correctly, and will work with DC++

---

### Post by drummer on 2005-07-08
[QUOTE=weasel fierce]What do you do in Ubuntu to find your own IP ? 

I need to figure out how to set my router up, so it forwards correctly, and will work with DC++[/QUOTE]
 do ifconfig in a terminal and you'll get something like this:```
$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1036178 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1036178 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:94148878 (89.7 MiB)  TX bytes:94148878 (89.7 MiB)

wlan0     Link encap:Ethernet  HWaddr 00:09:5B:BF:03:3A
     -->  inet addr:192.168.1.2  <-- Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::209:5bff:febf:33a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38290 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40107 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:27137591 (25.8 MiB)  TX bytes:7813269 (7.4 MiB)
          Interrupt:17 Memory:fb020000-fb021fff

```
the Ip address is where I've put the -->   <-- under wlan0, you would look under the name of your network interface (for ethernet, it's probably eth0, wlan0 is my wireless network card)

---

### Post by weasel fierce on 2005-07-08
You sir, are a gentleman

---

### Post by drummer on 2005-07-08
All in a day's work ;)

---

### Post by Kvark on 2005-07-08
The network tool under system tools provides this info and several other useful network diagnostics in a GUI interface.

(just don't port scan computers that are not your own, then they might think you are looking for a port to hack them through)

---

### Post by gammyhand on 2005-07-08
[QUOTE=Kvark]The network tool under system tools provides this info and several other useful network diagnostics in a GUI interface.

(just don't port scan computers that are not your own, then they might think you are looking for a port to hack them through)[/QUOTE]
 what does ifconfig mean? Did they just not want to copy windows and use ipconfig? ;)

---

### Post by drummer on 2005-07-08
From the man pages:  ifconfig - configure a network interface
so I'm guessing that it stands for **_i_**nter**_f_**ace **_config_**uration,
but yes.. it does look suspiciously familliar... :?

---

### Post by somuchfortheafter on 2005-07-08
and since it does show the interfaces entire configuration not just ip info it makes sense however i had a wee bit of trouble with it so much that i used alias to link ipconfig to ifconfig lol.

---

### Post by Mr. Electric Wizard on 2005-07-08
Heehee,
I have a gDesklet setup on my desktop that has my Host Name and IPAddress.... :)

---

