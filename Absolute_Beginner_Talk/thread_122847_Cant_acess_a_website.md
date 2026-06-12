---
title: "Cant acess a website?"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by Elfie on 2006-01-28
Hello there,

This is my first day using ubuntu, but I've played some with slackware and freeBSD before.. 

However, my question is what I need to enable for using a webbrowser since every page "Connection refused...", but I can ping the pages thru a terminal. Im also allowded to ping other LAN-computers such as my windowsbox. 



Whats the problem here?
*using a router*

---

### Post by bscbrit on 2006-01-28
I assume that you are not accessing this forum using your webbrowser?  If you are, then its working!

Are you able to ping [www.ubuntuforums.org?](www.ubuntuforums.org?)  Have you successfully updated software from the net but cannot use just the webbrowser?

---

### Post by stream303 on 2006-01-28
[QUOTE=Elfie]
Whats the problem here?
*using a router*[/QUOTE]

Sound like a dns problem.  In your networking dns tab, what nameserver is listed?
(or look at the **/etc/resolv.conf** file)

If it isn't one that your isp provides (typical of soho routers), try finding the isp's primary and backup nameservers and entering that in the configuration boxes as the first ones in the list.

If that works, we can go from there ...

---

