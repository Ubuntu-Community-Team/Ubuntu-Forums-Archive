---
title: "What are the permissions/ownership of the /home directory?"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by ComplexNumber on 2006-12-23
i've somehow locked myself out of my home directory. the only reason why i can post this is because i temporarily made the owner and group of my /home directory to be me. i would have thought that the owner and group would have been root, but when i set it to be root and then log in from the login screen(ie GDM), it tells me that it can't find my user directory(ie bassist). when i change the ownership of the /home directory to be me, i can login fine. 

btw to change the ownership, i'm having to login as root .

can anyone please tell me what the group and owner of the /home directory is meant to be? also, if you fire up the terminal, cd to /, then type in "ls -l", what does it give you for the permissions of the /home directory?

much appreciated.

---

### Post by Bachstelze on 2006-12-23
By default, group and owner of your home folder is you and perms are 755.

---

### Post by ComplexNumber on 2006-12-23
> **HymnToLife said:**
> By default, group and owner of your home folder is you and perms are 755.
just to clarify, i'm not talking about my own home directory(ie /home/bassist), i'm talking about the ownership(ie owner and group) of /home. surely when there are several different users, the owner can't be me.
thanks for the reply.

---

### Post by Bachstelze on 2006-12-23
root:root then, perms to 755 also.

---

### Post by ComplexNumber on 2006-12-23
> **HymnToLife said:**
> root:root then, perms to 755 also.
i'm an idiot. your right. thank you :). i owe you one :). i thought i'd tried everything. i kinda knew that the owner and group must be root, but when i set both to root, it wouldn't let me in. it seems like it was the permssions to blame, even though i set the owner and group to "create and delete files"(ie rwx).

---

