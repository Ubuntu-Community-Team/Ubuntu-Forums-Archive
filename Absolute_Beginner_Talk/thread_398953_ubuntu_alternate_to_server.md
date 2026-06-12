---
title: "ubuntu alternate to server"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by lazlow on 2007-04-01
I've followed advice I found on these forums and installed ubuntu 6.10 using the alternate CD, as the server wont boot on my EPIA 5000.

I'm now in 6.10 as an OEM user, prior to deleting it and ubuntu asking for the user's info on the next boot.

However, I am wanting a server configuration rather than what appears to be a standard desktop setup with the alternate CD. Is there a simple way to 'convert' the alternate install to a server setup?

Failing that, I've tried a LAMP install following the [howtoforge guide](http://www.howtoforge.com/ubuntu_debian_lamp_server). But once I apt-get the various packages I'm asked to insert the original install CD! I don't want to have to re-connect the CD-ROM drive everytime I need to update or install a new package, as this EPIA 5000 is running very bare. Is there a way around this?

So two questions, from a complete ubuntu n00b, but I'm willing to learn - thanks in advance!

---

### Post by zvacet on 2007-04-01
for first you can use this
[http://www.plug.org/pipermail/plug/2005-October/017588.html]("http://www.plug.org/pipermail/plug/2005-October/017588.html")
or 
```
sudo aptitude remove ubuntu-desktop
```

Maybe first solution is better cause leave you chance to reactivate GUI if you want to.for second 
```
gksudo gedit /etc/apt/sources.list
```
and put # sign in from of line with Cd realese.After that you will not be asked to insert disc when you installing something.

---

### Post by lazlow on 2007-04-02
> **zvacet said:**
> for first you can use this
[http://www.plug.org/pipermail/plug/2005-October/017588.html]("http://www.plug.org/pipermail/plug/2005-October/017588.html")
or 
```
sudo aptitude remove ubuntu-desktop
```

Maybe first solution is better cause leave you chance to reactivate GUI if you want to.for second 
```
gksudo gedit /etc/apt/sources.list
```
and put # sign in from of line with Cd realese.After that you will not be asked to insert disc when you installing something.Thanks for the reply!
One question though, the link you posted seems completely alien and unrelated. But then again, it's probably down to my lack of linux knowledge.

I had to revert to using the alternate CD for install, as the EPIA 5000 doesn't support the 686 kernel of the server install apparently.

---

### Post by zvacet on 2007-04-02
That link is about disable GUI.In that case you still have it on your comp and it is just disabled.Second solution uninstall it.That is the diference.

---

### Post by lazlow on 2007-04-02
Brilliant, thanks for clarifying it!

---

