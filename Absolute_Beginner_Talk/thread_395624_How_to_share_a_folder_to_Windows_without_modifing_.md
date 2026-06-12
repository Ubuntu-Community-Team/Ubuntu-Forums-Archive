---
title: "How to share a folder to Windows without modifing text files?"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by astrolabio on 2007-03-28
I know my way in the /etc/samba/smb.conf file.

But I was wondering if there is finally an easy tool to make those kind of simple shares faster.

Either KDE or Gnome or whatever based app woud be great.

I tried the GNOME->System->Administration->Shared_Folders but when i go to my windows box it still asks me for a password and the tool i was talking about is not helping me working around this issue.

---

### Post by ziggykg on 2007-03-28
If I'm not wrong, if the username/password pair for Samba and Windows are the same you should be able to access the shared folder without being prompted for the credentials.

---

### Post by astrolabio on 2007-03-28
unfortunately that's not the case.

---

### Post by bigken on 2007-03-28
in a terminal type 

sudo smbpasswd -a (yourname)

sudo smbpasswd -e (yourname)

---

### Post by bigken on 2007-03-28
this will ask for your user password then a new samba password :)

---

