---
title: "Root User"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by manishk on 2006-11-04
When installing Ubuntu I gave an user name and password as part of the process...but my 'promt' in Terminal is a $ shouldn't it be a # for a root user??

---

### Post by David_T on 2006-11-04
type "sudo su", enter your normal user account password, and you will be in root.  example:
```

$ whoami
davidt
$ sudo su
Password:
# whoami
root
# 

```

---

### Post by quux on 2006-11-04
It should... but only if you become root first. You can do this e.g. via "sudo bash". 

You can check your current identity using the "id" command.

---

### Post by manishk on 2006-11-05
Once I 'do' this **sudo su** thing in the terminal...will I be the root user even in gnome?? I ask beacuse when I tried installing new themes or changing the permissions on a file it said the file is owned by the root and I cant do it.

---

### Post by taurus on 2006-11-05
You can install themes in your own $HOME/.themes.  And if you want to copy something to root's partition, then use it with the sudo command...

```
sudo cp <filename> <destination>
```

---

### Post by CatKiller on 2006-11-05
No. You'll be root in that terminal.

---

### Post by ewl1217 on 2006-11-05
I can't believe this hasn't been mentioned yet...

In Ubuntu, unlike some other Linux distributions, you run as a normal account, and can temporarily elevate to root privileges using sudo. The root account is actually disabled by default, but you can enable is if you want. I reccomend that you read [this wiki page]("https://help.ubuntu.com/community/RootSudo") about sudo.

---

### Post by manishk on 2006-11-07
Got it! Thanks people

---

