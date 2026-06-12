---
title: "Changing folder permissions"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by milad on 2007-04-13
I'm using Samba to share a folder between my Ubuntu desktop and Windows laptop.
When I was following the guide to set up Samba I changed my shared folder permissions using this command:

sudo chmod 0777 /media/samba

I wanna be able to read/write this folder but not modify current files. Is this the correct settings for me?

---

### Post by aysiu on 2007-04-13
I think you'd want something like ```
sudo chmod -R 444 /media/samba
sudo chmod 664 /media/samba
``` That will give you read-only for all the current files, but it should give you read/write for the folder. Not 100% sure on that, though.

---

