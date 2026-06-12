---
title: "Proxy Help"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by adewale on 2008-02-12
Hi,
I have a little problem, i want to be anonymous, this is because my isp restricts me from loading certain pages including yahoo mail, currently am limited to maximum of 300kb of data, so thats a problem. I would have use tor but its about 2mb, On windows multi proxy or Ultra surfer would do the job and free me. Anyway please is there any ubuntu program that would do this thanks.I've downloaded tiny proxy but i don't have a clue on what to do. Thanks

---

### Post by Aquaman420 on 2008-02-12
Here is a thread that will probably help you.

[http://ubuntuforums.org/showthread.php?t=419997&highlight=tor+privoxy]("http://ubuntuforums.org/showthread.php?t=419997&highlight=tor+privoxy") 

Here is an old one, but I am sure many philosophies still apply

[http://ubuntuforums.org/showthread.php?t=95527&highlight=tor+privoxy]("http://ubuntuforums.org/showthread.php?t=95527&highlight=tor+privoxy")

---

### Post by adewale on 2008-02-16
Please guys help out, I've downloaded the tor, privoxy, foxyproxy installed everything but firefox refuses to browse. **This is because my isp made it compulsory for me to use a proxy address to connect**. How do i tell tor to use this proxy
Thanks

---

### Post by adewale on 2008-02-16
No help yet ? Ultar surf did this with ease it asked for my network config how can TOR do this i just need to give my proxy

---

### Post by peabody on 2008-02-16
You don't need tor to proxy if you have a proxy provided by your isp

System -> Preferences -> Network Proxy

If you have the latest foxy proxy I don't think you need privoxy to use tor any more, provided tor is running (and can actually connect to the Internet, again, if your ISP FORCES you to proxy, then I don't think tor will work).  Foxy proxy should just be able to set it up for you.  You may have to run tor by using

sudo /etc/init.d/tor restart

in a terminal.

To clarify, if all you need is a way to connect to your ISP's proxy service, IGNORE tor, it's not what you want.

---

