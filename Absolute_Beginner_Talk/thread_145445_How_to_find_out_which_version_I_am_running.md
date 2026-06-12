---
title: "How to find out which version I am running"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by fubar0 on 2006-03-16
Hello, 

Is there a command were I can find out which version (Breezy, Hoary, ...) I am running?

Thanks in advance

---

### Post by SpectralDesign on 2006-03-16
uname -a

this will tell you what kernel you are using.... hrm...

The only qucik answer I can give is that if you are in X-windows and click the life-saver (help) icon, it shows the version of Ubuntu there....

---

### Post by mlind on 2006-03-16
cat /etc/issue

---

### Post by fubar0 on 2006-03-16
Many thanks! Just wanted to check if my ```
apt-get distr-upgrade
``` worked.

---

### Post by Lord Illidan on 2006-03-16
[quote=fubar0]Many thanks! Just wanted to check if my ```
apt-get distr-upgrade
``` worked.[/quote]
Actually, it is ```
apt-get dist-upgrade
```

---

### Post by fubar0 on 2006-03-16
of course, you're right! Typo!

---

### Post by jrib on 2006-03-16
```
lsb_release -a
```

---

### Post by henriquemaia on 2006-03-16
[QUOTE=_jason]```
lsb_release -a
```[/QUOTE]

Nice tip. Thanks.

---

### Post by aysiu on 2006-03-16
This may not be the "proper" way to do it, but you can also press Control-Alt-F1 and see.

Then press Control-Alt-F7 to get back.

---

