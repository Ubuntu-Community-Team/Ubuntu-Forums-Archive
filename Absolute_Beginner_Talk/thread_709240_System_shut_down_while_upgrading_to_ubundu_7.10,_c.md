---
title: "System shut down while upgrading to ubundu 7.10, could not login after restart"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by somangili on 2008-02-27
I was upgrading to 7.10 from 7.04 in my office computer. It took a lot of time and when I was out someone shut down my computer. When I restarted I could not login.  After entering password a blank olive colour scree appears with the cursor. When I changed the session to gnome fail safe I could login. But I could not connect to the internet and could not start the update manager. Can anyone help.

---

### Post by TheDilettante on 2008-02-27
At first blush, I'd ask if you can save your personal data onto another disk and simply install Gutsy fresh - that you had no GUI login sounds like the install didn't finish.  Have an external drive?

---

### Post by sryth on 2008-02-27
Sorry to say, but you're probably looking at a re-install.  I'd find whoever shut off your machine and have some serious words with them at the least, linux doesn't like being turned off that way, especially not in the middle of a major operation.

Back up any important data files.

Then get a list of installed packages.

dpkg --get-selections | grep -v deinstall > installed-software

^^^will give you a file named installed-software in your current directory that has a list of all packages you installed with apt.  Put this with your backed up data files.

Once you have a clean install up, and updated.

dpkg --set-selections < installed-software

^^^ Will re-install the packages you had before.   Or you can read the file and install them manually if you want to pick and choose.

Wouldn't take very long really.


I'd still find that person though. :)

---

### Post by somangili on 2008-02-29
Thanks everybody who replied my post.  As suggested I had no other way but to reinstall ubundu7.10 with a live CD.  Now I am happy the problem is over. Thanks.

---

