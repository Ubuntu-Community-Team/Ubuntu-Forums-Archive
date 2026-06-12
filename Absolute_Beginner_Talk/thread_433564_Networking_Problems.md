---
title: "Networking Problems"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by Rhaddad on 2007-05-05
every since I upgraded to fiesty. I have been having networking problems.
1. Printer sharing doesn't work
2. When i try to share folders by going system-->Administration-->shared folders I select the folder and click close. When I open it back up again the shared folder that i Chose isn't on there, as well as the domain MSHOME, that I'm sharing files with.

---

### Post by bullgr on 2007-05-05
it's goot to use gui but sometimes you need to get dirty with the command line...
so, better do it manualy setting up samba
go there
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
or there
[http://doc.gwos.org/index.php/Share_files_using_Samba](http://doc.gwos.org/index.php/Share_files_using_Samba)

with this howto's your be fine

---

### Post by Rhaddad on 2007-05-05
I don't have a static IP though,  you need static IP's for these.

---

### Post by bullgr on 2007-05-05
how you connect your pc's?
don't you connect them thru a router or direct with a ethernet cable?
you can setup a static ip.
if you mean that you have a dsl connection with dynamic ip, it's different from your local ip.
you can for examble have in the first pc ip 192.168.0.1 in the second pc 192.168.0.2 and the
gateway (router) 192.168.0.100
that is the static ip metioned  in the howtos...

give more details...

---

### Post by Rhaddad on 2007-05-05
Oh, I was thinking of something else. As in with my router to my ISP(dynamic). I'll take it of DHCP release and do the tutorial, and I'll get back to you. Thanks

---

### Post by Rhaddad on 2007-05-05
Those tutorials didn't work, but i was reading something about synaptic manager and how it doesn't remove conf files unless you do a complete remove, I did that and reinstalled it. And everything is working.

---

