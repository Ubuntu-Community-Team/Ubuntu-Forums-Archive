---
title: "Connecting to the Internet"
date: 2006-01-01
forum: Absolute Beginner Talk
---

### Post by daddywelsh on 2006-01-01
Hello everybody.:p 

Although I'm an experienced PC user I'm completely new to Linux. Chose Ubuntu as it seemed to be the friendliest. I've just installed Ubuntu 5.10 and it went flawlessly except for connecting to the Internet. I have an adsl router with windows pcs connected, the linux box occupies the last slot. Ubuntu has recognised the ethernet card on the PC but still can't connect. Does anybody have some step by step instructions on what to do, I tried the help files but not enough info there. Any help on setting up the ethernet connection and settings in Firefox would be highly appreciated.

---

### Post by cwaldbieser on 2006-01-01
[QUOTE=daddywelsh]Hello everybody.:p 

Although I'm an experienced PC user I'm completely new to Linux. Chose Ubuntu as it seemed to be the friendliest. I've just installed Ubuntu 5.10 and it went flawlessly except for connecting to the Internet. I have an adsl router with windows pcs connected, the linux box occupies the last slot. Ubuntu has recognised the ethernet card on the PC but still can't connect. Does anybody have some step by step instructions on what to do, I tried the help files but not enough info there. Any help on setting up the ethernet connection and settings in Firefox would be highly appreciated.[/QUOTE]
Try going through these steps, and post any outputs where you have trouble:
[http://ubuntuforums.org/showthread.php?t=87643]("http://ubuntuforums.org/showthread.php?t=87643")

---

### Post by vasudevank on 2006-01-01
since it is adsl you may want to try this 

Code:
adsl-setup
adsl-start

I don't know if Ubuntu supports rr-ppope, but it is worth a try

---

### Post by stream303 on 2006-01-17
What does your /etc/resolv.conf file show?

If a nameserver such as 192.168.0.1 or 192.168.1.1 appears, it could be that dhclient is picking up the dns server inside your router rather than using your isp's nameservers

---

### Post by hen3rz on 2006-01-17
Hello,

When i first booted up ubuntu i also had trouble setting up my internet and found these forums a great help!

The problem I had with mine was Ubuntu was trying to use my modem/router as a DNS server and was having no luck and not allowing me to go on the internet. 

To check if your having the same problem you could try type in:
```
ping 66.102.7.104
```
into the terminal and if you get a reply it means you have a problem with your DNS servers.

To fix this i simply went to my ISP's website and searched for there DNS servers and simply deleted the DNS's servers Ubuntu added and placed my ISP ones to the DNS list in **System > Administration > Networking > DNS Servers**

---

