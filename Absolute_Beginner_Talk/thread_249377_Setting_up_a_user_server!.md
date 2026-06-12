---
title: "Setting up a user server!"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by dragze on 2006-09-02
hi, is it possible to setup a user server like you can with windows server?? i.e. setup the user accounts of each user on the server and the other pc's connect to the server to get user information etc, plus this would allow users to change there password and it is then changed on all the machines, compared to adding each user on each machine and having to change the user password on each machine aswell.

I know you can do this on a windows server and am wondering if this can be done on linux im sure it can but i dont know where to start.

Suggestions please!!

Thanks,
dragze.

---

### Post by bluefrog on 2006-09-02
ldap server or Samba-Ldap server.

see idealx.org amongst other things for samba-ldap
[http://www.tldp.org/HOWTO/LDAP-HOWTO/](http://www.tldp.org/HOWTO/LDAP-HOWTO/)
[https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)

James

---

### Post by dragze on 2006-09-02
cheers for the info bluefrog, just one question is it as hard as it looks to setup or is it not to bad once u get into it??

cheers again,
dragze.

---

### Post by furiousV on 2006-09-02
> **dragze said:**
> cheers for the info bluefrog, just one question is it as hard as it looks to setup or is it not to bad once u get into it??

cheers again,
dragze.

I have never set up LDAP or anything before (I'm at college right now, and will most likely learn to do it on Windows Server 2000/2003) but see if [Webmin](http://www.webmin.com/) will make it any easier for you.

They have it available as a standard module. [http://www.webmin.com/standard.html](http://www.webmin.com/standard.html)

That should make things easier for you. If you decide to install Webmin and LDAP from there, let me know how you got on :)

---

### Post by dragze on 2006-09-05
cheers for all your help!! :D i will give webmin a try cheers!
i will let u know how i get on! :S (fingers crossed!)

Cheers again,
dragze.

---

