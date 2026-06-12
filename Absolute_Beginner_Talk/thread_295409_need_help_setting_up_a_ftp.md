---
title: "need help setting up a ftp"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by harsh87 on 2006-11-08
i'm using ubuntu dapper and i got a lan connection.
i want to set a ftp so that other users can log on and browse my files and download them or upload.
can anyone help?

---

### Post by boban on 2006-11-08
Your question is very broad :) Try

```

sudo aptitude install gproftpd 

```

It's GUI for configuring [proftpd]("http://www.proftpd.org/") ftp server. I think I was able to configure everything from it... Install it, and try configuring - if you'll have problem - come back to ask :)

Check also [this thread]("http://ubuntuforums.org/showthread.php?t=79588&highlight=howto+ftp")

---

### Post by harsh87 on 2006-11-09
tahnx for ur help.
i was able to istall gproftpd by typing sudo install gproftpd proftpd
but i was not able to create users.
i tried it in secure way specified in vain.
i have a lan connection(no internet).
please anyone help me in configuring it in gui mode.

---

