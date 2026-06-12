---
title: "debian wheezy with unity-greeter"
date: 2012-09-05
forum: Any Other OS
---

### Post by microcore on 2012-09-05
When i asked this on debian forums, they kicked me away :)

I have installed lightdm from debian repo and unity-greeter from ubuntu 12.04 package. It works fine - i can change background, choose theme and enable/disable grid. but have little problem, like [COLOR="Blue"]_[COLOR="Blue"][this]("http://osdir.com/ml/ubuntu-accessibility/2012-04/msg00169.html")[/COLOR]_[/COLOR] - i can't shutdown/restart from greeter.
Commands from this instruction doesn't work for me.
Could somebody help me with it?

Sorry for my eng

---

### Post by tartalo on 2012-09-06
> **microcore said:**
> When i asked this on debian forums, they kicked me away :)

I have installed lightdm from debian repo and unity-greeter from ubuntu 12.04 package.

I went to Debian User Forums expecting hilarious sarcastic comments. Unfortunately, except one comment that simply linked to this forum, what I found was a quite boring thread where people repeatedly told you that mixing Ubuntu and Debian repositories was unsupported and probably wouldn't work.

---

### Post by UltimateCat on 2012-09-10
Like Tartalo said; you should not have installed an application that was designed for Ubuntu. 

Un-install the Unity-Greeter as root
```
apt-get purge <name of unity greeter>

```

# apt-get remove; removes a package
# apt-get purge removes; the pkg and it's configuration files

---

### Post by Haghiri75 on 2012-09-10
you shouldn't install from ubuntu package. 
you should add ubuntu repos from /etc/apt/sources.list to debian :)

---

### Post by tartalo on 2012-09-10
> **UltimateCat said:**
> Like Tartalo said; you should not have installed an application that was designed for Ubuntu.

Oh no, I said nothing about his little experiment, I said that OP's "being kicked out Debian forums" was far from the comedy I expected after reading that expression, what's more I felt that the forum, as a whole, didn't "kick him out".

---

### Post by marticc on 2012-09-23
> **microcore said:**
> When i asked this on debian forums, they kicked me away :)

I have installed lightdm from debian repo and unity-greeter from ubuntu 12.04 package. It works fine - i can change background, choose theme and enable/disable grid. but have little problem, like [COLOR="Blue"]_[COLOR="Blue"][this]("http://osdir.com/ml/ubuntu-accessibility/2012-04/msg00169.html")[/COLOR]_[/COLOR] - i can't shutdown/restart from greeter.
Commands from this instruction doesn't work for me.
Could somebody help me with it?

Sorry for my eng

I am using lightDM and unity greeter in Debian (actually in LMDE with my repos pointing to testing), and I've got the same problem and I have not been able to fix this.

Anyway, how did you manage to change the background?, I have not been able to do it (I tried editting the unity greeter.conf file, but it is not working. Any suggestions?

---

### Post by NormanFLinux on 2012-09-23
Ubuntu and its community supported distro family IS based on Debian's unstable branch.

That's why packages made to work on Ubuntu might not work on Debian and vice versa.

---

### Post by marticc on 2012-09-24
I know that Ubuntu and Debian are not 100% compatible, and that there might be problems. The point is that I have been using lightDM with unity greeter in LMDE / debian testing with no problems (so I guess that unity greeter can be used in Debian testig), but, when I updated lightDM, despite the fact that I can use unity greeter I have been uable to change the background.

---

