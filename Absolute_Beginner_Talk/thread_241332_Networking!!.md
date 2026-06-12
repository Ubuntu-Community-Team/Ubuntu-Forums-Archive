---
title: "Networking?!?!"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by Alien260 on 2006-08-22
hello, 
i have some files on my PC (ubuntu) that i want to transfer to a windows PC, when i try to "share this folder" it downloads the SAMBA package, but then it cant be found on the network. If i try browsing (on the XP Machine) i cant find my linux machine only the other win Pcs. 

What can i do? 

thanks 
Alien

---

### Post by wieman01 on 2006-08-22
Just a hint since I am not in front of my own computer... You need to specify a **workgroup** under Linux which is the same one as you are using under Windows. You can configure a workgroup using one of the applications/tools that come along with Gnome ("Shared folders"?).

---

### Post by Alien260 on 2006-08-22
hi, 
i did that but everytime i press ok it doesnt change anything. i open it again and it lost all the info i just put in??

Alien

---

### Post by Iowan on 2006-08-22
The **/etc/samba/smb.conf** file has a "workgroup=" line that should be set to your Windows group.

---

### Post by wieman01 on 2006-08-23
Do you open "share folders" with sufficient administrator rights? Does ths system ask you for your password when you start up the application?

This seems to be a problem with your "sudo" rights.

---

