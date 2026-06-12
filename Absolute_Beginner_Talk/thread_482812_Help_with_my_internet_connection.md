---
title: "Help with my internet connection"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by syed1994 on 2007-06-24
I just install Ubuntu here and I don't know why my internet connection cannot resolve the IP. It works on XP.

P.S. Don't let me think that "load modules" I would no, just give me the terminal lines.

---

### Post by Crafty Kisses on 2007-06-24
> **syed1994 said:**
> I just install Ubuntu here and I don't know why my internet connection cannot resolve the IP. It works on XP.

P.S. Don't let me think that "load modules" I would no, just give me the terminal lines.
Are you on a wireless connection?

---

### Post by syed1994 on 2007-06-24
I am connected directly to my cable modem.

---

### Post by Crafty Kisses on 2007-06-24
> **syed1994 said:**
> I am connected directly to my cable modem.

Try to ping a website, for example:
```
ping google.com
```

---

### Post by syed1994 on 2007-06-24
It says unknown host.

---

### Post by xpod on 2007-06-24
Have you tried rebooting everything.........cable modem included??

---

### Post by syed1994 on 2007-06-24
Yes

---

### Post by syed1994 on 2007-06-24
Can anyone help?

---

### Post by skillet on 2007-06-24
what are the contents of /etc/resolv.conf?

---

### Post by mattg89 on 2007-06-24
in the console do:
```
sudo ifconfig
```
and post up the results

---

