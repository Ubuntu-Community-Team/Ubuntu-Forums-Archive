---
title: "[SOLVED] MythTV can't access my SQL database"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Hopworks on 2007-10-20
I googled this for hours, like I did for creating an XFS file system on a partition. I solved the latter, but can't figure out the former.

I have my second drive mounted with a partition formatted as XFS, and ready to use MythTV. The wheels came off again. I can't get MythTV to be able to access my MySQL database. I'm complete stumped here because the password I gave the backend configuration is exactly the same as the root password for MySQL. I found an instance of the file Myth uses for SQL access that had the password wrong. I edited it via nano and now when I run the backend config from system/administration/MythTV Backend Setup, the graphic background image is all different, and I don't have the menu I had before. Just two pages of options and it's done. I don't get it.

I'm not above configuring ALL that stuff again, but if the passwords match, why can't it access my database(s)?

Hop ](*,)

---

### Post by Hopworks on 2007-10-28
I had a password issue with MySQL that I fixed. I just set it up incorrectly I guess. I went back to the drawing board with MySQL and worked through all of it again, and now MythTV is working just fine.

---

