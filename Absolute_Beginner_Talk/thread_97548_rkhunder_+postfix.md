---
title: "rkhunder +postfix"
date: 2005-12-01
forum: Absolute Beginner Talk
---

### Post by [pl]ice on 2005-12-01
um, how come i need postfix on my box for rkhunter? and no i haven't researched more... busy :(    is it just for remote mailing/reportin?

can i go around it etc?

thanks

---

### Post by MartinG on 2005-12-01
It is necessary in order for you to get rkhunter's reports delivered to your mailbox (/var/mail/..).  It is quite safe to use, as the default configuration restricts its activities to localhost.

---

### Post by [pl]ice on 2005-12-01
hey, so if i'll configure postfix,on the startup just for localmachine, to i have to do anything else to secure it? any ports/procedures etc to disable?
thanks.

---

### Post by MartinG on 2005-12-02
Nothing as far as I know ... I just installed the default and left it. A check with Nessus showed everything was still secure.  Oh, and I set up my mail (KMail) to collect system messages from /var/mail.  

One thing you may like to note in advance. RKHunter's daily report complains about the following, but elsewhere in the forums you'll find experts saying, "Don't worry, ignore it".

WARNING, found:  /dev/.static (directory)  /dev/.udevdb (directory)

[QUOTE='[pl]ice']hey, so if i'll configure postfix,on the startup just for localmachine, to i have to do anything else to secure it? any ports/procedures etc to disable?
thanks.[/QUOTE]

---

