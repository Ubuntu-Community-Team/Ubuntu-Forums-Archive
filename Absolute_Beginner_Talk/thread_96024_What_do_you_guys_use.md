---
title: "What do you guys use?"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by adduds on 2005-11-27
Hey all reading! :)

hope your all having linux funs, i was just wondering what you guys use for detecting WLAN Networks. I just installed ubuntu a couple days ago, and i go to university and they have wireless all throughout (like most). Will Unbuntu pick it up on it's own?

I installed **airsnort** but when i run scan i get (in terminal, i run it from their):

aadduds@ubuntu:~$ airsnort
/sbin/wlanctl-ng eth1 lnxreq_ifstate ifstate=enable > /dev/null
sh: /sbin/wlanctl-ng: No such file or directory
SIOCSIFFLAGS: Permission denied

Just wondering what **everyone** else uses? and what could **cause** that error??? i use eth1 for my internet so it's not null....

---

### Post by invalid on 2005-11-27
Try
```
sudo airsnort
```

Cb

---

### Post by adduds on 2005-11-28
I tried sudo airsnort (doesn't work)

it just keeps printing

adduds@ubuntu:~$ airsnort
/sbin/wlanctl-ng eth1 lnxreq_ifstate ifstate=enable > /dev/null
sh: /sbin/wlanctl-ng: No such file or directory
SIOCSIFFLAGS: Permission denied
 
infinitely cause it keeps scanning, until i press stop

Although i am using a wireless internet connection cause this is on my laptop so i nkow my wireless card is working....

any ideas?

cheers/thx,
ad

---

### Post by KingBahamut on 2005-11-28
airfart is better in my opinion. 
[http://airfart.sourceforge.net/](http://airfart.sourceforge.net/)

---

