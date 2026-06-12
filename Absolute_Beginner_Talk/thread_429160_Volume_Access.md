---
title: "Volume Access"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-04-30
There are four users.  Two volumes.  Only one user needs access to the second volume.  It should be protected from access by the other users.

I understand that any users home directory is private to that user.  Would a simple solution to protecting the second volume be  to make that volume the users home directory (System / Administration / Users and Groups - change profile)?

---

### Post by starcraft.man on 2007-05-01
I'm confused, why do you need to prevent the 3 other users from modifying the "second" volume? and what exactly do you mean by "second" volume? Are you talking about audio volume?

---

### Post by expatCM on 2007-05-01
The second volume is another hard drive which contains all the personal data to one user.  It is a hierarchy of directories.  It should not be accessed by anyone else.

---

### Post by starcraft.man on 2007-05-01
> **expatCM said:**
> The second volume is another hard drive which contains all the personal data to one user.  It is a hierarchy of directories.  It should not be accessed by anyone else.

AHH, ok... sorry, I guess I'm a bit sleepy, going soon. Well, seems pretty simple. Just create a new user group named limited and make it only access certain partitions.

To create and modify user groups.

```
System > Administration > Users and Groups
```

To modify the permissions of a folder or partition right click on the desired folder (say your separate partition), click on properties and go to the "permissions" tab. Then you have many options to limit the selected folder/driver/whatever.

That should do it, have fun :)

If your doing that btw, I'd make seperate partitions on the actual hard drive say, /home/user1. Then you can make it as big or as small as you want and it can be entirely isolated from any other part of your OS :)

---

### Post by expatCM on 2007-05-01
This did not quite work out ... think I did not quite understand something ... sorry ...

What I did was go to Users and Groups and created a new group.  I then added the user who wishes to protect their data to that group.

Then I opened gnome commander using su.   Found the volume and right clicked.  Into properties and permissions.  Here I tried to change the owner and the group.  I tried to change the owner from root to the user and change the group from root to the new group.

Sadly a message came back Operation Not Permitted.   I then tried to make the changes one at a time but the same message was returned.  What did I miss?

---

### Post by expatCM on 2007-05-01
It seems that there is quite a bit to this ... the following link partly sets it out
[https://help.ubuntu.com/community/VolumePermissions](https://help.ubuntu.com/community/VolumePermissions)

The article appears to be in progress.  I do not understand what settings to make to change the permissions of a FAT32 drive so that it is accessible by only a specific user or group.  Does anyone know?

---

