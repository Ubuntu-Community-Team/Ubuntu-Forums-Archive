---
title: "[SOLVED] How Do I Change Permissions and Delete This Folder?"
date: 2007-09-13
forum: Absolute Beginner Talk
---

### Post by chrome307 on 2007-09-13
[IMG]http://i6.tinypic.com/661irg2.jpg[/IMG]

---

### Post by por100pre1 on 2007-09-13
Try typing this in terminal (with an space after it):

```
sudo rm -r 
```

drag and drop the folder into the terminal window and THEN press enter...

another way:

```
gksudo nautilus
```

and then do what you need...

OH! I see...

```
sudo chmod -R 755 folder
```

I'm sooo dumb...

---

### Post by hardyn on 2007-09-13
sudo rm -r

without specifying a sub dir, will that not delete everthing?

okey, i should have read that closer... pardon me... but it DEPENDS on the drag and drop of the sub dir.

---

### Post by chrome307 on 2007-09-13
Thank you :)

the first command worked .......... took ages as the folder was over 1.5GB

---

### Post by santy_kushwaha on 2007-09-13
u need to login as the root to gain the own root acess and the terminal will not help in this case u have to login as the root

---

### Post by mohit052 on 2007-09-13
1.become " / "
$sudo su root
Password:
Re-Type Password:

root@machine_name$

2.change the permissions of the folder. with the following command everyone gets write permissions
$chmod +w filenmae 

3.delete the file or dir
$rm -rf filename

---

### Post by mcduck on 2007-09-13
> **mohit052 said:**
> 1.become " / "
$sudo su root
Password:
Re-Type Password:

root@machine_name$

2.change the permissions of the folder. with the following command everyone gets write permissions
$chmod +w filenmae 

3.delete the file or dir
$rm -rf filename

It would be way easier to just use 'sudo' instead of activating the root account and logging in as root. And if you are root, you there's no reason to change permissions of the directory any more.

'sudo rm -r /path/to/directory'

Even if you, for some reason, wan to became root in terminal you don't need to go through the trouble of activating the root account. Simple 'sudo -i' will open a root session for you (run 'exit' to quit the root session when you are ready).

Anyway, in case like this I'd just run 'gksudo nautilus' to open the file manager as root and then use that to remove the directory. :D

> **santy_kushwaha said:**
> u need to login as the root to gain the own root acess and the terminal will not help in this case u have to login as the root
This far I haven't found a single thing that would require you to be root in Ubuntu.  And of course you can do this kind of stuff in terminal. That's what 'sudo' is for. :D

---

