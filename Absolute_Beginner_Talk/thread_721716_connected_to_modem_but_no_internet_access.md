---
title: "connected to modem but no internet access"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by Juggrnott on 2008-03-11
I have been using Ubuntu for about 6 months everything was working wonderfully. My whole household is glad to say We don't do windows lol. but my problems began when i followed the instructions on [this thread ]("http://ubuntuforums.org/showthread.php?t=508145")about connecting to xbox live through ubuntu. I connected to xbox live for almost 10 mins then everything went kaput. 
I connect to the internet through a wireless card to a 2wire dsl modem. I can connect to the modem but my internet does not work. I have an XP laptop (for work) that still connects just fine. If someone could help me that would be great. 

Thanks

---

### Post by neurostu on 2008-03-11
So you can get an internet connection? Try a couple of things:
-ping your router
-ping another computer on your network
-ping google.com

post results!

---

### Post by neurostu on 2008-03-11
Also try running ```
 ifconfig
```
and post the results

---

### Post by Juggrnott on 2008-03-11
Ping? I know in windows to ping from the command prompt put ping.(whatever your pinging) but not sure how to in terminal

---

### Post by Juggrnott on 2008-03-11
> **neurostu said:**
> Also try running ```
 ifconfig
```
and post the results

I will post as soon as i get home (still at work)

---

### Post by neurostu on 2008-03-11
running ping in the terminal is really easy:
```

ping <ip.address>

```
like
```

ping 192.168.1.1

```
or
```

ping www.google.com

```

---

