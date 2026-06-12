---
title: "apt-get install slapd"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by afaquino on 2006-10-24
Hi! I like Ubuntu Dapper very much!
I am recently installing and configuring ldap on my box when I
accidentally deleted /etc/ldap/schema directory. Now my problem is that I can't install slapd anymore! or the content of /etc/ldap/schema is always empty! Help pls... I am a newbie

Thanks

---

### Post by mbradlcu on 2007-12-14
well this is a very late response but you may want to try:
```

sudo apt-get purge slapd

```
```

sudo apt-get install slapd

```

---

