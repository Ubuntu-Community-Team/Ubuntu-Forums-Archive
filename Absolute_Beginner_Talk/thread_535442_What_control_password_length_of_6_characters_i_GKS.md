---
title: "What control password length of 6 characters i GKSU?"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by FJA on 2007-08-26
I'm new to buntu, and have by now made several 'default' installations.. mostly without problems - so THX for a great package!!!

However - I would like to change required pw length of 6 characters to 4 caharacters... Yes I know longer is better - but this is for purely internal use to prevent accidental users of making problems..

I've been searching and testing - and found a lot of hints for PAM. I also found 2 common-password files, and managed to edit in both.
In both min=4 is found, but still graphical user-admin demands 6 characters.. Found a post suggesting removing 'obscure' in parameters - done that, same problem - tried 'minlen'  - same problem.

...so - it seems the check is actually made by 'gksu user-admin' itself. Is this controllable by editing another configuration file - or what does this ??

Please help!

Frank

---

### Post by uclalinux on 2007-08-28
[http://www.linuxforums.org/forum/misc/1766-minimum-password-length.html](http://www.linuxforums.org/forum/misc/1766-minimum-password-length.html)
Think this will help

---

### Post by FJA on 2007-09-02
THX for the tip - just 'cracklib' is not default installed... I have posted a bug report..

---

