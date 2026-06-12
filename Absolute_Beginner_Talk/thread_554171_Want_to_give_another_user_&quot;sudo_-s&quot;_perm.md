---
title: "Want to give another user &quot;sudo -s&quot; permission how do I do that?"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-09-18
How do I make my new user account ( sysadmin : sysadmin ) belong to the
117( admin ) group?

---

### Post by jamvegan on 2007-09-18
System->Administration->Users and Groups, select the user, click Properties, go to User Privileges tab, check Administer the System.

Or, edit /etc/group (always a good idea to make a backup first when manually editing system config files) and add the username, after a comma, to the end of the admin line.

---

### Post by jingo811 on 2007-09-19
Tnx that was waay simpler than doing all that "visudo" business from an older thread
[http://ubuntuforums.org/showthread.php?t=1880](http://ubuntuforums.org/showthread.php?t=1880)

**[ SOLVED ]**

---

### Post by jamvegan on 2007-09-19
Oh, yeah.  That seems to have been written when the admin group solution didn't even exist!  Glad to help. :-)

---

