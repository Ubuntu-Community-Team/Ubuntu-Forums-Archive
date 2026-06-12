---
title: "Sudo command"
date: 2006-10-22
forum: Absolute Beginner Talk
---

### Post by Alvar on 2006-10-22
I'm having problems using the sudo command. Such as "sudo -i" and then I enter my password and run "synaptic". I get a message "not loged in as a root user, application will run in read-only mode". Then so I try reset my terminal and type in "sudo synaptic" and enter my pass. This time nothing happenes. I typed it again and still nothing happens. It seems like running a normal command works ,ie. synaptic with no admin purposes, but running a sudo command returns nothing. I want to run as a root user but I can;t seem to (Can't even listen to music on CD). Please help me on how to access admin status.

---

### Post by raul_ on 2006-10-22
```
 sudo su root 
``` then enter your password. Everything u type in the terminal after that will be in root mode

---

### Post by GStubbs43 on 2006-10-22
Never mind.... I read the post wrong... ;)

---

### Post by bigken on 2006-10-22
create a new password in the terminal type **sudo passwd** ;)

---

### Post by Alvar on 2006-10-22
I don't know what is going on guys. I typed in your commands, but it just ignores it and goes to the next command line (just like nothing even happened) and it is not even asking me for my password.

---

### Post by bigken on 2006-10-22
you could try and boot into single user mode and try the sudo passwd :-k

---

### Post by Alvar on 2006-10-22
Sorry but how do I boot into single user mode? Usually I just see the options of logining in as Gnome and default user mode.

---

### Post by raul_ on 2006-10-22
But in the terminal what name does it display? Your used name or "root" ? Because if u have entered ur password in a short past, the next time u make "sudo" it won't prompt u for the pass

---

### Post by bigken on 2006-10-22
when the pc 1st boots press escape its either   single user or safe mode ;)

---

### Post by Alvar on 2006-10-22
It has my name in the terminal. After I type sudo and enter password, my name is still there. I don't see anything like "root@sumel -laptop" if that is what you mean. That never shows up

---

### Post by Ba|der on 2006-10-22
After writing 
```
sudi -i
``` or ```
sudo bash
``` you should get root in front of the @. For testing purpose, try Ctrl+Alt+F2 and login with your normal login, and retry the commands above. You log out with ```
exit
``` and you may change back to X with Ctrl+Alt+F7.

---

### Post by CatKiller on 2006-10-22
Are you in the admin group, the list of people who are allowed to use sudo? There are quite a few posts from people who have managed to take these privileges away from themselves.

---

### Post by kijuan on 2006-10-24
i had a problem regarding sudo command, when i input the command "sudo -i" there was an error "sudo: shell: command not found", can you help me with my problem... but when i input "sudo bash" it will  go to root.

---

