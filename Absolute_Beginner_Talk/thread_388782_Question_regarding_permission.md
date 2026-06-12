---
title: "Question regarding permission"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by kenyi25 on 2007-03-19
Can a user in a particular group modify the contents in a dir which is belongs to his group,  but owned by root user?? :confused: 
The dir permission is: dwrxwrx-rx

---

### Post by simonn on 2007-03-19
If the group has write permissions (which it does in your example), yes.

---

### Post by kenyi25 on 2007-03-19
sorry i missed out this point,
what if the parent dir does not belong to the particular group??

---

### Post by carverj on 2007-03-19
hmm, but wouldn't that depend on whether the user was in the group: root ?
In his case, there is no write permission granted for others, and so assuming the user is not part of group: root, he will not be able to write to the contents of this directory.
Regarding the parent, same applies. The filesystem is heirarchical, so, if the owner  (say root) denied priveleges on the parent directory, this applies to any file (which also constitutes a directory in the world of unix) contained within.

---

### Post by simonn on 2007-03-19
> **carverj said:**
> hmm, but wouldn't that depend on whether the user was in the group: root ?
In his case, there is no write permission granted for others, and so assuming the user is not part of group: root, he will not be able to write to the contents of this directory.


"which is belongs to **his** group,"

> **carverj said:**
> 
Regarding the parent, same applies. The filesystem is heirarchical, so, if the owner  (say root) denied priveleges on the parent directory, this applies to any file (which also constitutes a directory in the world of unix) contained within.

This is not entirely true. 

If a user does not have write priviledges, but does have read priviledges on a parent dir {s,}he can still have any priviledges on sub dirs.

However, if the user does not have any priviledges to a parent dir, they will not be able to access any of the sub dirs (baring things like web servers, samba, NFS etc).

---

### Post by carverj on 2007-03-19
> 
Quote:
Originally Posted by carverj View Post
hmm, but wouldn't that depend on whether the user was in the group: root ?
In his case, there is no write permission granted for others, and so assuming the user is not part of group: root, he will not be able to write to the contents of this directory.
"which is belongs to his group,"

Which is belongs to his group.. I take it you mean he is in the group : root?
He hasn't specified whether his user in the group: root


> 
Quote:
Originally Posted by carverj View Post
Regarding the parent, same applies. The filesystem is heirarchical, so, if the owner (say root) denied priveleges on the parent directory, this applies to any file (which also constitutes a directory in the world of unix) contained within.
This is not entirely true.

If a user does not have write priviledges, but does have read priviledges on a parent dir {s,}he can still have any priviledges on sub dirs.

However, if the user does not have any priviledges to a parent dir, they will not be able to access any of the sub dirs (baring things like web servers, samba, NFS etc).

Interesting, my unix teacher is right, permissions are more difficult than ppl realise
:)

---

### Post by simonn on 2007-03-20
> **carverj said:**
> Which is belongs to his group.. I take it you mean he is in the group : root?
He hasn't specified whether his user in the group: root


The group "root"  is not mentioned. The only thing mentioned is that it is "his group". In ubuntu, by default, every physical user will also have a group with the same name that only they are a 
member of.

So from what kenyi25 has written I would assuem that the ownership is root:[user].

---

### Post by carverj on 2007-03-20
> So from what kenyi25 has written I would assuem that the ownership is root:[user].

Yes, what he is saying is that the directory is a system directory, unless he became super-user and made the directory that way.
What does root:[user] mean?

---

