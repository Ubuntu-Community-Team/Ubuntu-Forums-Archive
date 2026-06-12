---
title: "/etc/init.d/sendmail reload?"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by joemacnz on 2006-10-15
G'day all,
           everytime I boot up dapper I get this message:

          /etc/init.d/sendmail reload

I then run this in the terminal and all is well untill I reboot and it tells me to do it again.How can I fix this. As far as I know I don't use "sendmail" although I couldn't send an automatic bugreport because I didn't have it so I tried, unsuccesfully to install it.Can anyone help?
Cheers.

---

### Post by sands on 2006-10-29
same problem for me too..

---

### Post by joemacnz on 2006-11-01
I have tried installing, uninstalling and back again to no avail. Any help?

---

### Post by stimpyaw on 2007-02-01
I'm having the same problem:

          /etc/init.d/sendmail reload

and when I attempt the reload it just tells me to do it again too.  I also installed **sendmail** so I could send a **Bug Buddy** report.  But **sendmail** installed with no problems and **Bug Buddy** was able to send the report.

---

### Post by l951b951 on 2007-02-03
I installed sendmail to do a bug buddy report.  I kept getting the same boot error.  I visited this forum post:
[http://www.ubuntuforums.org/showthread.php?t=270925&highlight=etc%2Finit.d%2Fsendmail+reload](http://www.ubuntuforums.org/showthread.php?t=270925&highlight=etc%2Finit.d%2Fsendmail+reload)

The last piece of advice is to install Postfix.  I did that, booted and sendmail (and it's error) are now gone.

---

### Post by stimpyaw on 2007-02-04
thanks for the link, the Postfix worked and the sendmail error is now gone. thanks!

---

### Post by Howlin' Hobbit on 2007-06-02
I searched the forums because I was getting that message too, even though I'd gone into the "Services" part of my Admin menu and told it not to start. All I wanted it for was to test the occasional php script I write for my site that needs to send mail.

Postfix worked like a champ. Didn't have to configure squat. PHP found it and it worked. Sendmail, sendmail's error (and the major slowdown to my bootup sequence) are gone.

Thank you *very* much, all who posted here!

---

