---
title: "File Sharing"
date: 2006-07-23
forum: Apple PPC Users
---

### Post by mooreted on 2006-07-23
Okay, I read the howtos, searched the Internet, searched the forums.

How do you share files EASILY between OSX and Ubuntu?

---

### Post by simonn on 2006-07-23
> **mooreted said:**
> Okay, I read the howtos, searched the Internet, searched the forums.

How do you share files EASILY between OSX and Ubuntu?

What are you finding so hard?

---

### Post by mooreted on 2006-07-23
For instance. After following the directions on the NFS howto, when I try to mount the Linux NFS share from OSX I get:

Operation not permitted.

I can share files with Windows in a few minutes, I've been at this all day. I just can't make it work.

---

### Post by simonn on 2006-07-23
> **mooreted said:**
> For instance. After following the directions on the NFS howto, when I try to mount the Linux NFS share from OSX I get:

Operation not permitted.


Do the users have the right permissions?

Users must have the same uid on both OSX and Linux.

Also, IIRC NFS shares must be a whole partition, not just any old folder.

Samba is easier. I suggest you look at the samba howto at samba.org. Plenty of examples.

> I can share files with Windows in a few minutes, I've been at this all day. I just can't make it work.

Ask yourself, "does anyone else care that I can do this in windows?". I don't.

---

### Post by mooreted on 2006-07-23
Samba is really, really slow.

When I try to use NFS manager for OSX, I can't click anything, no nfs servers show up, I can't add entries. I think something is wrong with my network on the OSX side. I wish I knew how to figure out what the problem is.

Oh well, maybe someday I'll know what I'm doing.

Thanks anyway.

---

### Post by mooreted on 2006-07-23
After another day of searching, I found out that for OSX to access NFS shares, you have to set the 'insecure' parameter in the exports config file. After setting that, it works great.

---

### Post by jrharvey on 2008-01-29
> **mooreted said:**
> After another day of searching, I found out that for OSX to access NFS shares, you have to set the 'insecure' parameter in the exports config file. After setting that, it works great.

How do you do this??

---

### Post by oswaldkelso on 2008-01-30
[http://ubuntuforums.org/showthread.php?t=657225](http://ubuntuforums.org/showthread.php?t=657225)

---

### Post by ssam on 2008-01-31
try gshare.

---

### Post by Ripfox on 2008-01-31
> **simonn said:**
> Do the users have the right permissions?

Users must have the same uid on both OSX and Linux.

Also, IIRC NFS shares must be a whole partition, not just any old folder.

Samba is easier. I suggest you look at the samba howto at samba.org. Plenty of examples.



Ask yourself, "does anyone else care that I can do this in windows?". I don't.

I do...he's just citing an example.

---

