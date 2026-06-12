---
title: "FQDN hostnames - confusing"
date: 2005-11-01
forum: Absolute Beginner Talk
---

### Post by pelle.k on 2005-11-01
<ot>This is my first post. yay! :) </ot>
So there's two types of FQDN names - internal an external.
/etc/hosts is where i should set my internal hostnames. so why should this file  include FQDN when i have none to enter besides my own computer name.

The closest thing to a domain name i would have is my external ip. or my router maybe. I don't want to make up a name that doesn't exist!

I have no external FQDN registred, but anyway this isn't supposed to be in the hosts file anyway right?

Can someone shed some light over this please?

---

### Post by KingBahamut on 2005-11-01
Are you trying to run a domain internally, is that what your asking?

---

### Post by pelle.k on 2005-11-01
Acctually, im trying to configure ubuntu as a server using this [guide]("http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p3")
(1) 127.0.0.1   localhost.localdomain   localhost   server1
this is clear to me.
(2) 192.168.0.100   server1.example.com     server1
server1 is clear to me, because that is the name of the server.
I can understand server1.example.com IF i have registred andwas  using the external domain example.com. But if i choose NOT to register a domain name, but use my  external ipfor access to my server instead, what should i use as a FQDN as i have none. or do I? Why make something up when it doesn't exist.

---

### Post by pelle.k on 2005-11-01
Sorry about posting in the wrong area. Maybe this is just a little bit above beginner level but anyway, I think i have figured it out. Please correct me if i'm wrong.

My server is named "server".

127.0.0.1 localhost.localdomain localhost (they all mean the same)
192.168.1.x server.localdomain server (even though it should be correct, is it necessary? it could be enough to remove this line and add server to localhost.)
(if i register a domainname then i can add this too... )
192.168.1.x registreddomainname.com

---

