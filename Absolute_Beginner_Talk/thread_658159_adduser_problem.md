---
title: "adduser problem"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by phyxsly on 2008-01-04
Hi. I created a new user using useradd just minutes ago in gutsy. However, when i use the created username to login, it says incorrect password. when I viewed the properties of the user using the Users and groups in the Admin Menue, I found out that the password which is supposed to be 6 characters long became 8 characters. I don;t know what happened. Anyway, here's the command that i used:

sudo useradd -d /home/students/test -m test -p "testin" -c "Just Testing" -g 1002 -s /bin/bash

Where did i go wrong? Please help.

---

### Post by fiddledd on 2008-01-04
Why not just add a user by System->Administration->Users and Groups.

---

### Post by sciencewhiz on 2008-01-04
the adduser and adduser man pages shows that -p expects an already encrypted password. Since what you specified was not encrypted, I have no idea what it would decrypt to.

The best thing to do would be to use the passwd command to change the password.

```
sudo passwd test
```

Like fiddledd, I have found the gui tool very convienent for adding a small number of users.

---

### Post by charlie763 on 2008-01-04
When I tried to add a user with a three character password via the GUI in System > Administration > Users and Groups, the system gave me an error stating the password must be greater than six characters. I did dome searching on how to change this.

I then looked on the internet and found that PASS_MIN_LEN can be defined in  /etc/login.defs.

In Ubuntu, /etc/login.defs tells you to configure the proper file in /etc/pam.d/. It looks like you'll have to edit /etc/pam.d/common-password. There are instructions within that file. You'll have to comment out the line
```
password   required   pam_unix.so nullok obscure md5
```
and uncomment the lines
```

# password required       pam_cracklib.so retry=3 minlen=6 difok=3
# password required       pam_unix.so use_authtok nullok md5

```

I'm guessing you can then change the value of minlen=6 to something else. I haven't tried this, so I cant say that it will work.

---

### Post by phyxsly on 2008-01-04
> **fiddledd said:**
> Why not just add a user by System->Administration->Users and Groups.

It would be easier if I add users using the graphical way. But I will add more than 300 users. It will surely keep my day busy. ;) So, I created a php console script that will read from a file and create users automatically. But the problem their is, the password.

---

### Post by charlie763 on 2008-01-04
A bit of Googleing reveals...
[LIST]
[*][Add users as a batch script then send them an email]("http://ubuntuforums.org/showthread.php?t=224761")
[*][Bash adduser script to generate Linux useradd syntax strings]("http://www.osix.net/modules/article/?id=577")
[*][adduser bash script]("http://ubuntuforums.org/showthread.php?t=273944")
[/LIST]

When you figure things out, please post your solution.

---

