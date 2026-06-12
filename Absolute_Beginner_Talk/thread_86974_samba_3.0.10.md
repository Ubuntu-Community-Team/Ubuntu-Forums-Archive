---
title: "samba 3.0.10"
date: 2005-11-06
forum: Absolute Beginner Talk
---

### Post by kiviuq on 2005-11-06
Hi all, 
I am new to ubuntu and I am not sure where to post a question about samba. It is up and running but rejecting name/password from a windows 2000 server user. I have more info, but waiting to post in the proper forum.

---

### Post by davidsrsb on 2005-11-06
Samba uses its own user/password system which need to be set up. The most common beginners mistake is to only create the user as a Linux user.

---

### Post by kiviuq on 2005-11-07
Using the smbpasswd -a <username> did the trick. Thanks, I did not know that there is two seperate user databases.

---

