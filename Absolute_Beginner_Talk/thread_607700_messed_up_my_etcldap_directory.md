---
title: "messed up my /etc/ldap directory"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by kalil on 2007-11-09
After having problems with a previous slapd installation I removed all ldap packages. But it seems like I removed too much. When I try to reinstall slapd I get the following errors:

/tmp/slapd.config.90451: 1337: cannot open /etc/ldap/schema/core.schema: No such file
/tmp/slapd.config.90451: 1337: cannot open /etc/ldap/schema/cosine.schema: No such file
/tmp/slapd.config.90451: 1337: cannot open /etc/ldap/schema/nis.schema: No such file
/tmp/slapd.config.90451: 1337: cannot open /etc/ldap/schema/inetorgperson.schema: No such file

Any ideas on how to bring my ldap directory back to initial state?

---

### Post by kalil on 2007-11-09
Gentle bump. I could really use some help here.

the /etc/ldap directory is empty save for two empty directories. Reinstalling libldap, slapd and ldap-utils does nothing to improve the situation.

---

### Post by tekknokrat on 2007-12-19
try 

```
apt-get purge slapd
```

---

