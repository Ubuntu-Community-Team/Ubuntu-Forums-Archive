---
title: "adding users to sudoers file"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by Winblowz on 2006-06-21
I'm setting up an Ubuntu server. I'm using nothing but the command prompt (no gui), and I need to add another user. I already added the user by doing the  "useradd" command. Now, when I try to use sudo with the new user it says he is not in the sudoers file. I can run the sudoers file with "visudo", but where do I go from here? What do I add to the sudoers file to create the new user?

---

### Post by catlett on 2006-06-21
[http://doc.gwos.org/index.php/DapperGuide#How_to_allow_more_sudoers](http://doc.gwos.org/index.php/DapperGuide#How_to_allow_more_sudoers) Follow this gfuide and it will give you ther needed editing and commands.

---

### Post by aysiu on 2006-06-21
```
sudo adduser *username* admin
``` or ```
sudo cp /etc/group /etc/group.backup
nano /etc/group
``` and add the user's name to the *admin* line.

---

### Post by Winblowz on 2006-06-21
thanks, that solved it:D

---

### Post by Winblowz on 2006-06-22
I also wanted to add another user to my Desktop Kubuntu installation, so I followed the same technique. When I tryed to login with the new user I had created, it said "Could not start kstartupconfig. Check your installation." Any ideas?

---

### Post by aysiu on 2006-06-22
Maybe [this](http://www.linuxquestions.org/questions//showthread.php?t=328302) might help?

---

### Post by Winblowz on 2006-06-22
That link was just what I needed:p

---

