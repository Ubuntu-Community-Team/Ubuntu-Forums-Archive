---
title: "User account types and best practices for everyday use"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by i.am.canadian on 2006-11-19
I'm looking at setting up a Ubuntu system in a few weeks and I have been doing my research here on the boards and the online documentation (all of which is extraordinarily helpful by the way), but I still have a question.

I'd like to set my system up right the first time (as much as I possibly can anyway), so I'd like to know whether or not it is necessary to set up a second account with more restricted permissions for my everyday use?

My understanding is that Ubuntu creates an admin type account for you during set up, but is it safe to use this account on a day to day basis?  I also know that it is not a root account as in other distros, but I also know that in OS X the advice is to create a standard user account for your daily use, even though the administrator group is not technically root either.

Anyway, any advice would be much appreciated and I look forward to being more involved in this community once I get my system up and running.  Cheers all.

---

### Post by aysiu on 2006-11-19
The *admin* group has the ability to temporarily assume root privileges for a command by prefacing it with the word *sudo* and entering a password. Another password doesn't have to be entered for another fifteen minutes.

You can change the timeout to some other time limit (two minutes, 0 minutes), and you can change what commands certain *sudoers* have access to with root privileges. You can also remove people from the *admin* group altogether.

In other words, you have total control over who gets what privileges. And if you accidentally remove *admin* from all users, you can [boot into recovery mode and fix that.](http://www.psychocats.net/ubuntu/sudo)

---

### Post by nalmeth on 2006-11-19
If it's just you using the computer, then the default scheme will be fine.

the "sudo" command gives you administration rights for your user. Unless you are running any apps with sudo, they will run as your regular user, which doesn't have permissions to directories outside /home/username and /tmp.

You can go ahead and create a /root user, but this is not neccessary.

---

### Post by i.am.canadian on 2006-11-19
Thanks a lot for the prompt responses.  Sounds like what I needed to know, I can't wait to get started. :)  Cheers.

---

