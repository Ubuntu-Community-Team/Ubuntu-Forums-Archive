---
title: "Permission error copying files from a dvd."
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by enixon on 2007-01-24
I recently made the switch, replacing windows with ubuntu. Every thing seems to work fine except for a permission error I´m having. I can´t pull any of the back up data I burned to a dvd in windows before the switch. This includes my libary of mp3´s, movies, book marks, you get the picture. My computer reads the dvd and I can open it up but when I try to copy any of the files to my desktop it gives me the error, ¨"/media/cdr...any.de.URL" cannot be copied because you do not have permissions to read it.¨ I´ve set my self as the admin but still no luck. Also worth mentioning, I deleted the first default user account(not root, the other one) that ubuntu created after installation and replaced it with a new one, the one I´m currently using.I have no idea what so ever as to where to go from here.


Any help you guys can provide me would be greatly appreciated. This is becoming a head ache.

---

### Post by Tomosaur on 2007-01-24
Are you able to invoke the sudo command?

Generally speaking, you should at least be able to read the contents of the DVD - this leads me to thinking this is a problem with mounting the cdrom drive in the first place. If you are unable to use sudo, you may well need to go into recovery mode to sort your privileges out. Recovery mode logs you in as root automatically.

So anyway, try using sudo first (or invoking a program which requires root access). If it's successful, open up a terminal and type the following:
```

mkdir cd
sudo mount /dev/cdrom ./cd

```

This should mount the cdrom and allow you to see the contents.

---

### Post by pistcivet on 2007-01-24
Have you looked here yet:
Open "Users and Groups", choose your username then properties - User Privileges,
check all that apply.

---

### Post by enixon on 2007-01-26
Yes, I've tried giving my self admin permission. The problem is not that the dvd is not mounting, because I can see the contents of the dvd when I open the dvd icon. The problem is I don't have permission to copy any of the files on the dvd. I reinstalled ubuntu and that didn't fix the problem. Is it possible to restrict access to a dvd when you burn it?

---

