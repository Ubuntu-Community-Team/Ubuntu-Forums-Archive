---
title: "Howto set Permissions for File Server"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by dplewis on 2006-12-10
Hello all, I'm still working on trying to get Ubuntu server working for my home network.  I'm stuck right now trying to figure out how to setup groups/users on the file system and samba shares.

Basically, I'm setting up two shares (music, pictures).  I want to have read/write access to these shares.  The kids will have read only access.

After reviewing many forums, I thought I could accomplish this goal by using groups. 

_groups:_
music_M
music_R
pictures_M
pictures_R

_directories:_
/srv/samba/music
/srv/samba/pictures

I figure I need to set the permission on the file system first.  How do I go about doing this with the requirement for a Read Only and Modify group?  Is there a better way?

Thank you,

David

---

### Post by dplewis on 2006-12-11
I figured out that I can setup the read and the write groups within Samba.  At least that's what I plan on trying next.  My question is, for this to work, how am I supposed to set permissions for the directory on the file system?  Do I need to do anything, or does Samba handle everything?

Thanks,

David

---

### Post by chalex on 2006-12-11
I'm not sure how to do this off the top of my head, but the Samba guide is pretty good.  Here's the relevant section: [http://us4.samba.org/samba/docs/man/Samba-Guide/simple.html](http://us4.samba.org/samba/docs/man/Samba-Guide/simple.html)

I think your usernames/groups within samba will need to match your Windows usernames/groups.

---

### Post by Iowan on 2006-12-11
> **dplewis said:**
> Do I need to do anything, or does Samba handle everything?
I *thought* Samba handled the details.  If not, you can edit directory permissions later.  You *should* be able to use the **read list =**and **write list=** options to control who can do what (although it might be a bit redundant to use both - if a user is not in the write list, they can read-only... well, if they can read at all).

---

