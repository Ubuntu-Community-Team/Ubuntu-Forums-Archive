---
title: "Dapper to Edgy Update...HOW? Not Working?"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by keef247 on 2007-03-24
trying to use this method
[http://blog.mypapit.net/2006/10/howto-upgrade-ubuntu-dapper-to-edgy-eft.html](http://blog.mypapit.net/2006/10/howto-upgrade-ubuntu-dapper-to-edgy-eft.html)
and this one
[http://www.debianadmin.com/upgrade-ubuntu-dapper-to-ubuntu-edgy-eft.html](http://www.debianadmin.com/upgrade-ubuntu-dapper-to-ubuntu-edgy-eft.html)
and neither do anything but give me errors.
on the second link i cant even get up the software update gui thing...

how do i do it in terminal please or GUI preferably...
links or commands please!
so far i get:
dave@pc:~$ sudo sed -e &#8217;s/\sdapper/ edgy/g&#8217; -i /etc/apt/sources.list
Password:
sed: -e expression #1, char 1: unknown command: `

so i don't know whats going on.
I'm currently on 6.0.6...
cheers

EDIT: might be working now trying "update-manager -c"

---

### Post by machoo02 on 2007-03-24
the 'upgrade-manager' method is the recommended method to move between releases.

---

### Post by Barber on 2007-03-25
I still got an error saying it couldn't install something (47th out of 48). Can't remember exactly what now - not helpful, I know. I'll try and find out soon, but if you've got any idea why it might not be able to retrieve certain files when updating (via update manager) to edgy, please let me know.

---

### Post by machoo02 on 2007-03-25
Hmm...perhaps one of the repos was down or you lost a connection.  It happens sometimes.  You could try re-running update manager to see if it fixes the problem.

---

