---
title: "what forum should i got to?"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by elvinatom on 2007-06-07
**Hello community,**
I've been working in the IT field a bit (MS networking) and after 12 years of developing anger towards MS, I installed linux on my workstation about 1.5 month ago and I liked it.  I used to have a Win2K server hosting my site, DNS, FTP and files in an AD domain - serving 6 Win2k/XP workstations.

A week ago I wiped out my server to replace it with Ubuntu server (feisty 64) and I'm now trying to get everything back on track - with some difficulties ...  I've successfully installed DNS and apache2 (was rather simple).  I've installed Xorg/KDE-core to run some gui-based configuration tools and firefox (is that a bad idea?).

Problem is:
I can't get LDAP setup with users and groups,  Users and groups authentication on my LAN is my goal.  Windows boxes just need access to the samba shares with encryted authentication, but they don't need to log onto the directory.
I don't really know a thing about linux, so I've followed several howtos and guides (also from this site), but i get an error message when i get to the point of loading the initial data: 

***ldapadd -x -W -c -D "cn=xxxxxx,dc=xxxx,dc=xx" -f /etc/ldap/init.ldif*** (the x-es are username,domain and suffix).

It asks me for the password and then returns:

***ldap_bind: Can't contact LDAP server (-1)***,

I've tried to set the switch -d8 but got the same message (no additional info).

I ran into other problems with other guides and I'm starting to get frustrated.  I've also tried to read some manuals, but I don't understand much of the explaned and therfore don't really gain any knowledge.  I am a pretty resourceful guy but this is brutal.

How do I get this straight, or how do I get global knowledge of linux networking in general? Any easy to understand books out there with practical examples that is up to date?

Little help here would be super.  (and please forgive me the long-winded blurb)

---

### Post by elvinatom on 2007-06-07
Problems setting up LDAP is my topic - i've read a sticky in the server forum that says go to the HOWTO forum, but where is it?

---

### Post by John.Michael.Kane on 2007-06-07
These may be of use.
[http://ubuntuforums.org/showthread.php?t=271629&highlight=LDAP](http://ubuntuforums.org/showthread.php?t=271629&highlight=LDAP)
[http://ubuntuforums.org/showthread.php?t=223805&highlight=LDAP](http://ubuntuforums.org/showthread.php?t=223805&highlight=LDAP)

For further Tutorials & Tips
[http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)

---

### Post by elvinatom on 2007-06-07
Thank you - will check it out!

---

