---
title: "Is there a way to rename the Home Directory?"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by mollindz on 2007-07-12
I'm fairly new to Ubuntu (Feisty Fawn), and am really enjoying it.  I'm selling my current XP/Ubuntu computer and would like to include the existing Ubuntu installation for the buyer.  It's all set up with the Beryl Desktop and Firefox and Thunderbird Profiles that share with the Windows XP installation on the same computer.

My problem is, If I change the username and password for the new owner, I guess the user account still references the Home Directory in my name.  Can I changer the name of the home directory, or is that impossible?  I know it's a small thing, but I would like the new owners to have a personalized installation.

I tried creating a new account, but it didn't share any of the preferences ot my account (Startup programs, Desktop, Beryl, Firefox and Thunderbird Profiles, etc.).  Is there a way to create a new account that mirrors the original installation account?

I appreciate any help.

All the best,  Rob

---

### Post by pbaehr on 2007-07-12
Scroll down a little bit on this thread for instructions and discussion on renaming a user account:

[http://ubuntuforums.org/showthread.php?t=64021](http://ubuntuforums.org/showthread.php?t=64021)

Hopefully that will help you. They discuss some of the difficulties involved regarding programs.

(ignore the first response suggesting creating a new user)

---

### Post by annda on 2007-07-12
create the new user, transfer all the files from the original account and change their privileges to the new user. use sudo for that.

```
sudo chown -R newuser:newuser /home/newuser
```

then you can delete your home dir and your user. and make sure the new user is in the admin group!

UPDATE: i think the other post was smarter :-)

---

