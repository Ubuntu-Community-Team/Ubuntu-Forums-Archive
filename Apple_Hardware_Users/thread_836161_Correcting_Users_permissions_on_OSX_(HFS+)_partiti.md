---
title: "Correcting /Users permissions on OSX (HFS+) partition."
date: 2008-06-21
forum: Apple Hardware Users
---

### Post by Boopop on 2008-06-21
Hi all,

   I've just installed Hardy Heron on my C2D Macbook, have most of my hardware configured, but I can't work out how to get access to my home folder in my OSX partition. I've added the partition to fstab, and in OSX, I've changed the folder's permissions for "Everyone" from no access to read and write, but then when I go back to Ubuntu, I still get access denied, due to incorrect permissions. 


   I've tried searching the net for help, but the only other thing that was suggested was editing my UID in Ubuntu to match that of the UID in OSX, but someone who tried it said that that broke his Ubuntu install as he then lost any permissions to access his whole Ubuntu filesystem! So I don't think I'll be trying that any time soon.

Any help would be greatly appreciated :)

Boopop

---

### Post by flaggh on 2008-06-21
The easiest way is to create a new user with the uid matching the user in OSX and use that account instead.

---

### Post by Boopop on 2008-06-21
Is there no easier way of doing it?

If not, how would I go about checking what UID my OSX user account uses, and then making sure the account I created in ubuntu was the same?

---

### Post by flaggh on 2008-06-21
changing the uid of your user is not trivial, but should not be too difficult if you follow through with the whole process.  If you do forget a step you could end up losing permissions.  There are plenty of posts covering this topic but make sure you understand the whole process before attempting it.

To check the uid of your OSX account, just type

```
id
```

in the terminal.  Usually the default is 501.

---

