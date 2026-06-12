---
title: "Access Ubuntu disk from WinXP across network"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by Frex on 2007-02-12
Hi,

I recently installed dapper drake on a pc, and since I already had Windows installed on this computer, I made it a dual boot system with an FAT32 partition for my files.

Now, I would like to find this computer on a Windows network, while it is running Ubuntu. 

That is, computer X is part of a Windows network, and computer Y has got Ubuntu installed and running. How can I access the FAT32 partition on computer Y from computer X?

---

### Post by apollo13 on 2007-02-12
One way would be Samba, go to System->Administration->Shared Folders and you are up and running...

apollo13

---

### Post by Frex on 2007-02-12
Thanks for your reply.

Ok, now I find my shared folder in network directory, but now I'm prompted for a password. Which password do I have to use?

---

### Post by apollo13 on 2007-02-12
Unix user and password, if it does not work try root...

---

### Post by Frex on 2007-02-12
Still can't get in; the login box keeps appearing...

---

### Post by apollo13 on 2007-02-12
try:
```
smbpasswd -a YOURUSERNAME
```
It will prompt you for a password, enter what you like, it even can differ from your Unix password, ah and YOURUSERNAME has to be a valid Unix user (not a Wind00$user)

The new entered password should work (this doesn't change your Unix login information, only samba...), alternative would be turning guest ok on (through /usr/local/samba/etc/smb.conf, at least if doing it manually)

---

### Post by Frex on 2007-02-12
It works! Thanks a bunch!:guitar:

---

