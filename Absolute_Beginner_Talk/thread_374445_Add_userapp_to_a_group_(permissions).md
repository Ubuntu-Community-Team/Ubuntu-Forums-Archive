---
title: "Add user/app to a group (permissions)"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by thornomad on 2007-03-02
Hi,

I am using ABCDE to rip some CDs; am getting an error saying it doesn't have permission to create folders in my ~/Music directory.  

I think I can do something around setting up a certain GROUP for my /Music directory (and sub-directories) and then adding myself and ABCDE (the program) to the group so both of us (but not "the world") would be able to create directories and files.

How do I do this in the CLI ?

Thanks!

---

### Post by dmsynck on 2007-03-18
You should be able to do the following as root using sudo. First, use the 
'groupadd' command (man groupadd ) to add the new group to the /etc/group file. Then, you should be able to edit the /etc/group file and add whatever users you want to the group you just created. Now, both users should be a member of that group and have access to the same directories/files. Hope this helps.

---

### Post by thornomad on 2007-03-19
Thanks.  I am still learning about this whole "group" and "permissions' thing ... appreciate that advice.  Will give it a try.

---

