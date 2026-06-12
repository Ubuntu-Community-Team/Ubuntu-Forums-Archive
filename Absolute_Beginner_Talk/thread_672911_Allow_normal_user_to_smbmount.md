---
title: "Allow normal user to smbmount"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by rikoshay on 2008-01-20
Hi,

I've written a little script that mounts a selection of folders from my server onto my desktop PC. It's mainly to make my girlfirend's life easier when she's trying to stream media from the server. As it stands at the moment however, the script makes nothing simpler as it uses the smbmount command which requires the root password to be inputed each time it is called. I don't want all the folders to mount on boot as I don't normally use them. I think what i want to do is to change the permissions of the smbmount command so a normal user can call it.

Does anyone know a way of doing this? I'm using Gutsy.

Cheers

---

### Post by luisromangz on 2008-01-20
The way to go is configuring the sudoers list.

---

