---
title: "password protect"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by jdm2 on 2006-09-19
I was wondering if there was a way to passowrd protect a folder.  What I wanted was when that folder was click a pop up would come up and ask for a passowrd no matter what user that was for.  If that's not possible how could I set it up for only a certain user and not root could access it.  Thanks for the help.  

P.S. Does anybody know of a program that would let me play go on linux and if you do how would I get it and install it.  Thanks

---

### Post by Brunellus on 2006-09-19
root accesses everything.  if he can't, he's not root.

otherwise, you can set ownership and permissions on the directory to restrict access only to the owner.

---

### Post by jdm2 on 2006-09-19
I read if I set the permission to 700 only that user could access it.  Is that correct?  Thanks

---

### Post by Brunellus on 2006-09-19
yup, that's right.  make sure that no other user or pseudouser NEEDS it before you wall it off, though.  chmoding your system files into inaccessibility would be a bad idea.

---

### Post by jdm2 on 2006-09-19
It's just my documentsand I don't want guest to run sudo and be able to access it.  So I was just planing on making an account for them.

---

### Post by Brunellus on 2006-09-19
only the first created user account is added to the sudoers file.  Nobody else gets to be a sudoer unless the first user adds them explicitly.

If your files are in ~/ then you should be OK.

---

### Post by jdm2 on 2006-09-19
Thanks for the help.

---

