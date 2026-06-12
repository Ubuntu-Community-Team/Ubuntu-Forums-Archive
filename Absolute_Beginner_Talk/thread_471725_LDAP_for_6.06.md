---
title: "LDAP for 6.06"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by wildatsun on 2007-06-12
Hello all,

I want to install an ldap server...

Which ldap server do I install?  I tried **ldap-server** but it said -

[I] Package ldap-server is a virtual package provided by:
  slapd 2.2.26-5ubuntu2.2
 You should explicitly select one to install.[/I]

But when I try to install  "**slapd 2.2.26-5Ubuntu2.2**" it says -

 "Couldn't find package slapd 2.2.26-5Ubuntu2.2"

Which package shall I download and does anyone know a good HOW-TO guide as I have searched on this forum but cannot find one that is understandable.

Thank you for all your help!

---

### Post by wildatsun on 2007-06-12
Has anyone any suggestions?

Thank you.

---

### Post by wildatsun on 2007-06-13
I found what I needed - apt-get install ldap-utils libpam-ldap libldap-2.2-7 libnss-ldap nscd

But I don't know how to test, does anyone have any suggestions?

Thank you.

---

### Post by tbaptista on 2007-06-15
Hi,

Try the howto at: [https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)

Tiago Baptista

---

### Post by lsilver on 2007-06-29
I'm trying to install a very basic LDAP server for central directory lookup of email names from Thudnerbird.  I've installed slapd and ldap-utils from the main rositories and followed the howto above (and Ubuntu Unleashed instructions) to modify the slapd.conf file as follows:

suffix          "dc=uglyduckling, dc=com, dc=au"
rootdn          "cn=manager, dc=uglyduckling, dc=com, dc=au"
rootpw		secret

Everything else is default.  However, when I run slaptest it says the conf file is invalid.  

Two questions, what's wrong with the above and how do I get any info out of slaptest to find out what's wrong with the conf file.

Thanks, Leo.

---

