---
title: "How to Permissions, join group"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by bdemers on 2007-03-12
Hi,

I need to learn how to make a user join a group.  I then need to make on group join another.

I see people using PAM to do this

---

### Post by bernied on 2007-03-12
The file /etc/group controls which users are in which group. There are several apps that modify this file, such as groupadd, useradd. I prefer to modify the file directly.

To add a user to a group add the username at the end of the line. If there is a name already at the end of the line, put a comma then the new name (no space), if there is a colon, then simply add the new name (no space).

To make one grou join another - I'm not sure what you mean by this, maybe you mean add all of the users in group1 to group2. Then simply copy all the names next to group1 and put them at the end of the line for group2.

To make a new group, use groupadd.

To find out more, use man, eg:
```
man group
```

---

### Post by bernied on 2007-03-12
I should have said, changes to the /etc/group file will not take effect until the user logs in again.

Is this homework?

---

### Post by bdemers on 2007-03-14
No, this isn't homework.  I have a group of kids logging into Win 2003 from Edubuntu workstations.  Running on a win 2003 terminal server is an interactive app that requires audio to work properly.  The kids log onto the windows ad, runs a remote session of the app from the Edubuntu workstation.  The kids use headphones plugged in locally for the audio.  Audio has been enabled at the win 2003 term server.

So far all is ok except that the sound is not working when user is a domain user, but is if user is logged in only locally(obviously this is not a remote session in this instance).  Figure this is a rights issue and so wanted to make the domain users have the same permissions as a local user.

---

