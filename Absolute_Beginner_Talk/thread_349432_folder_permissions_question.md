---
title: "folder permissions question"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by JohnnyAvocado on 2007-01-30
I have a question from yesterday that I realized wasn't specific to ftp permissions. The question is this...

If I have folders in the /home dir, how can I allow user3 to have access to user2 and user4 without making them part of the same group. I am looking for the windows equivilant of right clicking and just granting user3 permission to whichever folder they need access to.

users/folders:
user1 - just access to user1
user2 - just access to user2
user3 - access to user3,user2 and user4
user4 - access to user4

Would I somehow use chmod to grant user3 access to user2 and user4? I have all the users locked down to their own folder. Just don't know how to grant a specific user access to a specific folder.

I am using dapper drake server. 

Thanks so much for any help.

Johnny

---

### Post by ComplexNumber on 2007-01-30
create a group where they can have access, then change the permissions so that that group can have access. note that any user can be part of more than 1 group.

---

### Post by JohnnyAvocado on 2007-01-30
Thanks very much for the info. I understand what needs to be done. Just to clarify though, since it is only a one off situation, is there no way to say that people only in group 'X' have access with the exception of this one person who also has access? I would prefer that method to keep things more straight forward.

Thanks again.

---

### Post by ComplexNumber on 2007-01-30
> is there no way to say that people only in group 'X' have access with the exception of this one person who also has access?
i'm not too sure of the finer details. i don't think there is the facility to exclude a member from a group, just the facility to not include a member from a group.

---

### Post by JohnnyAvocado on 2007-01-30
I finally got it all straightened out. Thanks so much for the help.

I added the lone user to all of the other groups by doing a 

```
sudo nano /etc/group
```

Everything is working great now. That worked just fine. 

Thanks again.

---

