---
title: "Problems installing packages"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by Josh_b on 2006-07-24
Hey,

I've tried a few how-to's on here ([Hotmail/Evolution]("http://www.ubuntuforums.org/showthread.php?t=200408") and [Firewall]("http://ubuntuguide.org/wiki/Dapper#firestarter")), and when I use sudo apt-get install to get either firestarter or hotway hotsmtp, it can't find it. I've also searched through Synaptic.

Am I doing something wrong?

Thanks,
Josh

---

### Post by taurus on 2006-07-24
How exactly did you try to install those with apt-get?  Also, make sure you remove the # sign in front of all the lines for universe & multiverse in /etc/apt/sources.list...

Open a terminal, Applications -> Accessories -> Terminal, and type

```

sudo gedit /etc/apt/sources.list

```

---

### Post by Who on 2006-07-24
> **Josh_b said:**
> Hey,

I've tried a few how-to's on here ([Hotmail/Evolution]("http://www.ubuntuforums.org/showthread.php?t=200408") and [Firewall]("http://ubuntuguide.org/wiki/Dapper#firestarter")), and when I use sudo apt-get install to get either firestarter or hotway hotsmtp, it can't find it. I've also searched through Synaptic.

Am I doing something wrong?

Thanks,
Josh

I don't know about these specific packages, but if you do a 'name and description' search for them and you can't find theme then they are almost certainly not in your repositories

BUT, that probably doesn't mean you can't get them...

You acn gain access to lots more software by enabling more repositories. 

In Synaptics you gan use Settings-->Repositories to enable all the Ubuntu ones (universe, multiverse) or this guide to get even more
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories](http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories)

Note that software from these places isn't supported officially (in Synaptic, supported packages have a little ubuntu man by them)

---

### Post by Josh_b on 2006-07-24
I removed all the #'s in front of the URL's in the sources.list file and can now find those packages.:D 

Thanks

---

