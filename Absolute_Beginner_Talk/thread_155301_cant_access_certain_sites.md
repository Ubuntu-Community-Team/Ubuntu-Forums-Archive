---
title: "cant access certain sites"
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by malavar on 2006-04-04
hey, im having problems accessing certain websites from time to time, such as google, or sun etc. sometimes google works but lately it wont load at all, my other computers that were on the same network, but were using different OS's worked fine. any idea on what the problem might be? im using firefox

---

### Post by dermotti on 2006-04-04
Are they all useing the same DNS servers?

---

### Post by johnnymac on 2006-04-04
Set your properties of firefox to use less cache...or remove cookies after exit....works for me and it keeps things lean

---

### Post by malavar on 2006-04-04
johnnymac i tried your solution but it didnt work, im not using and yes i believe they are using the same dns server.

they all goto the same router (homemade freesco router) i even tried plugging this pc directly to the internet and still no luck. im thinking its a software problem either linux or firefox,

---

### Post by stoeptegel on 2006-04-04
Are you on DSL or cable? Once in a while i also have an unstable DNS server of my ISP (demon.nl)
If yes then try to setup a DNS server from another ISP located in your country and see if that makes any difference.

PS.You can test your DNS server response with "traceroute" (not installed by default)

---

### Post by malavar on 2006-04-04
hey im on cable, ok ill try that thanks,

---

### Post by malavar on 2006-04-04
hmm i ran a traceroute and the hops are taking longer than normal, some getting as high as 50+ ms on local routers. i pinged google.com and it worked normally, but when i tried the url again it failed...

---

### Post by halitech on 2006-04-04
I might be off base but what version of FF are you using? Don't think DNS is really the issue cause you can get the DNS resolution to know where google is. I'm thinking the IPv6 setting is turned on and not working well

---

### Post by malavar on 2006-04-04
im using ff 1.0.7 the stock version that comes with warty warthog lol

---

### Post by halitech on 2006-04-04
if you type in about:config in the address bar and look about 3/4 way down, it's something about network dns ipv6, try turning that off and then restart FF

---

### Post by malavar on 2006-04-04
i set network.dns.disableIPv6 to true and still no luck

---

### Post by stoeptegel on 2006-04-04
[QUOTE=malavar]hmm i ran a traceroute and the hops are taking longer than normal, some getting as high as 50+ ms on local routers. i pinged google.com and it worked normally, but when i tried the url again it failed...[/QUOTE]

The hops are not part of the test though. 
Just if you get an IP adress in the reply you know the DNS server is more or less working. Then there's probably someting else wrong.

---

### Post by malavar on 2006-04-04
well i just said that because earlier i noticed downloads would freeze half way through and stuff so i figured it had something to do with lost packets or something of that nature. thanks for all the help. 
btw when i try google, or sun, i dont get a error page i dont get any page for a few minutes... then i get a message box that it cant find the site, (but traceroute and pinging eventually find the site) i hope im not confusing everyone thanks in advanced for more help.

---

### Post by stoeptegel on 2006-04-04
Well i am not sure where the problem is, but i have to go somewhere...
 
Are you able to telnet into your modem and look for packet losts, collisions or errors?
In my modem i can find this information in menu "System Maintenance - Status".

---

### Post by malavar on 2006-04-04
i found that its related to network.dns.ipv4OnlyDomains with a value .doubleclick.net now i dont know how to fix it

---

### Post by sohailubuntu on 2006-04-05
Malavar, I'm having the same exact problem. The browser will try and access the site for a few minutes and then won't be able access the site. What's worse is that after this happens previous sites that were working fine, don't work at all. And I'll have to restart my computer to use the internet. I noticed that this happened when I tried to access cnn.com.

---

### Post by TheRingmaster on 2006-04-05
[QUOTE=malavar]im using ff 1.0.7 the stock version that comes with warty warthog lol[/QUOTE]

maybe try getting the new version of firefox (1.5)

---

