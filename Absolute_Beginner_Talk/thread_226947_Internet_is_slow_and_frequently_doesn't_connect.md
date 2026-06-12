---
title: "Internet is slow and frequently doesn't connect"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by Keti on 2006-07-31
My internet goes extremely slowly in Ubuntu. When it works. Most of the time it won't connect. Gaim can't connect to MSN or Yahoo. Firefox can't connect to google, but sometimes connects to invisionfree and loads the banner of a page before stopping for two minutes. Sometimes I can get more reliable connections in Galeon, but it also runs slow.

I'm on a wired connection to a GT704-WG router by Actiontec, and an ADSL connection. It works great in WinXP, I can connect to anything and everything quickly.

If there's anything else you need to know for a diagnosis and cure, I'll be watching the thread for the next couple hours probably, ask and I'll get back as quickly as possible.

Thanks in advance.

---

### Post by Smandola on 2006-08-01
Keti,
This may be an obvious question, but what type of hardware do you have.  ie: processor, Ram, HD. Lets start there, and try to figure out why you have such slow internet speeds.

s.

---

### Post by gils0040 on 2006-08-01
i had the same problem with an actiontec router. The solution was to set a static ip and dns (the actual problem was that the actiontec router was assigning an incorrect dns). to check to see if this is your actual problem do:
less /etc/resolv.conf
it should list a domain and 2 dns addresses. if one of the addresses is the address of the router, this is your problem. let me know what you find out

---

### Post by Keti on 2006-08-01
search domain_not_set.invalid
nameserver **192.168.1.1**
nameserver 68.238.112.12

Router's IP is obviously the first one.

Guess that's it. So what's the fix?

---

### Post by gils0040 on 2006-08-01
you can either
1. system -> administration -> networking, select your device and configure it for a static ip. once that is done go to the dns tab and change the 192.168.1.1 to the correct dns server (it will probably be slightly different then the other one and can be found by opening a browser and going to 192.168.1.1 and i think the status page). This will fix the issue on your computer.

or
2. you can fix the actual problem that lies with the router by telneting into it (my actiontec 701 router uses busybox, im assuming that the 704 does as well) and rewriting the /etc/udhcpd.conf file. this can be done by the following:
cat udhchpd.conf # this will display the contents of the file
cat > udhcpd.conf # this will allow you to rewrite the file

rewrite the file exactly how it is shown except the line that reads
opt dns 192.168.1.1 (other dns address) 
change 192.168.1.1 to the correct dns value (found from that status page of your router)
when you have completed rewriting the file press ctrl+d which will close and save the file. then you can reaquire an ip from the router by rebooting your computer. note that this method must be done everytime the router is rebooted.

good luck!

*btw the user and password for telneting are probably both "admin"

---

### Post by Keti on 2006-08-01
I tried option 1, and as soon as I set it for a static IP, it doesn't to connect to anything off my LAN. But instead of waiting 5 minutes to tell me that firefox won't connect, it does so in about .5 seconds. Any idea what went wrong?

---

### Post by gils0040 on 2006-08-01
make sure that once you configure everything, that you select the correct default gateway device at the bottom of the network settings. if it still isnt working, try pinging your router and if that works try pinging google or some other website.

---

