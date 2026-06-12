---
title: "How to open ports?"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by Valthinos on 2008-02-08
Hi everyone, I was just wondering how to open ports in Ubuntu. I need to open ports for programs like Warcraft so I can play properly. Any and all help is appreciated!

Thanks!

---

### Post by skymera on 2008-02-08
i woukdnt open any to *everyone*

try Firestarter from the repos.

easily customisable and can open ports to specific IP's or everyone.

```
 sudo apt-get install firestarter 
```

---

### Post by Valthinos on 2008-02-08
I have firestarter and I have ports open but it's still not working.. Maybe I did something wrong. What do I have to do, just set the ports? Or something more?

---

### Post by y-lee on 2008-02-08
[ Opening ports.]("http://www.ubuntugeek.com/how-to-open-bittorrent-ports-from-the-command-line.html")  that might help for a simple command line way.

Firestarter might be the best way tho. up to you. :)

---

### Post by y-lee on 2008-02-08
Just found this too, [ Warcraft Tft port opening]("http://ubuntuforums.org/showthread.php?t=151050")

---

### Post by Valthinos on 2008-02-08
Thanks for all your help y-lee. I tried to follow the guide from Warcraft Tft port opening but I got lost. However, I did send him a pm so hopefully I'll get a response soon. Anyway, I'll just boot into windows to play for now, no biggie. Once again, thanks for your help, greatly appreciated.

---

### Post by dreadlord_chris on 2008-02-09
Are you possibly behind a router (some DSL/Cable modems have built-in NAT, same issue)? If so, you'll need to deal with port-forwarding from the router/modem. It's quite possible that Windows UP&P was/is *transparently* configuring this for you.

---

