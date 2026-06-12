---
title: "[SOLVED] mapping from windows to ubuntu server issue."
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by opie102 on 2008-01-26
Hi guys,

 Im having an issue getting XP pro to map to my ubuntu server. I have Samba installed and configured, the drive mounted and shared, the server is in the correct workgroup and i can see the server if I browse the network although I cant see the share.

 If I try to UNC or actually map a drive letter windows pops up the Username/Password box and wont take any login I use ( windows admin log in or the Main ubuntu user)

 I have gotten this to work before, when i had the desktop version of Ubuntu running if i did it as a UNC but cant seem to remember how i did it, this server is going to act as  a file server and not being able to see the drive could pose a problem :)

thanks in advanced for any help.

---

### Post by h0ax on 2008-01-26
Could def. pose a problem if your file server doesn't show the disk ^_^

Have you created a user for samba specifically?

---

### Post by opie102 on 2008-01-28
Thanks. that did it. Didnt realize that i had to create a user in samba figured it would import the user for me, thats what i get for not reading the docs more carefully. lol

thank alot for the help.

---

