---
title: "[SOLVED] message at logon"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by bobmac on 2007-09-05
Folks,

I'm not only totally new to Ubuntu but also totally new to linux.

When I log on I get the following message:

User's $HOME.dmrc file is being ignored. This prevents the default session and language from being saved. File shoul dbe owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writeable by other users.

Does anyone know what this means and what I should do about it?

Any help would be much appreciated.

Bob

---

### Post by por100pre1 on 2007-09-05
In terminal:

```
chmod 644 .dmrc
```

---

### Post by bobmac on 2007-09-06
Tried the chmod, rebooted and got the same message

---

### Post by sumguy231 on 2007-09-06
Go to a terminal, and do this:
```
cd ~
ls -al

```
Most things there should look like this:
-rw-r--r--  1 <user> <user>   281 2007-03-04 16:31<filename>
Where <user> is your username. If it's not, do this:
```

sudo chown -R <your username goes here, no brackets> /home/<username> 
sudo chgrp -R <username> /home/<username>

```
Also, in the part that says something like "-rw-r--r--" there should be a 'w' before the first dash.

---

### Post by bodhi.zazen on 2007-09-06
.drmc file permissions, in a terminal: (use first set)

> 	sudo chmod 644 .dmrc
	sudo chown user_name .dmrc
	sudo chmod 755 /home/user_name
	sudo chown -R user_name /home/user_name

	OR, if that fails:

> 	sudo chown -R user_name /home/user_name 
	sudo chmod 755 /home/user_name
	sudo rm -rf /home/user_name/.dmrc

Where  user_name = your log-in name :p

ALTERNATE : [http://ubuntuforums.org/showthread.php?t=489171](http://ubuntuforums.org/showthread.php?t=489171)

---

### Post by bobmac on 2007-09-06
Neither of these worked. Here's what happened

calban@ubuntu:~$ sudo chmod 644 .dmrc
Password:
calban@ubuntu:~$ sudo chown calban.dmrc
chown: missing operand after `calban.dmrc'
Try `chown --help' for more information.
calban@ubuntu:~$ chown calban.dmrc
chown: missing operand after `calban.dmrc'
Try `chown --help' for more information.
calban@ubuntu:~$ chown -R calban /home/calban
calban@ubuntu:~$ chmod 755 /home/calban
calban@ubuntu:~$ rm -rf/home/calban/.dmrc
rm: invalid option -- /
Try `rm --help' for more information.
calban@ubuntu:~$ rm -rf/home/calban/.dmrc
rm: invalid option -- /
Try `rm --help' for more information.
calban@ubuntu:~$ 

I'm afraid that the help for these commands doesn't mean a great deal to me.

Bob

---

### Post by alienexplorers on 2007-09-06
you have to remember to leave a space between commands, thats why you are getting so many errors.

> calban@ubuntu:~$ sudo chmod 644 .dmrc
Password:
calban@ubuntu:~$ sudo chown calban .dmrc
calban@ubuntu:~$ sudo chown -R calban /home/calban
calban@ubuntu:~$ sudo chmod 755 /home/calban


---

### Post by bobmac on 2007-09-06
Many thanks to all who helped me.

The last problem was as explained me missing out a space between commands.

Again folks, thank you all

Bob

---

