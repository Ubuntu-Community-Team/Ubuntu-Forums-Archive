---
title: "[SOLVED] Big Problem - I think I don't have a root account"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by arjayes on 2007-11-28
While following a howto on a site . I didn't follow the instructions carefully enough .
 I was creating a new group to edit a bunch of files . While adding my account to that group 
I used this command 
                usermod -G <name of the new group> <current user name>
I didn't read that I was supposed to add all the current groups that user belonged to along with the new group.
unfortunately that was the only administrator account .  So is there any thing i can do to restore administrative status to my current account .
thanks

---

### Post by Dr Small on 2007-11-28
Boot into recovery mode from the GRUB menu and you will be logged in as root.
You can run your command there, to restore admin to your only account.

Dr Small

---

### Post by bodhi.zazen on 2007-11-28
When you boot to recovery mode it may be easiest to directly edit /etc/groups.

[indent]* Just my 2c as I think it is actually just as easy to directly edit /etc/groups ....

```
nano -B /etc/group
```

The -B flag makes a backup :)

Add you user to admin and any other group you might want, ie groups, audio, video, you user ....

Add you user at the end of the various lines, comma delineated.

Reboot

---

