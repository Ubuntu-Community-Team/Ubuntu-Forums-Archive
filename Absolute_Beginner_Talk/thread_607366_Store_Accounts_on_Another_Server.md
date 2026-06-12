---
title: "Store Accounts on Another Server"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by laika$ on 2007-11-08
I'm note even sure of the right words for this:
I've got three Ubuntu desktops for my kids and I'd like to have accounts on all three machines for all three  kids.  Yes I could create accounts for each on each, but that is a major pain, especially if one steals the other's pwd and we have to change them, etc.

So I'd like one machine to act as an "account server" for the other two, and store the login credentials on one machine.  Any pointers?

Thanks.

---

### Post by Dr Small on 2007-11-08
I don't exactly know how to do this, but with SSH, you could have the users on the ssh server, but i don't know how one computer would connect to the other to verify ssh accounts and then login to the desktop.

Maybe there is a simpler way.

Dr Small

---

### Post by Whiffle on 2007-11-08
Easy :)

Setup one computer as a nfs server (has to be on all the time that the other two computers are used ), make it share a folder over nfs (maybe call it users), and then have the client computers mount the /users directory in /home via /etc/fstab.  Point each users home directory to a directory in that shared directory (i can't remember where this setting is, somewhere under Administration > users ?), and you should be set.  You can use permissions to make sure they stay out of each others business.  Its possible to syncronize passwords as well across all of the machines, but I've never had a need to (so i dont know how).

---

### Post by ubnewbie2 on 2007-11-08
Here's a full blown solution

[http://times.usefulinc.com/2005/09/25-ldap](http://times.usefulinc.com/2005/09/25-ldap)

The link points to instructions for setting up an ldap server, and telling linux to use it to authenticate

---

### Post by laika$ on 2007-11-08
holy cr*p that's complicated.  How did unix do it before ldap?

---

### Post by ubnewbie2 on 2007-11-08
> **laika$ said:**
> holy cr*p that's complicated.  How did unix do it before ldap?

:)

Well, it is a full directory service.  Have you ever played with Novell's NDS or MS's Active Directory?   They can all get a bit complicated to set up.

It's a good question though.  Is there a more simple authentication server that unix/linux can use.  I have read of Fedora Directory Server, but I think it's a bit full on too.

---

