---
title: "What are the differences between Ubuntu Server edition &amp; Red Hat Enterprise Edition?"
date: 2005-11-11
forum: Absolute Beginner Talk
---

### Post by Akhran on 2005-11-11
What are the differences in terms of hardware driver support, hardware detection and such? Or are the differences are only in terms of packaging?

Thanks.

---

### Post by LHZ on 2005-11-11
I don't know anything about the hardware detection features of either, to be honest, but there's a difference in philosophy between Red Hat Enterprise and Ubuntu Server that's very important.

Red Hat Enterprise is Red Hat's flagship product, designed to be sold to businesses who want good customer support, good applications, and lots of extras. It's a big, shiny Linux. That's why you have to pay for it.

In contrast, Ubuntu Server is the *minimal* install, designed to get an old computer up and running as a web or file server. So instead of fanciful and user friendly, it's exteremely basic (it doesn't even have a graphical interface).

They're not quite the same thing :D

---

### Post by Akhran on 2005-11-11
Does it mean that ubuntu server edition is not suitable to be installed modern enterprise servers?

Thanks.


[QUOTE=LHZ]I don't know anything about the hardware detection features of either, to be honest, but there's a difference in philosophy between Red Hat Enterprise and Ubuntu Server that's very important.

Red Hat Enterprise is Red Hat's flagship product, designed to be sold to businesses who want good customer support, good applications, and lots of extras. It's a big, shiny Linux. That's why you have to pay for it.

In contrast, Ubuntu Server is the *minimal* install, designed to get an old computer up and running as a web or file server. So instead of fanciful and user friendly, it's exteremely basic (it doesn't even have a graphical interface).

They're not quite the same thing :D[/QUOTE]

---

### Post by chazzjazz on 2005-11-11
no it means you have to be less noob to run a ubuntu server....if you are noobie then pay thru your nose to get the point and click of redhat :)

---

### Post by LHZ on 2005-11-12
[QUOTE=Akhran]Does it mean that ubuntu server edition is not suitable to be installed modern enterprise servers?

Thanks.[/QUOTE]
Yes it is. It just takes more skill and know-how.

I would, however, advise against using Ubuntu server for daily office work, unless your cmputers are really, really old. Use either regular Ubuntu or a lightweight distro like DSL or Puppy for that.

The 'selling point' of Red Hat enterprise is that a company can buy it to run it both as a server and on everyones desktops. You get a all-in-one solution with good applications and good support, but you pay for it.

---

### Post by Akhran on 2005-11-12
Any difference between the Server edition and the normal ubuntu installation with 'server' option?

Thanks !

[QUOTE=LHZ]Yes it is. It just takes more skill and know-how.

I would, however, advise against using Ubuntu server for daily office work, unless your cmputers are really, really old. Use either regular Ubuntu or a lightweight distro like DSL or Puppy for that.

The 'selling point' of Red Hat enterprise is that a company can buy it to run it both as a server and on everyones desktops. You get a all-in-one solution with good applications and good support, but you pay for it.[/QUOTE]

---

### Post by LHZ on 2005-11-12
As far as I know, there's no seperate 'sever edition', just the option to do a server install with the standard install cd.

---

### Post by apjone on 2005-11-12
[QUOTE=Akhran]What are the differences in terms of hardware driver support, hardware detection and such? Or are the differences are only in terms of packaging?

Thanks.[/QUOTE]
ubuntu server is alot easier to use, with redhat there are alot of gotcha's , eapecially with Kudzu and sendmail at boot time. If you are new to linux then use ubuntu server unless you know someone who can help you with redhat

---

### Post by Akhran on 2005-11-12
Server edition : [http://www.ubuntuforums.org/showthread.php?t=79093](http://www.ubuntuforums.org/showthread.php?t=79093)

[QUOTE=LHZ]As far as I know, there's no seperate 'sever edition', just the option to do a server install with the standard install cd.[/QUOTE]

---

### Post by ThirdWorld on 2005-11-12
Does ubuntu have any plans to compete with other distros like redhat on the enterprise market? offer certifications? will they create tools similar to active directory to manage networks?

---

### Post by bluefrog on 2005-11-12
as suggested above, use ubuntu normal install to sestup a server, you will have less hassle than if you select server at the install. 
with ubuntu normal install, takes 10 minutes (time to download the packages more or less) to install samba-ldap for example.
installing it on the server install ubunut will take you quite more time cause of all the things you will have to install ahead...

james

---

### Post by apjone on 2005-11-12
[QUOTE=ThirdWorld]Does ubuntu have any plans to compete with other distros like redhat on the enterprise market? offer certifications? will they create tools similar to active directory to manage networks?[/QUOTE]

umm ubuntu just got Certified for IBM DB2 which is a big step in becoming enterprise ready server distro

---

### Post by ThirdWorld on 2005-11-12
[QUOTE=apjone]umm ubuntu just got Certified for IBM DB2 which is a big step in becoming enterprise ready server distro[/QUOTE]


Does that mean that we can expect ubuntu certifications (im talking about training like redhat certs) corporate, goverments migration and server deployments?

---

### Post by LHZ on 2005-11-12
[QUOTE=Akhran]Server edition : [http://www.ubuntuforums.org/showthread.php?t=79093](http://www.ubuntuforums.org/showthread.php?t=79093)[/QUOTE]
Right. My knowledge has just been updated.

It's pretty much what they say in the first post: you get the bare bones server install (no GUI), and lots and lots of useful (command line) tools for webservers and the like. It's like the server install + stuff you'll be using anyway.

---

