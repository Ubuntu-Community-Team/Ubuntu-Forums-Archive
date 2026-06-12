---
title: "changing ownership"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by Bheegerji on 2007-12-15
$ sudo chown -R myusername:myusername /home/myusername/.*

I used this command to resolve a problem in Amarok. Rather than solving the problem, it created a new one. I have two user accounts on my Ubuntu. After executing this command the ownership of the secondary user has been transferred to my name i.e. superusers name. Now, the secondary user account is inaccessible. I get the gollowing error message when I try to acces the secondary account.

"User's $HOME/.dmrs file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."

"Your session lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of disk space. Try logging in with one of the failsafe sessions to see if you can fix this problem."

Plz help me fix this problem.

---

### Post by seventhc on 2007-12-15
not sure if this will work with your particular situation but you might try...
```
sudo nautilus
``` from here you can navigate to different folders and right click then go to properties and change permissions or add ownership.
Its probably not as fully functional as the command line, but I used it today and I got my desired results. So maybe you can change or give ownership back using nautilus.

also have a look at this link.

[http://ubuntuforums.org/showthread.php?t=631161](http://ubuntuforums.org/showthread.php?t=631161)

---

### Post by Bheegerji on 2007-12-15
thanks mate, that worked fine.

---

### Post by seventhc on 2007-12-15
Great :) which one worked?? nautilus or the link?? I'm curious in case I have the same problem someday ;)

---

### Post by Bheegerji on 2007-12-15
Sorry for being impatient. I marked this solved without checking. I tried the sudo nautilus command and changed the ownership of the secondary users directory. But still  getting the same error. Have I to reset the ownership of my home folder to root?

---

### Post by Bheegerji on 2007-12-15
"not able to open the file home/secondaryuser/.profile" thats the detail of the error message I get.

---

### Post by seventhc on 2007-12-15
maybe make sure it is set to read and write then click where it says apply permissions to enclosed folders.and go through the options you see there.

---

### Post by Bheegerji on 2007-12-15
Changed the ownership of my home folder to root. Still problem persists. Plz help

---

### Post by Bheegerji on 2007-12-15
> **seventhc said:**
> maybe make sure it is set to read and write then click where it says apply permissions to enclosed folders.and go through the options you see there.

No use. Let me try the command prompt.

---

### Post by benerivo on 2007-12-15
I don't think your home folder should be owned by root (unless you have specifically enabled the root account and log in as root). My home folder is owned by me, and the group ownership is me. I have read write permissions, and the 'group' and the 'other users' have access permissions.

---

### Post by seventhc on 2007-12-15
i wouldnt change it to root, you just want it how it was before.

---

### Post by benerivo on 2007-12-15
For a command line change use```
sudo chown -R yourusername /home/yourusername
```

---

### Post by Bheegerji on 2007-12-16
no use guys. still cant access the secondary user account.

---

### Post by Bheegerji on 2007-12-16
Well, found a low tech solution for my problem. 

Copied all contents of the secondary user to a removable medium, deleted the account and all related folders. And again created the secondary account and restored it with the contents.

If anyone does know any better solution then please do post.

---

