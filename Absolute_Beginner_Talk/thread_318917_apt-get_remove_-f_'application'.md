---
title: "apt-get remove -f 'application'"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by kpm on 2006-12-14
Hi, I just installed Bugzilla using apt-get but want to remove it and reinstall the latest stable with dpkg rather than apt-get.  I tried using apt-get remove -f bugzilla to get rid of it all but noticed when I searched for bugzilla with 'locate bugzilla', well I still had lots of bugzilla directories scattered throughout.  So I tried sudo dpkg -P bugzilla which got rid of the configuration files, but still have all those bugzilla directories in /var/lib/bugzilla.  I suppose I could sudo rmdir -r /var/lib/bugzilla but for one, I am not sure I want to do that, if apt left them there, maybe it was for a reason, and two, I am going to be reinstalling with the .tar, are dependencies and such going to be in the /var/lib/bugzilla directory??

thanks

---

### Post by charles.g.moore on 2006-12-14
This is kinda off topic but check this out, one of the local forum staff here pointed me to it
[http://ubuntuforums.org/showthread.php?t=37736](http://ubuntuforums.org/showthread.php?t=37736)

---

### Post by kpm on 2006-12-14
> **charles.g.moore said:**
> This is kinda off topic but check this out, one of the local forum staff here pointed me to it
[http://ubuntuforums.org/showthread.php?t=37736](http://ubuntuforums.org/showthread.php?t=37736)

Thanks for the link, will come in handy.  Though I thought apt-get managed dependencies as well??

---

### Post by nickburns on 2006-12-14
try:

sudo apt-get --remove bugzilla

this should clean up all the stuff that it created.

---

