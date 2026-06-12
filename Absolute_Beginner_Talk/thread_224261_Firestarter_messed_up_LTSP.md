---
title: "Firestarter messed up LTSP"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by OMRebel on 2006-07-27
I'm about to kick myself...lol
I installed Firestarter on my Edubuntu server.  After installing it, my clients cannot log in now.  I can boot and get to the login screen, but no user can log in at this point.  It was working fine until I put Firestarter on it.  I even tried turning off the firewall inside of Firestarter, but same thing.  

How can I go in and manually configure the server to allow users to log in again from the clients?

First person to answer this gets a toast in their honor. :D 

Thanks everyone.

---

### Post by OMRebel on 2006-07-27
Just to give a bit more information - I am unable to login through Webmin now as well.

---

### Post by OMRebel on 2006-07-28
Bump

---

### Post by T700 on 2006-07-28
You can use Firestarter to create a rule (policy) to specify the client's port and protocol that is allowed through the firewall.  Are you sure that you actually disabled the firewall in Firestarter?  Just shutting down Firestarter will not open back up the ports.

Paul

---

