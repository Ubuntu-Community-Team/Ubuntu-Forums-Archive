---
title: "can not log as root"
date: 2005-10-03
forum: Absolute Beginner Talk
---

### Post by Marw on 2005-10-03
Hi I've installed ubuntu breezer it works but i can not change anything because I am not root.
At first I thought it was my mistake in password spelling so i reinstalled it wrote only one letter root password but it is still the same wrong password can somebody help me?

---

### Post by mpat on 2005-10-03
In Ubuntu the root login is disabled by default, just to protect you from yourself. ;-)

Just log in with the account you've created during the installation and use:

```
sudo <command>
```

Then *<command>* is executed as user root. I know that there is a way to reactivate the root account, but I don't have it in mind. Maybe you'll find something in the HOWTOs. I always use sudo or - if I want to make more modifications on my system:

```
sudo /bin/bash
```


Have fun!

---

### Post by dgrafix on 2005-10-03
you can either use sudo (command) 
or there is a way of enabling su but its not reccomended(aparently, im new to this too)
you may want 2 check it but i think its
sudo su -c passwd
 
give it a password
then u can use su

but sudo is more secure

---

### Post by Mustard on 2005-10-03
Try hitting ctrl-alt-F1, logging in as root, then edit the /etc/sudoers file to allow the user account you are using now to have superuser privileges.

To edit the file type this, which opens up the sudoers file in the nano editor...

```
nano /etc/sudoers
```

Find the section that looks like this....

# User privilege specification
root	ALL=(ALL) ALL

add this line...

# User privilege specification
root	ALL=(ALL) ALL
**your_user_name** ALL=(ALL) ALL

..substituting your user account login name for the part in bold.

Ctrl+O will save the file
Ctrl+X will exit the nano editor.

Exit from root login.
I think you might have to hit ctrl-alt-f7 to get back to desktop, I can't remember.

Your user account should have superuser privileges now.  This means that when you are asked for a password when performing an administrative task, you put in your user account password, not the root password.

---

### Post by DJ_Max on 2005-10-03
It's always good to do a little reading as well. [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

