---
title: "Different users"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by Bruce2 on 2007-12-20
How would I transfer folders from one user to another on my computer using ubuntu? Is there an easy way to do this?

If the answer is copy it to a disk how do i do that? I am very computer illiterate....lol

---

### Post by PmDematagoda on 2007-12-20
The files of the users of Ubuntu are based at the /home directory. So if you just move a directory up from your own Home folder, you should be able to see those of the other users.

---

### Post by Inxsible on 2007-12-20
> **PmDematagoda said:**
> The files of the users of Ubuntu are based at the /home directory. So if you just move a directory up from your own Home folder, you should be able to see those of the other users.But you wont have access to them unless you are an admin on the machine !!

---

### Post by hyper_ch on 2007-12-20
and once transferred they also need to be chowned to the new user... you could however setup a sepearte share folder into which all users have read/write access.

---

### Post by rkd on 2007-12-20
Do you want to set things up so that both users have access to a group of files?  Or do you want to take a group of files that one user currently has and move them over to another user so that the first user no longer has access to them?  Or do you mean some third thing that I haven't mentioned?  Are the files in question already gathered together in one subdirectory or are they mixed in with files that you don't want to change?

Let us know in a little more detail just what you want to accomplish and we can give you precise directions on what to do.

---

### Post by The Cog on 2007-12-20
Perhaps the easiest way is to have userA copy his files to the /temp directory, then let userB copy them, then have userA delete the temporary copies again.

Otherwise, you can make userB a member of userA's group, in which case userB is allowed to read userAs files (and copy them) directly.

---

