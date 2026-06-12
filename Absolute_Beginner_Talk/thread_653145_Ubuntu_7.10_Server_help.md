---
title: "Ubuntu 7.10 Server help"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by smarty79 on 2007-12-29
Hi everyone,

This is my first post so am a newb when it comes to Linux.

Basically i have a spare PC lying around at home and now i have a Static IP from my ISP i thought i would have a go at using this PC as a server so i could connect to it from over the internet for email forwarding and file storage etc.

I have downloaded the Ubuntu 7.10 Server software and have installed it. It has rebooted and is now just sitting there with commands on the screen (Starting various systems).

What do i do with it now?

I suppose i was expecting something similar to Windows, as up until now this is all i have ever used.

Can someone give me some pointers on how to proceed.

Please be gentle :)

---

### Post by taurus on 2007-12-29
The server version means it's a command line.  If you want window manager like Gnome, then you can install it with

```
sudo apt-get update
sudo apt-get install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

---

### Post by hyper_ch on 2007-12-29
You can follow this guide to setup a complete hosting/email server:
[http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10)

---

### Post by smarty79 on 2007-12-29
Thanks.

I will have a look at these.

:)

---

### Post by smarty79 on 2008-01-01
Right having another go at this now.

I am a bit confused when setting in the IP address settings. (In the Perfect Server Setup Guide)

Address - My Static IP
Netmask - subnet mask
network - ?
broadcast - ?
Gateway - My default gateway

What do i put into the network and broadcast parts?

---

### Post by hyper_ch on 2008-01-01
if it's just for testing purposes, skip that part ;)

That would only be needed if you want to operate a true email server as email servers with dynamic IP addresses will be blocked in most cases.

---

### Post by smarty79 on 2008-01-01
Well i have got a account with UKdomains, (URL and email). So could i use this server to get these emails?

If so what would i put in these bits?

---

### Post by hyper_ch on 2008-01-01
Well, I don't know what kind of setup you have.

You say you got an account with UKdoamins. So you did buy a domain name and you want that domain name point to your server that you are trying to setup?
What about email? What have you got exactely there?
Do you also have a dedicated IP address?

---

### Post by smarty79 on 2008-01-01
Well, I don't know what kind of setup you have.

You say you got an account with UKdoamins. So you did buy a domain name and you want that domain name point to your server that you are trying to setup? [COLOR="Red"]Yes i am[/COLOR].

What about email? What have you got exactely there? [COLOR="red"]The account does have email which i would like this server to retrieve then send i to a remote PC when connected.[/COLOR]

Do you also have a dedicated IP address? [COLOR="red"]I do have a static IP from my ISP[/COLOR]


Thanks for your help.

---

### Post by hyper_ch on 2008-01-01
Ok, so you got a static IP from your ISP. I assume you are connected with a modem/router, right?

---

### Post by smarty79 on 2008-01-02
Yes i am connected via a ADSL Modem/Router, this also has the Static IP programmed into it  so i will setup my router to Port Forward to the Severs local IP i assume.

---

### Post by hyper_ch on 2008-01-03
well, you have to forward those ports from the router to the server which are being used...

that would be at least:

- web (port 80)
- email smtp (port 25)
- email pop/imap (dunno by heart)
- ftp (20/21) or ssh (22)
- mysql (dunno by heart, something with 3000)
- evtl. dns queries - if you cannot use your webhosts dns servers

eventually you could make the server in the dmz - but I've never done that...

---

### Post by smarty79 on 2008-01-03
What is DMZ?

Oh and thanks for your help with this :)

---

### Post by uncannybuzzard on 2008-01-03
dmz means demilitarized zone. it means that every request to your ip would hit the server first, unless specifically addressed to another computer attached to the router. if you're serious about running a server, you may have trouble getting a domain pointing to it, unless you want to set up another computer as a slave DNS (assuming you run your primary on your current server). not many companies will let you use their name servers unless you host with them.

---

### Post by hyper_ch on 2008-01-03
depending on the registrar 1 ip for a dns-server is sufficient and then he could setup a dns server on the server also.

---

### Post by smarty79 on 2008-01-03
> **hyper_ch said:**
> depending on the registrar 1 ip for a dns-server is sufficient and then he could setup a dns server on the server also.

What do i need to check to confirm this?

Thanks

---

### Post by uncannybuzzard on 2008-01-03
they have to be able to transfer zone files. that won't be possible if the registrar is running one DNS and he is running the other.

---

### Post by hyper_ch on 2008-01-04
well, I tend to think a provider does run two independant DNS servers ;)

---

### Post by smarty79 on 2008-01-04
> **smarty79 said:**
> Right having another go at this now.

I am a bit confused when setting in the IP address settings. (In the Perfect Server Setup Guide)

Address - My Static IP
Netmask - subnet mask
network - ?
broadcast - ?
Gateway - My default gateway

What do i put into the network and broadcast parts?

Right have found some more info on these.

Adress - Is the addres my router gives the server.
Netmask - Subnet from router
Network - ?
Broadcast - ?
Gateway - Address of router

What goes in the other two lines?

---

### Post by smarty79 on 2008-01-04
Have got that bit sussed now but am having problems installing the Postfix as per 'the perfect server guide'.  (page 5)

It keeps saying couldnt find package libsas12-2


What am i doing wrong?

---

