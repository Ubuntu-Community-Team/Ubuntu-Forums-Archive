---
title: "Connecting to the internet"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by pEdRiDeR2008 on 2006-09-28
On my Ubuntu that i just installed I cannot connect to the internet but I can in XP.  How do I fix this?

---

### Post by Bachstelze on 2006-09-28
Just hold on a sec, I'm asking my crystal ball what kind of connection you have :D

---

### Post by GreenHawkIA on 2006-09-28
HTL means - just a bit more information would be helpful.  Do you have dial-up or an always-on (Cable or DSL) connection?  Do you connect wirelessly from a laptop or using a cord?  What type of hardware are you using (routers, modems, etc)?  We can't help without some more info.
No slam at HTL here, just hopin' to help clarify un poquito.

---

### Post by pEdRiDeR2008 on 2006-09-28
I have broadband through zoomtown.  It uses a cord on my desktop and it has a cable modem that then connects into the phone line.  Its always on.

---

### Post by Bachstelze on 2006-09-28
RJ-45 or USB ?

---

### Post by pEdRiDeR2008 on 2006-09-28
Rj-45

---

### Post by GreenHawkIA on 2006-09-28
Rj-45 aka an ethernet or Cat-5 cable too.  Darn, HTL, posting while I'm writing my reply ;).  That's why these forums are awesome - and you have 900-billion beans.

---

### Post by pEdRiDeR2008 on 2006-09-28
It does work in XP, but in Ubuntu it does not run, do I have to configure it?  And if so how and where do I do this?

---

### Post by extempore88 on 2006-09-28
I am having a problem similar to the user above...

I am a long-time windows user who just made the linux jump yesterday, but I am not especially good with computer terminology, so I beg slack from HTL ;-).  

After installing yesterday, I tried to connect to the internet using firefox.  In XP, I connect using a wireless LAN (Linksys Router) from a Satallite connection.  I tried opening the network menu from the administrators tab and clicked "activate" on the wireless icon.  I exited the network page and loaded the internet browser.  Firefox still showed the error page (it was able to load Ubuntu's default homepage, but not any google or wiki pages).  After calling a friend who has oodles of computer experience (not much Linux and no Ubuntu), I tried entering the IP address I pulled off the XP partition.  Still no luck.

That's about all I can remember, but I fooled around with settings for about an hour yesterday trying to get it to work.  Whatever you gents (and ladies) can say to help would be appreciated.

---

### Post by Kreg on 2006-09-28
I am having a similar problem too. 

I am trying to connect to my university network by cable. I used to be able to connect on XP. The annoying thing is in the network window when i click on the ethernet it shows packets being sent and recieved but when i go into firefox nothing happens.

Kreg

---

### Post by nts on 2006-09-28
> **Kreg said:**
> I am having a similar problem too. 

I am trying to connect to my university network by cable. I used to be able to connect on XP. The annoying thing is in the network window when i click on the ethernet it shows packets being sent and recieved but when i go into firefox nothing happens.

Kreg

Can you ping sites?

If so, it seems like a DNS issue, check your resolve.conf file and make sure you have the correct DNS resolver ip addresses - check wioth your network admin, what these should be. They should be set in your router, but sometimes its worth checkin in Ubuntu too.

The resolve.conf file is located in /etc/

---

### Post by pEdRiDeR2008 on 2006-09-28
Anybody?

---

### Post by chrisfay on 2006-09-28
> I have broadband through zoomtown. It uses a cord on my desktop and it has a cable modem that then connects into the phone line.

Last time I checked, broadband internet didn't use the telephone...:p 

Post the output of:

```
route
```
and
```
ifconfig
```

Maybe you have something wrong in your routing table or ip configuration.

---

### Post by Liqua on 2006-09-29
I also had a similar problem - for me it turned out that the router I was using (D-Link G604T) could not respond to any DNS queries from Linux. (But worked fine within Windows).  

I had to manually assign a static IP for my linux box and point it to a pair of external DNS servers (your ISP can provide you with some if needed).

---

### Post by GreenHawkIA on 2006-09-29
Another thing you can try - is to disable IPv6 on your Ubuntu system...especially if you can only access certain sites, this seems to work.  Try [this thread]("http://www.ubuntuforums.org/showthread.php?t=266613").  And see if it helps.

---

### Post by jiminid on 2007-03-02
> **pEdRiDeR2008 said:**
> I have broadband through zoomtown.  It uses a cord on my desktop and it has a cable modem that then connects into the phone line.  Its always on.

So do I, and I just posted a request for some info on how to configure ubuntu to use zoomtown to connect. Have you had any luck figuring this out? Zoomtown tech support told me they only support windows...Someone please help us out of Gatesland...

---

