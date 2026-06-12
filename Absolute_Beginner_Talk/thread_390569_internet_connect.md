---
title: "internet connect"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by rwlange47 on 2007-03-22
I have a strong dislike for the windows application and have loaded ubuntu on my desktop.  I was able to get ubuntu to load but am unable to connect to the internet.   I am really new to linux/unix but am anxious to learn.  Can anyone assist with getting my internet connection?  Is there a good manual or location where I can learn the linux/unix language?
thank you
rwlange47
[email]rwlalnge47@yahoo.com[/email]

---

### Post by meborc on 2007-03-22
ok... tell us what kind of connection do you have? ADSL? cable? static IP or dynamic? dou you need to insert your login and password for internet under windows? do you have router or modem?

:)

---

### Post by rwlange47 on 2007-03-22
thanks for the reply.  i have cable internet using firefox and when needed explorer.   I do not log in when accessing the internet and am using a linksys wireless-g router but am cabled from the router to my desktop.

---

### Post by mrmonday on 2007-03-22
Go to:

System> Administration> Network Tools

Change the device to Ethernet interface, have you got an IP address?

---

### Post by rwlange47 on 2007-03-23
I have an ip which is being used on my windows machine.  Should i get a different ip address and how do I do that.
thank you
rwlange47

---

### Post by Bachstelze on 2007-03-23
Open up a terminal,

```
sudo dhclient eth0
```

as simple as that.

---

