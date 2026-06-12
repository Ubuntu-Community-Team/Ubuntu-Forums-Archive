---
title: "How to become User in Disk Group"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2007-02-25
Because of something else I'm doing, I need to become a member of the User Group named Disk.
This group is the owner of /dev/hda2 which is my WindowsXP partition.
However, the group DOES NOT show up in System>Administration>Users and Groups>Manage Groups although it DOES appear in /etc/group

Although, in /etc/group I am shown as a member of this group, when I type "groups" in terminal, the group Disk does not show up as one of which I am a member.

Further, the lack of access to the hda2 disk that I am seeking in the other task seems to confirm that I am indeed NOT a member of this group.

So what do I need to do to join this exclusive club?

Can anybody help?

---

### Post by Koybe on 2007-02-25
Did you try hitting 'Show all users and groups' checkbox in the System>Administration>Users and Groups ?

---

### Post by PaulFXH on 2007-02-25
Thanks, but I don't appear to have the checkbox to which you refer and I've looked everywhere.
Is there somewhere else I should be looking?

---

### Post by Koybe on 2007-02-25
I don't know... I'm using Dapper...

Anyway you can change it by editing your group file :
sudo gedit /etc/group

Go to the line with your Disk group :
```
disk:x:id:user
```
and add other users :
```
 disk:x:id:user,user2,user3,user4
```

etc...

---

### Post by PaulFXH on 2007-02-25
Thanks, but as I mentioned in my first post, I AM listed as a user of the group Disk in /etc/group.
However, when I type Groups in Terminal, Disk is NOT shown as one of the groups of which I am a user.
So, I'm puzzled.

After a reboot, however, everything is fine. Typing Groups now shows that Disk is one of my Groups.
Thanks for your help

---

### Post by jfsylvain on 2007-02-25
sudo adduser PaulFXH disk

---

### Post by jerremy-tamlin on 2008-05-17
I have both added myself to disk in /etc/group and when this didn't work I removed it and tryied ```
sudo adduser myusername disk
``` which returned success.

Neither of these flush the group privelages - which I assume is what is needed. Does anyone know how to do this so I don't have to restart my computer?

Cheers.

---

### Post by CatKiller on 2008-05-21
Logging out and logging back in refreshes group memberships.

---

### Post by jerremy-tamlin on 2008-05-25
Brilliant!

But then, logging out still requires me to close all programs I'm using. I guess if I studied the login process I'd see where it refreshes them. But has been several days now and computer has been restarted many times, so it's not so pressing at the moment.

---

