---
title: "'groups' and 'users'"
date: 2006-05-24
forum: Absolute Beginner Talk
---

### Post by Rinzwind on 2006-05-24
I can view what user belongs to what group with:

**groups rinzwind** 

But can I also see from the user the members of the group the user is in? 

So in case I didn't explain myself perfectly: 

I want to know the users of the group rinzwind is in.

---

### Post by Sef on 2006-05-24
So you want to know this:

In groups rinzwind, you can see who are the users, and you want to be able to know what other groups they are in, correct?

---

### Post by mostwanted on 2006-05-24
I'm not sure of any cmd-line alternatives but there is a graphical program for viewing/setting up groups and users in System &#8594; Administration.

---

### Post by Arndt on 2006-05-24
[QUOTE=Rinzwind]I can view what user belongs to what group with:

**groups rinzwind** 

But can I also see from the user the members of the group the user is in? 

So in case I didn't explain myself perfectly: 

I want to know the users of the group rinzwind is in.[/QUOTE]

The group information is in the file /etc/group, which has a fairly straightforward format (see "man group"). I don't know if there is any command to do what you want. Note that a user may be present in more than one group.

---

