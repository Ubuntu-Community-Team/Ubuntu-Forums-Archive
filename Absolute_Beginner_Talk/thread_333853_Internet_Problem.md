---
title: "Internet Problem"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by RMorris78 on 2007-01-08
I am having an odd problem with the internet. I just did a fresh install of xubuntu 6.06.1 on my new hp dv2120us laptop.  I made sure the wired connection is working, it is setup for dhcp.  i can log into my router, see other computers on my network, but not access the internet.  the internet is functioning as i am using it on this computer.

any ideas? thanks!

---

### Post by Ernewein on 2007-01-08
i am having this exact same problem, i assume our issue is the same.  I can even connect to the router and ping any computer but for some reason no internet.

---

### Post by RMorris78 on 2007-01-08
are you using 6.06.1 by any chance? what hardware are you using?

---

### Post by HereInOz on 2007-01-08
Sounds like your ubuntu machine is not picking up its DNS from the router.  Go in to System > Administration > Networking and try setting a static IP address in the same subnet as the router's internal IP address, set your gateway as the router's internal IP address and enter the DNS addresses of your ISP in the DNS section of the Networking properties box, and I reckon you will be there.

 As a test, try pinging 66.102.7.104   

If you can ping that, try pinging [www.google.com](www.google.com) 

If you can't ping that, then it is a DNS problem and the above process will probably fix it.

---

### Post by RMorris78 on 2007-01-08
awesome! it worked!

one question.... why though? ive never had to do this on any other machine?

---

### Post by HereInOz on 2007-01-08
I can't give you a definite answer, but some routers do not seem to be able to pass on the DNS info to a Linux machine, and it all seems a little haphazard.  I have had two D-Link modems, the same model, where one would relay the DNS and the other wouldn't - to the same machine, I might add.  Could have been different firmware versions.  

Mine is not to reason why, but this option works for me.  It also simplifies any subsequent prot forwarding tasks as well, as you know that the computer is always going to have the same IP address.

Glad to be able to assist.

---

### Post by RMorris78 on 2007-01-08
thanks so much for the help.  weird though, there are 3 other linux computers on the network, they use dhcp fine. hey at least it works now

---

### Post by jaywhy13 on 2007-01-11
Hmmm.. I had a similar problem today... Just wanted to share how I got around it. My prob was... i was on the network, could see other on the network... I could ping external servers all over the world.. but no content was being served to any browser I had... funny...

Two things worked for me... the latter was a permanent fix...
I changed my IP to a different one, different from the one I'm ususally assigned... that worked.

And two, I changed my router settings to ALWAYS give me the new address I chose and locked that setting so that ONLY I will get that address a any point in time. 

I was kinda playin around wit som spoofing sh*t to understand some networkin stuff I was learnin in class.. I think that contributed to my initial problem.

---

