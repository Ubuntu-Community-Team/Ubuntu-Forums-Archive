---
title: "help changing user defaults"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by nater on 2008-01-22
how do I change the default settings for new users such as screen-saver and power settings?

I can login to each account and change the settings. Where do I go to change the settings for all users? or all new accounts.

Using desktop and setting accounts for each user, what I want to do is have a default value of 5 min until timeout and screen lockout for all users on the box.

tia
nater

I am new to administration of multi user setup. I can barely figure how to manage my own settings now I need to support others.

---

### Post by blueridgedog on 2008-01-24
You could experiment with /etc/skel by placing gnome configuration files from a user setup that you are satisfied with.  This will require some testing as it may not work as expected.

/etc/skel is where default files for new users are placed.

Take a look at:

[http://gentoo-wiki.com/GNOME_Admin_Guide_quick-n-dirty](http://gentoo-wiki.com/GNOME_Admin_Guide_quick-n-dirty)

or 

[http://www.google.com/search?source=ig&hl=en&rlz=1G1GGLQ_ENUS240&q=gnome+%2Fetc%2Fskel&btnG=Google+Search](http://www.google.com/search?source=ig&hl=en&rlz=1G1GGLQ_ENUS240&q=gnome+%2Fetc%2Fskel&btnG=Google+Search)

---

