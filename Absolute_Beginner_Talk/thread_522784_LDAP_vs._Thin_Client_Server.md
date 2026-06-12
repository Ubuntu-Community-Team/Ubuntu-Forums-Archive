---
title: "LDAP vs. Thin Client Server"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by leetcharmer on 2007-08-11
Hi, I would like to increase my linux server specialties.  Can anyone tell me the differences in security among an open LDAP server vs. an Thin Client Server?  What are the advantages of one over the other.  Can they be integrated simultaneously?

On my current Test Box, I have a NAS configured and all computers can login to the server box to gain an extra 200GB storage :D.  Next thing I wanna do is get a similar Active Directory going so the server administration can have fairly high control over the clients in the network.  I'm kinda scatterbrained on the concepts of setting up both LDAP and Thin Client, so can you help me know where to start?  Thanks!

---

### Post by P_Squiddy on 2007-08-20
Well, the two concepts aren't entirely in the same field of inquiry.  LDAP is an authentication method, while Thin Client is a means of providing service to a client.  With LDAP, you do things like hold information about the user, like password, group memberships, etc.  Thin Client implementations generally provide a working environment for the user on a low-end unit ("thin" client) while running the actually applications from a high-end server.

You can use LDAP with a Thin Client implementation.  OpenLDAP is a good topic to Google for more info on how to use LDAP (or use this [link]("https://help.ubuntu.com/community/OpenLDAPServer") for Ubuntu info).  For Thin Client information, you may want to check out LTSP (the Linux Terminal Server Project).  Ubuntu info is [here]("https://help.ubuntu.com/community/UbuntuLTSP").

---

