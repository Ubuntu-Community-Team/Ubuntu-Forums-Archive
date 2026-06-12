---
title: "mail at command line problem"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by rcmayfld on 2007-07-23
i type
mail [email]somebody@address.edu[/email]
cc: (enter cc)

type message

<cntrl D>


error message=
send-mail: fatal: open /etc/postfix/main.cf: No such file or directory
Can't send mail: sendmail process failed with error code 75

---

### Post by asmoore82 on 2007-07-23
to do these actions you must have an Email *_server_* installed and configured on that local machine.

(Actually you don't need a whole email server just the sendmail portion of it but you get the idea)

---

### Post by rcmayfld on 2007-07-24
how do i configure sendmail?

---

### Post by ReverendJ1 on 2007-07-24
Try this:
```
sudo dpkg-reconfigure postfix
```
that will let you configure it.

---

