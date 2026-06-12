---
title: "LAMP + LDAP auth?"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by jedimastermopar on 2007-12-20
Anyone able to point to a tep by step to installing a ubunut LAMP server with LDAP auth?

---

### Post by blueridgedog on 2007-12-22
LAMP is in install option in Ubuntu server.  What do you want to authenticate with LDAP?

---

### Post by syutzy on 2007-12-22
I just set this up on our department webserver at school.  Here's a helpful guide: [http://wiki.case.edu/Apache#LDAP]("http://wiki.case.edu/Apache#LDAP")
If you're using 7.10, use mod_authnz_ldap, but the general idea is the same.
Obviously you'll need to replace the information specific to my school with your own info.
The one thing I'm still working on is secure LDAP.  I'll try to remember to post back here when I figure it out.

General guide:
-Make sure that mod_ldap and mod_authnz_ldap are installed and enabled
-Configure LDAP connection settings (I created and linked ldap.conf to store these)
-Add restricted access code to .htaccess, <directory> tags, etc

---

