---
title: "my internet is slow/not working sometimes"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by ddh33 on 2007-01-27
Hi all, I'm currently living in Oregon, US.

I've been a Windows user my whole life and just switched to Ubuntu because of a system crash. I'm a programmer so the command line is not too scary for me.

Everything worked after installation. I was surprised how little configuration I had to do. The internet also is working. However, it sometimes is slow, or not displaying pages at all. It shows a good connection in "Networking" with lots of packets received. DHCP/my usual IP are present. 

At first I thought I had too many windows open in Firefox. Indeed closing some could solve the problem. But sometimes it doesn't. It can stop being able to open webpages all of a sudden (always "wating" or "looking up...". Usually reboot/replugging in the cable help. A couple times I couldn't even connect to server on Gaim.

My ISP is Comcast. My Ubuntu is Edgy Eft. I'm using a Dell Inspiron 6000 with its standard devices. BTW, my internet had been very fast in Firefox on Windows.

---

### Post by riven0 on 2007-01-28
Perhaps ipv6 is giving you problems. For some reason, it's enabled by default in Ubuntu, though I don't know of anyone who is using that technology yet. So, [follow this great howto]("http://ubuntuforums.org/showthread.php?t=87798&highlight=disable+ipv6") on how to disable it.

Also, have you done the firefox tweaks? I've noticed a speed increase when doing them. 

[HowTo: Speed Up Mozilla Firefox]("http://ubuntuforums.org/showthread.php?t=179540&highlight=speed+up+firefox")


EDIT: Also, it could be you DNS server. So try following [this post for the solution]("http://www.ubuntuforums.org/showpost.php?p=1960622&postcount=7").

---

### Post by ddh33 on 2007-01-28
Thanks for the reply. I blacklisted ipv6 and did the firefox tweaks. Still some webpages are slow or fail to open. 

I also found this thread: [http://ubuntuforums.org/showthread.php?p=1647046&mode=linear#post1647046](http://ubuntuforums.org/showthread.php?p=1647046&mode=linear#post1647046)

I haven't tried it yet. I did "host something.com" in terminal for a lot of websites and it was very responsive in showing results. Not sure what to do next..

---

