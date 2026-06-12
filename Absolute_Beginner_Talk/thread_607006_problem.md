---
title: "problem"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by binzer on 2007-11-08
Hi,
I've a problem with ubuntu startup. When I startup ubuntu, it doesn't show the login screen, rather the following commands appear:
* starting anac(h)ronistic cron an acron                  [ok]
* starting deferred excution scheduler atd              [ok]
* starting periodic command schedulear crond         [ok]
*checking battery state...                                        [ok]
* Running local boot scripts(/etc/rc.local)                 [ok]
-(a blinking curser)

I rebooted ubuntu manytimes, but the problem persists. Please tell me how I can fix it.

thanks

---

### Post by me208 on 2007-11-08
I'm sorry but I think you have to re-install :(


ps. use more discriptive thread names

---

### Post by NightCrawler03X on 2007-11-08
PS:
Arch Linux, [http://archlinux.org](http://archlinux.org)

---

### Post by louieb on 2007-11-08
Sounds like you did a server install. Press enter a see if you get the login prompt.

---

### Post by Sef on 2007-11-08
> Sounds like you did a server install. Press enter a see if you get the login prompt.

If that is your problem then once you log in, at the prompt, type this command:

```
sudo apt-get update
```

then

```
sudo apt-get install ubuntu-desktop
```

That will install the Ubuntu Desktop Environment for you.

---

