---
title: "mail command not working? or is it?"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by mickeyren on 2008-02-02
Hi,

I just availed a dedicated linux ubuntu server. so far i can see that an smtp server is installed by doing telnet localhost 25.

then at first i tried to use the mail ocmmand but it says mail command not found so i installed mailx, this seems to be the package that will make the mail command work.

so now i tried to send an email via the mail command so i did this

mail [email]myemailad@somdomain.com[/email]

system asked for subject. i hit enter
then shows up a blank line. I type in some, then enter, then "." then enter
then asks for CC, i hit enter. then i went back to the command prompt.

didn't receive any emails, and the mail function on php doesn't work either, although therew as no error.

what am i missing here? i don't have a domain name yet pointed to my dedicated server, so maybe that's one of the reason? do ii need a domain name pointed to my server?

thanks in advance.

---

### Post by dcstar on 2008-02-02
> **mickeyren said:**
> Hi,

I just availed a dedicated linux ubuntu server. so far i can see that an smtp server is installed by doing telnet localhost 25.

then at first i tried to use the mail ocmmand but it says mail command not found so i installed mailx, this seems to be the package that will make the mail command work.

so now i tried to send an email via the mail command so i did this

mail [email]myemailad@somdomain.com[/email]

system asked for subject. i hit enter
then shows up a blank line. I type in some, then enter, then "." then enter
then asks for CC, i hit enter. then i went back to the command prompt.

didn't receive any emails, and the mail function on php doesn't work either, although therew as no error.

what am i missing here? i don't have a domain name yet pointed to my dedicated server, so maybe that's one of the reason? do ii need a domain name pointed to my server?

thanks in advance.

Look in your /var/log directory and examine the mail logs.

---

### Post by mickeyren on 2008-02-02
hi,

thanks for helping out but apparently its empty:

-rw-r--r-- 1 root        root       0 2007-05-16 08:40 mail.err
-rw-r--r-- 1 root        root       0 2007-05-16 08:40 mail.info
-rw-r--r-- 1 root        root       0 2007-05-16 08:40 mail.log
-rw-r--r-- 1 root        root       0 2007-05-16 08:40 mail.warn

---

### Post by dcstar on 2008-02-02
> **mickeyren said:**
> hi,

thanks for helping out but apparently its empty:

-rw-r--r-- 1 root        root       0 2007-05-16 08:40 mail.err
-rw-r--r-- 1 root        root       0 2007-05-16 08:40 mail.info
-rw-r--r-- 1 root        root       0 2007-05-16 08:40 mail.log
-rw-r--r-- 1 root        root       0 2007-05-16 08:40 mail.warn

Then you apparently do not have a MTA running.

You should have postfix or sendmail installed and configured (I prefer postfix).

---

