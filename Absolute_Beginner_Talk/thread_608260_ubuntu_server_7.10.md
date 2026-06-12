---
title: "ubuntu server 7.10"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by shawnstelzer on 2007-11-09
I am new to ubuntu and tring to set up a server to work as a predictive dialer and want to know how to get Asterisk I dont know how to get the software to download when I typed deb [http://archive.ubuntu.com](http://archive.ubuntu.com)
-bash: deb: comand not found

---

### Post by llamakc on 2007-11-09
```

sudo apt-get install asterisk


```

---

### Post by shawnstelzer on 2007-11-09
I Typed sudo apt-get install asterisk and then it asked for password I typed in the password and enter
sendmail:fatal open/etc/postfix/main.cf:no such file or directory

---

### Post by llamakc on 2007-11-09
Do you plan on running mail on the machine? I'm unfamiliar with the program asterisk, but you can install a sendmail-compatible mailer without bothering with that mess. mailx is one such package.

---

