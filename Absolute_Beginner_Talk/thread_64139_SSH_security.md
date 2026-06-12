---
title: "SSH security"
date: 2005-09-10
forum: Absolute Beginner Talk
---

### Post by Moonshine on 2005-09-10
Hi,

I've installed SSH on my old computer running Ubuntu 5,04 so I can access whilst I'm at college. I'll only be using it for SSH occassionally - Once a week or so maybe, to connect to the internet. It is working fine from here at the moment (haven't had the chance to test it at college yet) but I'm wondering what steps I need to take to ensure that is remains safe. From reading various articles I've picked that using a secure password and not logging in as root. How about a firewall? Is port 22 ok to be left open the whole time? 

Thats all for now, Thankyou.

edit: I now realise that this is probably the wrong section. Sorry about that.  ](*,)

---

### Post by cwaldbieser on 2005-09-10
[QUOTE=Moonshine]Hi,

I've installed SSH on my old computer running Ubuntu 5,04 so I can access whilst I'm at college. I'll only be using it for SSH occassionally - Once a week or so maybe, to connect to the internet. It is working fine from here at the moment (haven't had the chance to test it at college yet) but I'm wondering what steps I need to take to ensure that is remains safe. From reading various articles I've picked that using a secure password and not logging in as root. How about a firewall? Is port 22 ok to be left open the whole time? 

Thats all for now, Thankyou.

edit: I now realise that this is probably the wrong section. Sorry about that.  ](*,)[/QUOTE]
Sometimes switching to a non-standard port will thwart casual scans.

A firewall that just blocks ports won't be significant unless you have other services running you want to block.  You could configure a firewall to do more sophisticated things like limiting how often someone can connect to your PC to slow down brute-force attacks.

If you are ultra-paranoid, you try out something like [http://doorman.sourceforge.net/](http://doorman.sourceforge.net/), though I haven't seen anything like it in the repositories.

---

### Post by Moonshine on 2005-09-10
Thankyou for that reply,

One other question...

I assumed that after installing SSH, it would run as a service indefinately. However after I restarted this computer, it wasn't working. So how can I go about manually turning it on and off?  :-? 

Thanks again.

---

### Post by evilghost on 2005-09-10
```

sudo /etc/init.d/ssh start
sudo /etc/init.d/ssh stop

```

:)

---

