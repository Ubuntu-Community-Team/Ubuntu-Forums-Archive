---
title: "You have mail. Where??"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by mahy on 2007-02-15
When i log into my Ubuntu via console, it tells me i'd got mail. However, when i type 'mail' to read it (just like i do on a FreeBSD), bash tells me there's no such program. What do i have to install? thanks

---

### Post by louis_nichols on 2007-02-15
Youcan check your mail with the cat command. You just use the command on the path it gives you when it reports you have mail.

---

### Post by Stephen Howard on 2007-02-15
Linux distros don't install a bsd-mail equivalent by default.  That said, you can install it if you want, but I don't know who maintains it for Ubuntu, so you will need to do some searching.

Linux common command line mail programs include mutt, pine etc.  [Here's a list.]("http://www.faqs.org/docs/Linux-HOWTO/Mail-User-HOWTO.html#mua")

---

### Post by argie on 2007-02-15
I may have installed this some time along the line. But just typing:

```
mail
```

at the console is enough to get a program that reads the stuff in /var/mail/username except I've got one misconfigured script in the crontab and it's gone and sent 6000 odd messages

```
"/var/mail/george": 6421 messages 6421 unread
>U  1 root@localhost.lo  Mon Jan 15 00:25   19/676   Cron <george@roshan> None
 U  2 root@localhost.lo  Mon Jan 15 00:26   19/676   Cron <george@roshan> None
 U  3 root@localhost.lo  Mon Jan 15 00:27   19/676   Cron <george@roshan> None
 U  4 root@localhost.lo  Mon Jan 15 00:28   19/676   Cron <george@roshan> None
....

```
Heh.

---

### Post by Aberrix on 2007-02-15
I've run into problems using PINE, it says I have mail but when I check it there is nothing there...

mutt, on the other hand has worked flawlessly. no complaints.

---

### Post by dlehman on 2007-02-15
If you want to just check the mail and if you don't need it to be from the console start up evolution or what ever mail client you prefer.  

add a mail account type of mbox and point it to ```
var/mail/username
```
then you should get your mail

good luck

---

### Post by mahy on 2007-02-15
the last post helped me, thanks. Now i know where the system mail resides.

---

