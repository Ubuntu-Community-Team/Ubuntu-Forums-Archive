---
title: "Is it possible for Debian to run Ubuntu packages?"
date: 2012-12-19
forum: Any Other OS
---

### Post by linuxvstheworld on 2012-12-19
I've heard that in Debian you can install the Ubuntu Software Center to install Ubuntu packages on it, it kind of makes sense due to the fact that Ubuntu is based off of Debian, can it run any Ubuntu package?

---

### Post by CharlesA on 2012-12-19
Possible maybe, but not really recommended.

It could break things.

---

### Post by sandyd on 2012-12-19
Installing debian software in Ubuntu breaks things, so I would assume the reverse as well, even if Ubuntu is based on debian unstable

---

### Post by MadmanRB on 2012-12-20
I have done it, and yeah its not overly recommended.
I mean it will work if you have a compliant debian (such as sid) but I would not use it on stable (such as wheezy)

---

### Post by UltimateCat on 2012-12-20
Hi:

I've been running Debian 6.5.0 for about 7 months and all of the packages that I have installed have come directly from the Debian Repositories.
[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)
[http://www.debian.org/](http://www.debian.org/)

I don't recommend that you install packages that do not come from your distributions repo's. It not only could break things but there could be  the possibility of the system becoming unstable and or un-operative -

As Sandyd said; " Installing debian software in Ubuntu breaks things"

Taking wise counsel is your best bet-

Debian is a rock solid OS if your looking for stability-

---

### Post by snowpine on 2012-12-20
Can you be more specific what is the actual package you are trying to install? It is much easier to discuss specifics then abstract. I am sure there are some packages that probably work OK and some that don't. :)

---

### Post by Mopar1973Man on 2012-12-20
Ummm... Noob here... I thought any .DEB files where acceptable for Ubuntu being its a Debian based OS? :confused:

---

### Post by snowpine on 2012-12-20
> **Mopar1973Man said:**
> Ummm... Noob here... I thought any .DEB files where acceptable for Ubuntu being its a Debian based OS? :confused:

You probably shouldn't install .deb's willy-nilly (though again, I prefer discussing specifics to abstract). Rather, you should preferably find a .deb that is specific to your distro and release (in other words, don't try to install a 12.04 .deb in 12.10 and so forth).

---

### Post by CharlesA on 2012-12-20
> **snowpine said:**
> You probably shouldn't install .deb's willy-nilly (though again, I prefer discussing specifics to abstract). Rather, you should preferably find a .deb that is specific to your distro and release (in other words, don't try to install a 12.04 .deb in 12.10 and so forth).

Indeed. I rarely install a third-party deb unless I need to. For example, the  CLI/web interface software for my raid card comes as a RPM and I had to use alien to convert it to a deb. Not pretty but it worked, but it only worked because it was a very generic RPM.

---

### Post by lykwydchykyn on 2012-12-21
> **Mopar1973Man said:**
> Ummm... Noob here... I thought any .DEB files where acceptable for Ubuntu being its a Debian based OS? :confused:

.deb is just a format for delivering compiled software.  The packaging format may be compatible, but that doesn't guarantee that the software inside is compiled in a way that is compatible.

---

### Post by Mopar1973Man on 2012-12-21
Learn something new every day... ;)

---

### Post by linuxvstheworld on 2012-12-23
> **snowpine said:**
> Can you be more specific what is the actual package you are trying to install? It is much easier to discuss specifics then abstract. I am sure there are some packages that probably work OK and some that don't. :)
I don't use Debian it was just a question that popped into mind. :p

---

### Post by scorpiosnake on 2012-12-24
> **linuxvstheworld said:**
> I've heard that in Debian you can install the Ubuntu Software Center to install Ubuntu packages on it, it kind of makes sense due to the fact that Ubuntu is based off of Debian, can it run any Ubuntu package?

I certainly wouldn't recommend installing Ubuntu Software Center on Debian (not even sure if it is possible) or using a lot of Ubuntu packages on Debian. Most packages that are available on Ubuntu are also on Debian, so it is best to use the packages from the OS repos.

However there are times when things are not available for Debian, for whatever reason. I have installed a few Ubuntu packages on Debian Sid in the past and never had any problems. One example is pysdm, which I have installed right now on my Debian partition. It works great on Debian, but it is not available in the Debian repos so I grabbed the Ubuntu package.

This usually does not work with Debian Stable as the libraries are usually older than what the Ubuntu package needs.

However, nothing is certain and I have heard of people having problems using Ubuntu packages on Debian.

If you plan on using a lot of packages that are only available to Ubuntu is most likely best to just use Ubuntu.

---

