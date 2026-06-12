---
title: "Google only site loading"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by reidamd on 2007-04-27
I'm using Fiesty Fawn vs 7.04
I can get onto the google site, and run a search, but then none of the reults links will work. just stuck on waiting for..... 
I can ping sites no problem
When I reset my router, I can access any site for about 10 seconds, then I get the same problem
GAIM works fine

Is this a problem with DNS? I just installed ubuntu and this is what Im running into

If any one has any ideas, please let me know. I'm using an actiontec MI424WR router with Verizon FioS

---

### Post by toddward on 2007-04-27
Which browser are you using?  It sounds like the browser is restricting your view to certain pages--possibly a security setting.  Because if you can ping, then you should be able to get out to other servers with your browser.  

Try another browser to surf the web.

---

### Post by dbstraffin on 2007-04-27
> **reidamd said:**
> I'm using Fiesty Fawn vs 7.04
I can get onto the google site, and run a search, but then none of the reults links will work. just stuck on waiting for..... 
I can ping sites no problem
When I reset my router, I can access any site for about 10 seconds, then I get the same problem
GAIM works fine

Is this a problem with DNS? I just installed ubuntu and this is what Im running into

If any one has any ideas, please let me know. I'm using an actiontec MI424WR router with Verizon FioS

What version of firmware is running on the actiontec? I had problems with the older firmware where once you hit a certain number of connections (especially with torrents), no more would go through.  I couldn't even connect to the web page on the router itself.
The autoupdate in the router doen't find the latest firmware.  Please try the lastest version from here: [http://fiosfaq.com/index.php?action=cat&catnum=12]("http://fiosfaq.com/index.php?action=cat&catnum=12")

---

### Post by reidamd on 2007-04-27
I'm using firefox 2.0
I cant download another browser though!
How can I try changing the security settings, I would prefer to use Firefox if possible

Also, could this be a problem with my onboard ethernet card? I'm using A PcChips A33G mobo

---

### Post by toddward on 2007-04-27
I would have to say it doesn't sound like a problem with your ethernet card.  You can ping various things with the terminal...

Since Google is already cached up, we need to ping something else.  If you don't look at digg.com a lot, try pinging that:

```
ping -c3 www.digg.com
```

As for the security settings inside of firefox, go to Edit -> Preferences.

dbstraffin may have a point about connections being limited.  So, for a test, ensure that the only thing going out to the web is the web browser.

---

### Post by Cypher on 2007-04-27
This might be a MTU problem. Try
```

sudo ifconfig eth0 mtu 1400

```
and see if things work. If not, change 1400 to 1300 or 1200 or 1100, all the way down to 500 and see which one works..

---

### Post by reidamd on 2007-04-27
Okay, I just upgraded the firmware, worked for a few seconds b/c of router reset, now back to only google working. This is seems very weird to me.

---

### Post by reidamd on 2007-04-27
okay, I could ping digg.com I just tried the MTU fix, seems to be working!!! Horray... lets see if it holds up. Just a quick question, I'm happy you helped me fix this, but what exactly did I just do?? lol What's MTU I've never heard of it.

---

### Post by Cypher on 2007-04-27
MTU stands for [Maximum Transmission Unit]("http://en.wikipedia.org/wiki/Maximum_transmission_unit") and I'll let my friend Wikipedia do the 'splaining..;)

If whatever value you set the MTU to works over an extended period of time, we'll need to figure out how to get Ubuntu to set that value for you automatically instead of doing it manually each time you boot up.

---

### Post by reidamd on 2007-04-27
Horray, I'm on ubuntu forums, while actually using ubuntu. 1400 seems to work fine. How do I go about having it stay at this MTU everytime I boot??

---

### Post by jchaike on 2007-11-09
hey i know this thread is a bit old, but,  i had the EXACT SAME problem. i did the MTU thing, and it worked perfectly. I am now in the process of installing ubuntu to ym harddrive (rather then using the LiveCD). I was wondering if there is a way to make the MTU permanent? or if it is already permanent. 

Thanks =D

---

