---
title: "Turning off mail delivery reports"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by wsanders1 on 2008-01-10
I am trying to reverse engineer a Ubuntu server someone else configured on which email was broken, now it is working, but postfix (?? - well, it wasn't the default behavior for Postfox last time I checked) is putting a "mail delivery report" in nobody's mail inbox every time a message is successfully sent.

Postfix is installed and working more or less that way I want except for this unnecessary mail to nobody. I am an experienced postfix and sendmail administrator. 

I can't find a sendmail.cf file anywhere or an option to control this in postfix anywhere.. Is there any way to turn off this behavior?

Thanks,

wsanders1

---

### Post by Blutack on 2008-01-10
Might have some more luck here:
[http://ubuntuforums.org/forumdisplay.php?f=7](http://ubuntuforums.org/forumdisplay.php?f=7)

---

### Post by wsanders1 on 2008-01-10
Thanks, turns out this IS default postfix behavior when -v is included on the sendmail command line. Annoying. Have to go grovel around in php.ini files and the like to find out where someone put the -v flag in the sendmail command.

-w

---

