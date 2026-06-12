---
title: "Just installed feisty. GAIM won't connect"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by TheFourElements on 2007-04-22
I just finnished installing feisty and when I went to open GAIM it wouldn't connect to the network. All it says is that it is waiting for the network. D.oes anyone know how to fix this? Any help is appreciated.

---

### Post by RobsterUK on 2007-04-22
Which service are you trying to connect to? It may be an issue at their end

---

### Post by TheFourElements on 2007-04-22
MSN messenger

---

### Post by G4HZA on 2007-04-22
This is a problem with routers all over the internet.  The problem is caused by these routers 'corrupting' your ip packets.  Further informaion regarding this problem including how to change a linux setting to overcome this issue can be found here -http:// articles.techrepublic.com.com/5100-1035_11-6174075.html

This website is down as I type this but you need to type this command - sudo echo 0 > /proc/sys/net/ipv4/tcp_default_win_scale

If you need any further help give me an email.

Roger

---

### Post by TheFourElements on 2007-04-22
Funny thing happened. I restarted my computer once more and now it works.

---

