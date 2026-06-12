---
title: "Samba user accounts"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by bereta on 2007-12-05
Hello all 

I need so me help with setting up accounts in samba.

I have put linux server 6.06 LTS on a computer that i want to use as a storage server. I have installed samba on it and i can map to it from a windows  xp box with the root account just fine. But what i am trying to do is set up another account(s) for other people to log in with. I used the useradd command to add a second account in linux and then smbpasswd command to add that same user to samba, but the problem is that this new user can not copy and thing or create any directoryes. I've played around with the smb.conf file but still nothing. Is what my share definition looks like 

[homes]

path = /home/folder
guest ok = no
read only = yes
writeable = yes
create mask = 0664
directory mask = 0775

Can any one tell me what I might be doing wrong.

---

### Post by Dr Small on 2007-12-05
Check the actual permissions of the directory, instead of using SAMBA, and see if you set it up for Write access.

Dr Small

---

### Post by bereta on 2007-12-06
Yes that was the problem, changed the file permission and it works.

Thank you for  the help

---

