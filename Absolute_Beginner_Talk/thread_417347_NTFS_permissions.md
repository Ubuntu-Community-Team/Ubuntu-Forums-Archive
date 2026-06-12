---
title: "NTFS permissions"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by DigitalRanger on 2007-04-21
So Feisty now has read/write support for NTFS.

How does it work in the case of NTFS directory trees that have specific permissions?

(Example - XP laptop has two users who have their own file areas protected from each other by permissions. They dual boot with Ubuntu, and want to access their NTFS files - how does that work so that each user can access their files while respecting each others permissions?)

Thanks.

---

### Post by Happy_Man on 2007-04-21
You will have to set that within Ubuntu. Head over to whatever folder you want blocked, and use the Permissions tab under Properties to set user access.

---

### Post by DigitalRanger on 2007-04-21
> **Happy_Man said:**
> You will have to set that within Ubuntu. Head over to whatever folder you want blocked, and use the Permissions tab under Properties to set user access.

Thanks - So that means I can access any NTFS directories through Ubuntu, regardless of the permissions in XP ? (i.e. I don't have to use my/our Windows log-in details to access protected/permissioned NTFS folders ?)

---

### Post by Drakkor on 2007-04-21
Try this

---

### Post by Jormanks on 2007-04-21
And if that doesnt work?

---

### Post by dreadlord_chris on 2007-04-21
> **DigitalRanger said:**
> Thanks - So that means I can access any NTFS directories through Ubuntu, regardless of the permissions in XP ? (i.e. I don't have to use my/our Windows log-in details to access protected/permissioned NTFS folders ?)

Simple answer: Yes, if you mount your NTFS partitions with the ntfs-3g driver you will be able to access everything - except compressed or encrypted folders.

Linux & Windows use two totally different file-system security models, the ntfs-3g driver ignores the NTFS permissions: one consequence of this is you can't modify the NTFS permissions from within Linux (or visa-versa).

---

### Post by Drakkor on 2007-04-21
Works fine for me !! :)

---

### Post by DigitalRanger on 2007-04-21
> **dreadlord_chris said:**
> Simple answer: Yes, if you mount your NTFS partitions with the ntfs-3g driver you will be able to access everything - except compressed or encrypted folders.

Linux & Windows use two totally different file-system security models, the ntfs-3g driver ignores the NTFS permissions: one consequence of this is you can't modify the NTFS permissions from within Linux (or visa-versa).

Thanks for that. Looking back at Happy_Man's reply, am I correct in understanding that once mounted, I can set permissions within Ubuntu for which mounted directories are available to who?

---

### Post by Happy_Man on 2007-04-21
Yeah, that's pretty much it.

---

### Post by DigitalRanger on 2007-04-21
Great stuff, thank you. Now all I need to do is pluck up courage to actually start installing :D

---

### Post by Jormanks on 2007-04-22
> **Jormanks said:**
> And if that doesnt work?

?
I have to reinstall?

Thanks

---

