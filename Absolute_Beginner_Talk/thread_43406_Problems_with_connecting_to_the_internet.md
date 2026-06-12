---
title: "Problems with connecting to the internet"
date: 2005-06-21
forum: Absolute Beginner Talk
---

### Post by b3n123456 on 2005-06-21
I went to this page:
[https://wiki.ubuntu.com/DialupModemHowto?highlight=%28Dial%29%7C%28up%29](https://wiki.ubuntu.com/DialupModemHowto?highlight=%28Dial%29%7C%28up%29)
I did what it said but when I try to connect, it says something about an error with the /etc/ppp/peers/provider thing. Im not absolutely sure it detects my modem either even though it doesnt say anything is wrong with that. I searched the forum to find a similar thread as this one but I couldnt find one. Also when ubuntu is loading it says it has an error with /lib/modules/2.6.8.1-3-386/kernel/drive/pci/hotplug/shpchp.ko and then when ubuntu takes me to the desktop, it says something about an error with XKB configuration and how its too complex or somthing. Any help is **greatly** appreciated.

---

### Post by bunced on 2005-06-22
Can we have some more details on the errors, please. Exact error messages would be good  :-P 

Regards,
David

---

### Post by b3n123456 on 2005-06-23
[QUOTE=bunced]Can we have some more details on the errors, please. Exact error messages would be good  :-P 

Regards,
David[/QUOTE]
 It doesnt say the error anymore but when I go through the /etc/ppp/peers/provider thing, it doesnt let me. The icon for the provider thing has a box with a cross on it. It says stuff like access denied and stuff like that. Also where do I find the ip number for my primary name server?

---

### Post by bunced on 2005-06-23
For the primary name server, on a windows OS with the same server, do Start -> Run -> type 'cmd' -> When a black box comes up, type 'ipconfig /all' -> Scroll down until you reach a line that has DNS Nameserver or something line that -> Copy down the set of numbers on that line that have a pattern similar to xxx.yyy.zzz.aaa -> Put these into the Linux primary name server box.

Regards
David

---

### Post by b3n123456 on 2005-06-26
[QUOTE=bunced]For the primary name server, on a windows OS with the same server, do Start -> Run -> type 'cmd' -> When a black box comes up, type 'ipconfig /all' -> Scroll down until you reach a line that has DNS Nameserver or something line that -> Copy down the set of numbers on that line that have a pattern similar to xxx.yyy.zzz.aaa -> Put these into the Linux primary name server box.

Regards
David[/QUOTE]
 Thanks, Ill try that. It took me a long time to find this thread, I thought someone deleted it because it was a stupid question or something.
Edit: I typed in ipconfig /all and not much happened. It just wasi windows ip configuration and it didnt have anything else.

---

### Post by bunced on 2005-06-27
But you need to take the DNS numbers from this ip configuration for your primary name server.

---

### Post by b3n123456 on 2005-06-27
[QUOTE=b3n123456]Thanks, Ill try that. It took me a long time to find this thread, I thought someone deleted it because it was a stupid question or something.
Edit: I typed in ipconfig /all and not much happened. It just wasi windows ip configuration and it didnt have anything else.[/QUOTE]
 Ok I tried another time and this time it worked. I dont know why it didnt the last time. Anyway, the pattern to the dns nameserver isnt like xxx.yyy.zzz.aaa it is more like xxx.yy.zzz.aa So I did that and it came up with 2 dns nameservers numbers. Im not sure if anyone could hack me or whatever if I give the number out and if I just replace them with an "x" then you wont be able to see because there is the same amount of numbers but they are different.

---

### Post by bunced on 2005-06-27
OK - the number you need is the first DNS server. No, no-one can hack you if you give the number out - DNS normally belongs to your ISP not you. You would have to have your IP address and even then you would have things like Firewall (I hope!). Besides, you are broadcaasting your IP when you surf anyway :D.

So, to get back on track, you need the first DNS server

---

### Post by b3n123456 on 2005-06-28
[QUOTE=bunced]OK - the number you need is the first DNS server. No, no-one can hack you if you give the number out - DNS normally belongs to your ISP not you. You would have to have your IP address and even then you would have things like Firewall (I hope!). Besides, you are broadcaasting your IP when you surf anyway :D.

So, to get back on track, you need the first DNS server[/QUOTE]
 Ok I tried to put the first number in and then it asked for a second number, I put the other number in and followed through with the rest of the stuff. I typed in sudo pon and it said etc/ppp/peers/provider wasnt permitted or something. If you need me to state what it exactly says, I will do so. Do I really need a firewall? I thought you didnt need any protection etc with linux.

---

### Post by bunced on 2005-06-28
Yes, can I have the exact error message, please

---

### Post by b3n123456 on 2005-06-28
[QUOTE=bunced]Yes, can I have the exact error message, please[/QUOTE]
 Ok, watch this space, Ill go check it.
Edit: Ok I put in the name server and all that other stuff, I finished and tried to connect to the internet. I typed in sudo pon and it dropped down a line and it was blank for a few seconds then ben@ubuntu:~ $ came up. I assumed it connected so I tried fire fox and it said it couldnt find the page I wanted. SO I opened up the terminal again and typed in sudo poff and then it said /usr/bin/poff: No pppd is running. None stopped. Maybe I didnt create it properly.

---

### Post by bunced on 2005-06-28
ty

---

### Post by b3n123456 on 2005-06-28
[QUOTE=bunced]ty[/QUOTE]
 Maybe it is my modem. It is a Generic SoftK56 modem.

---

### Post by b3n123456 on 2005-06-28
Maybe it is my modem, it is a Generic Softk56.

---

### Post by bunced on 2005-06-29
I would start up another thread dedictated to the Generic Softk56 and see if anyone knows of a driver for it (ie. put Softk56 in the title)

Regards
David

---

