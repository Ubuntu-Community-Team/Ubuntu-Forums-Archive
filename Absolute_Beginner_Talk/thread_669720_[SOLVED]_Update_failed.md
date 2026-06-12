---
title: "[SOLVED] Update failed"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by arvevans on 2008-01-16
Error in automated update process:
[INDENT]
E: xcwcp: subprocess post-installation script returned error exit status 10

[IMG]http://arvid.evans.googlepages.com/temp_stuff[/IMG][/INDENT]

Should I be worried about this?

Arv
_._

---

### Post by aysiu on 2008-01-16
Maybe [one of these might help?](http://www.google.com/search?hl=en&q=xcwcp%3A+subprocess+post-installation+script+returned+error+exit+status&btnG=Google+Search)

---

### Post by arvevans on 2008-01-17
Tried this:

[INDENT]sudo rm /var/lib/dpkg/lock
sudo rm /var/cache/apt/archives/lock
sudo dpkg --configure -a
-> read the output, you will have to answer a few questions
sudo dpkg --configure --pending[/INDENT]

No help.  xcwcp is till exiting with error 10.

[INDENT]arv@arv-desktop:~$ sudo dpkg --configure -a
Setting up xcwcp (2.3-6) ...
dpkg: error processing xcwcp (--configure):
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 xcwcp
arv@arv-desktop:~$ 
[/INDENT]

OK, I give up.  This fixed it:

[INDENT]arv@arv-desktop:~$ apt-get remove xcwcp
[/INDENT]

Arv
_._

---

