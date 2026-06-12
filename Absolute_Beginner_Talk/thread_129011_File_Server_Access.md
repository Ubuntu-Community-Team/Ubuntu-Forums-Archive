---
title: "File Server Access"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by DavidPeterson on 2006-02-12
Hello,
I just installed ubunto and I need to know  how I can access files from another computer from my apps. I used the "files on server" tab under places to access my file server which worked great. However, I can't find it from my apps such as openoffice or gimp. How do I set it up so I can use my file server from my programs?

---

### Post by nursegirl on 2006-02-14
Hi David,
Could you please repost this question with more information about the other computer and how you are connected?  It will make it easier for us to answer you.

---

### Post by David Corrales on 2006-02-14
You're talking about browsing shares from within non-integrated programs. Currently that's an issue because programs who can view the gnome-vfs are able to read/write to browseable shares transparently while those who aren't (like OpenOffice for example) can't do it.
The best solution you can do is to actually *mount* the shares you need to access from all programs. That way, the remote files are seen as part of the current local filesystem and the transparency trick works for every application. For this I'd recommend using something like **LinNeiborhood** which allows you to browse all available MS workgroups and mount whatever you need onto your local filesystem :)

---

