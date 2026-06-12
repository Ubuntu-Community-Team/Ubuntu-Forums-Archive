---
title: "modifying folder ownerships"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by Barticus on 2007-08-10
I thought I understood ownerships, but I guess I was wrong :)

I created a group called 'test' throught the GUI users and groups interface.

I created a folder in my home folder called 'test_folder' in the GUI file browser. As one would expect, both owner and group of this folder is myself.

When I try to modify the group of 'test_folder' to the group 'test', I get an Operation not permitted error.  Executing the same command with SUDO works fine.  Since this folder is in my home folder, and I am both owner and group of this folder, should I not be able to modify its permissions without using SUDO?

---

### Post by Dr Small on 2007-08-10
You should be able to change the directory owner without sudo, I guess, but why not just use sudo if you need too? It's not that hard...

Dr Small

---

### Post by 5-HT on 2007-08-10
If you are the owner of the file and a member of its group, you can modify its group so long as you are also a member of the group you are changing it to. If you add yourself as a member of 'test', you'd be able to change group ownership of 'test_folder' to 'test' as your user. You're exactly right about having permissions for the directory as it is, but also have to keep in mind whether you'd also have permissions after the group change. If not, you'd need to escalate privileges via sudo to make the change. There is a very good reason for this: if these restrictions were not in place, a user could change group membership of whatever file they have access to to a group they are not a member of--huge potential security risk.  Hope that made sense.

cheers,

---

### Post by Barticus on 2007-08-10
As I understand it, my end user wants a folder to store data in that remote users can access (through a web-based application he is developing) without needing accounts on the server.

---

### Post by 5-HT on 2007-08-10
> **Barticus said:**
> As I understand it, my end user wants a folder to store data in that remote users can access (through a web-based application he is developing) without needing accounts on the server.
No need to mess around with groups then, just make sure that the directory has the proper read/write/executre permissions for 'others' as desired.

---

