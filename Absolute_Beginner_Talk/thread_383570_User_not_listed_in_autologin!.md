---
title: "User not listed in autologin!"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by Scorpuk on 2007-03-13
When I installed MythTV it created a user called mythtv.

I wanted to set that user as the autologin, but its not listed.

I tried adding the user to the gdm.conf-custom, but after a reboot the computer still sits at the login screen.

How can I set this user up so that its listed in the drop down list of users for autologin?


tnx in advance.

---

### Post by schwascore on 2007-03-13
Try going to System --> Administration --> Login Window

Click on the Users tab at the top right.

Un-check the check box and add the users you want to appear on the login screen to the column on the left.

That did it for me, hopefully it will solve your problem too.

---

### Post by majoridiot on 2007-03-16
> **Scorpuk said:**
> When I installed MythTV it created a user called mythtv.

I wanted to set that user as the autologin, but its not listed.

I tried adding the user to the gdm.conf-custom, but after a reboot the computer still sits at the login screen.

How can I set this user up so that its listed in the drop down list of users for autologin?


tnx in advance.

the mythtv user isn't technically a "user" per se... what you want to do is add your *main*
account to the mythtv group- which gives that user the needed privs for mythtv access.  in a
terminal do this (replacing USERNAME with your user):

```
# sudo usermod -a -G mythtv USERNAME
```

then you can add your main user to the autologin and do whatever else you wish. (you need
to log out and then back in for the group change to take effect).

as a note, you don't need an autologin if you are just wanting to start the backend- it starts
at boot by default. if you are wanting to add this to load the frontend, then just add your 
autologin for the main user and then put mythtvfrontend in your start settings for that
user in session manager.

---

### Post by Scorpuk on 2007-03-25
thank you soooo very much majoridiot that has helped me a great deal.


My box now switches on, logs in a user and starts mythfrontend in the event of a power failure. Once the power comes back on off course. :D

---

### Post by majoridiot on 2007-03-25
glad you got it working :)

---

