---
title: "Missing Command To Run - On Login"
date: 2005-05-31
forum: Absolute Beginner Talk
---

### Post by rschlack on 2005-05-31
When I log in or boot up, I immediately get a message in a dialog box.  "Missing command to run".  How do I go about figuring out where this is coming from so I can fix it?  Is there a log I can look at?

Thanks in advance,
Rob

---

### Post by Gsibbery on 2005-06-01
[QUOTE=rschlack]When I log in or boot up, I immediately get a message in a dialog box.  "Missing command to run".  How do I go about figuring out where this is coming from so I can fix it?  Is there a log I can look at?

Thanks in advance,
Rob[/QUOTE]

Look in the /var/log directory and check your boot lof and messages files. Check your .bashrc file in your home drecotry as well as the /etc/profile files and see if there are any peculiar looking lines maybe making a call to a program that isn't installed.

---

### Post by rschlack on 2005-06-01
I figured it out.  All I needed to do was log out and choose Save Profile.  After I logged back in the message was gone.  Any idea why this worked?

---

### Post by DarthPedro on 2005-06-14
Hi,

I had same problem. gksudo was the problem. it wanted to start alone without any program!
Please, look in the ~/.gnome2/session file and this has follow lines?
5,Program=gksudo
5,CloneCommand=gksudo
5,RestartCommand=gksudo
at begin of every lines maybe is other(not 5).

  Pedro

---

