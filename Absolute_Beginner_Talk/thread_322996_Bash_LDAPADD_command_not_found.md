---
title: "Bash: LDAPADD: command not found"
date: 2006-12-21
forum: Absolute Beginner Talk
---

### Post by EuroPimp on 2006-12-21
Hi, I'll try to describe my situation.
I'm trying to run an LDAP-server on Ubuntu 6.06. I installed slapd with 'apt-get install slapd' and adjusted 'slapd.conf' (in /etc/ldap/) to my needs. I also set up the LDAP-structure in a file called 'base.ldif'.
Now, when I try to add this ldif file with the 'ldapadd' command, it won't work.
I'm getting the following error message: 'bash: ldapadd: command not found'

Is there a solution to this?

---

### Post by JShadow on 2006-12-21
Do you have the ldap-utils package installed?

---

### Post by Ferri on 2006-12-21
Have you tried "sudo ldapadd"?

---

### Post by EuroPimp on 2006-12-21
> **JShadow said:**
> Do you have the ldap-utils package installed?

Thanx, that was the solution :).

---

