---
title: "Pine Help"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by jprb85 on 2007-03-23
I was finally able to set up Pine on my computer. The only problem is that it will not allow me to compose emails. Whenever I attempt to send an email It always says "Pipe can't access /usr/sbin/sendmail" no such file or directory. I went to /usr/sbin and could not find a sendmail but could find a pine .exe. When I tried to create a new folder in /usr/sbin Ubuntu would not let me do it. I would greatly appreciate if you could help me fix this problem so that I can start using Pine on my Ubuntu computer. 

Thank you.

:guitar:

---

### Post by taurus on 2007-03-23
Do you have sendmail on your machine?  What's the output of this command from a terminal?

```
locate sendmail
-or-
sudo find / -name sendmail -print
```

---

### Post by jprb85 on 2007-03-23
What I get after typing your command is.



jprblinux@jprblinux-desktop:~$ sudo find / -name sendmail -print
find: /proc/4642/task: No such file or directory
find: /proc/4642/fd: No such file or directory
jprblinux@jprblinux-desktop:~$ 


I do not think there is a sendmail file on my computer. 

Yet somehow I was able to install Pine and it runs and opens, just can't send mail.

---

### Post by devnulljp on 2007-03-23
Well, I'm impressed you got pine running. I gave up and went with mutt....
But, you have to install sendmail to be able to send mail. 

sudo apt-get install sendmail

should do it

---

### Post by jprb85 on 2007-03-23
I just did that but it still is giving me problems. Right after installing sendmail it gave me this message

Warning: 3 database(s) sources
        were not found, (but were created)
        please investigate.
Starting Mail Transport Agent: sendmail.


And whenever I boot Pine it says "incomplete maildomain in user-Destop"
"return address may be incorrect"

I have tried to send emails in pine but still does not work. I would appreciate any additional help.

Thank you.

---

### Post by andrew.46 on 2007-07-16
Hi,

 Saw your post:

> **devnulljp said:**
> Well, I'm impressed you got pine running. I gave up and went with mutt....
But, you have to install sendmail to be able to send mail. 

sudo apt-get install sendmail

should do it

 Sendmail is a little much in this setting. Try ssmtp instead.

                    Andrew

---

