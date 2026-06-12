---
title: "Ubuntu progress screen gone"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by mep on 2006-11-17
Hello,

I installed Kubuntu-desktop into my 6.10 gnome system.  I played for a bit in KDE and then decided to stay with Gnome.  I uninstalled the kubuntu-desktop but for some reason I am left with the Kubuntu startup progress screen rather than the Ubuntu screen at reboot??  How do I get the ubuntu progress screen back?  Again this is the progress screen before logging into system

Thanks in advance,

-mep

---

### Post by sam81 on 2006-11-18
Have a look at this thread:     [http://www.ubuntuforums.org/showthread.php?t=301916]("http://www.ubuntuforums.org/showthread.php?t=301916")
hope it helps!

---

### Post by mep on 2006-11-18
Thanks for the link to solve problem.

I used te below command:

```
sudo dpkg-reconfigure usplash-theme-ubuntu

```

It solved it!

Thanks,

-mep

---

