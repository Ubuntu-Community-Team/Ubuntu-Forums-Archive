---
title: "Why does &quot;sudo: unable to lookup ThinkPad via gethostbyname()&quot; error mean?"
date: 2005-06-03
forum: Absolute Beginner Talk
---

### Post by john_walsh54 on 2005-06-03
I go into terminal and type these instructions as per ubuntuguide.org -

john@ThinkPad:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup 

This command returns the error:

sudo: unable to lookup ThinkPad via gethostbyname()
Password:postdrop: warning: unable to look up public/pickup: No such file or directory

Thinkpad was meant to be the "host name" but Ubuntu could not detect my network card. How do I fix this problem?

---

### Post by jcs296 on 2005-06-03
I'm having the same problem; during install the network configuration step failed and so I skipped that step. Set a hostname, finished install, booted up and got the same error. When I do google searches for the problem, I see lots of people having postfix problems with 'public/pickup', whatever it is.  I noticed postfix isn't starting properly on my system as well.  Any ideas?  Help! Until networking works, I can't use the computer for anything useful!

---

### Post by poofyhairguy on 2005-06-03
[QUOTE=john_walsh54]I go into terminal and type these instructions as per ubuntuguide.org -

john@ThinkPad:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup 

This command returns the error:

sudo: unable to lookup ThinkPad via gethostbyname()
Password:postdrop: warning: unable to look up public/pickup: No such file or directory

Thinkpad was meant to be the "host name" but Ubuntu could not detect my network card. How do I fix this problem?[/QUOTE]

This is all I can find:

[http://www.ubuntuforums.org/showthread.php?t=32573&highlight=public%2Fpickup](http://www.ubuntuforums.org/showthread.php?t=32573&highlight=public%2Fpickup)

---

### Post by poofyhairguy on 2005-06-04
Nice solution. I gave it its own thread to help others:

[http://www.ubuntuforums.org/showthread.php?t=39395](http://www.ubuntuforums.org/showthread.php?t=39395)

---

