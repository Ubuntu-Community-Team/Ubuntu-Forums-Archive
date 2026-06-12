---
title: "SAMBA issues"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by ProjectGod on 2006-05-13
Hi Gang,

under /etc/samba on my ubu machine. there appears to be 3 smb.conf files!!!

smb.conf, smb.conf~, and smb.conf~~.

what does the ~ signify? which can i edit? 

cheers.

---

### Post by Bagnaj97 on 2006-05-13
I think the ~ on the end means it is a cached copy/backup file. Gedit makes lots of these, I'm not sure about other editors. The version that samba uses is smb.conf

---

### Post by ProjectGod on 2006-05-13
so i guess i just need to edit smb.conf... wondering if i can delete the other ones. :-k

---

### Post by muep on 2006-05-13
Deleting the other ones is ok, they are just backups made by your editor.

---

### Post by ProjectGod on 2006-05-13
excellent.

so if i want to remove samba all together. guess all i have to do is reverse the order... that is... use "**sudo apt-get remove samba**" and remove the folder i shared previously in "folder sharing" GUI tool. 

or perhaps the better way would be to use "**sudo apt-get remove --purge samba**" which also clears out the **.conf** cache

furthermore i need to remove the SYSTEM USER that acts as the user who accesses to the ubuntu shared folder(s).

cheers.

---

