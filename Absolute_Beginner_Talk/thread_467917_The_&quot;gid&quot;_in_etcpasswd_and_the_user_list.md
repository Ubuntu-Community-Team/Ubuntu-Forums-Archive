---
title: "The &quot;gid&quot; in /etc/passwd and the user list in /etc/group"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by dupa on 2007-06-08
I have a question.
When i create a user, i can assign him a "primary group" id..
For example

I have "myuser" that have in /etc/passwd the reference to a specific gid, for example the numeric code for"mygroup".

In the /etc/group list, there are in the "mygroup" row all the users that belong to the "mygroup" group.

I noticed that sometime a user have a gid set in /etc/passwd, but the username isn't in the list for that group in /etc/group.

My question is:

Is there any difference to appear only in the gid of /etc/passwd or appear both in the gid of /etc/passwd and in the list of /etc/group?

Thanks

---

### Post by sandwitch on 2007-06-08
Correct me if im wrong
The gid in "/etc/passwd/" is the primary group a user belongs to. there will be no user add the end off the line. so in my case:
grep sandwitch /etc/group
sandwitch:x:1000:
grep sandwitch /etc/passwd
sandwitch:x:1000:1000:Yet Another Linux User,,,:/home/sandwitch:/bin/bash

so there is no user sandwitch noticeable added to the group sandwitch. but it his primary group so in fact he does exist.
confused?

---

### Post by dupa on 2007-06-08
> **sandwitch said:**
> Correct me if im wrong
The gid in "/etc/passwd/" is the primary group a user belongs to. there will be no user add the end off the line. so in my case:
grep sandwitch /etc/group
sandwitch:x:1000:
grep sandwitch /etc/passwd
sandwitch:x:1000:1000:Yet Another Linux User,,,:/home/sandwitch:/bin/bash

so there is no user sandwitch noticeable added to the group sandwitch. but it his primary group so in fact he does exist.
confused?

reallly the fact is that I don't want that groups with the same name of the user are created..

So if I have a user: "myuser", I don't want that the group "myuser" will be created too.

I create users using:

```
adduser --ingroup mygroup myuser
```

I noticed that sometime happens that I have a primary group set in /etc/passwd but that user belonging to that primary group, is not listed in the list of that group in the /etc/group

So i'm trying to understand what implies to belong to a group as a "primary group" but doesn't belonging to that group in the /etc/group file.

Thanks

---

### Post by sandwitch on 2007-06-08
only the secondary groups are mentioned in /etc/group primary groups are mentioned in /etc/passwd

---

