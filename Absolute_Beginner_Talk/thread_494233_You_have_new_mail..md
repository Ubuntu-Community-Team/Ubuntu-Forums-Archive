---
title: "You have new mail."
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by gheywood on 2007-07-06
Just connected to my server via SSH, and got the following:

login as: greg
greg@192.168.1.13's password:
Linux vmhost 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
**You have new mail.**
Last login: Tue Jul  3 21:30:35 2007 from 192.168.1.10

I have obviously installed a mail server, but really don't know why it has received any mail, or how I can retrieve it :oops:

It is a server installation. Can anyone advise on how I can get it?

---

### Post by p_quarles on 2007-07-06
It's probably a welcome message, with how-to information. What mail server did you install? You can probably just type the name of the app and get right to it.

---

### Post by Raineer on 2007-07-06
Check in /var/mail/$USERNAME  (your user name)

It's just a text file with mail for you from Ubuntu, your own operating system leaves you notes!!!

It's practically never important so don't worry.

---

### Post by gheywood on 2007-07-06
Ah, just from rkhunter. Still, nice to feel wanted :)

Cheers for the info.

---

