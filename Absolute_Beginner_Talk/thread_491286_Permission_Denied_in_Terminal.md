---
title: "Permission Denied in Terminal?"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by TheBlackWizard on 2007-07-03
Greetings!

So, I am new to Linux and Ubuntu, and am learning the shell commands.

I am using the terminal program found in Applications > Accessories, in a standard Feisty Fawn installation.

When I try to use the mkdir command, I get an error message stating "cannot make directory x: permission denied"

what am i doing wrong?

am i logged in to root by default? do I need to log into a root? Is there some way to set the permissions?

Also, any links to a beginners guide that explains all of the directories and username setups would be nice.

Thanks!

---

### Post by dca on 2007-07-03
"sudo mkdir"

---

### Post by TheBlackWizard on 2007-07-03
Excellent.

Can you tell me what sudo does?

I am guessing by the su part, that means superuser.

Is my default login not the root? (The login I use to get into the GUI at startup.)

Will someone explain this in a bit more detail, how the user / su work?

---

### Post by r4ik on 2007-07-03
Try,

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Good luck !

---

### Post by mlentink on 2007-07-03
sudo means something like "as superuser do..."

You&#314;l find a good explanation of the shell commands at linuxcommand.org, although that isn't geared to Ubuntu specifically. Obviously the [ubuntu Wiki]("https://help.ubuntu.com/7.04/") is also a very good source

---

### Post by jfinkels on 2007-07-03
You may only make a directory if the parent directory gives you write access. You can check permissions for files and directories by typing:```
ls -l
``` (that's a lowercase L after the dash). For a directory, you will see the permissions looking something like this:```
drwxr-xr-x
```This is a shorthand: the 'd' means the listing is a directory, the first set of three letters, 'rwx' means that the owner of this file (listed after the permissions) has read, write, and execute access to this directory. The second set of three letters, 'r-x', means that the group to which this directory belongs (listed after the owner) has read and execute access only. The last set of three letters, 'r-x', means that all other users (i.e. all users who are not the owner, and who are not in the group that owns the file) have only read and execute access. The same rules applies to read, write, and execute permissions for files.

Now, if the parent directory is owned by "root", a special user with more rights than your personal user account, and permissions on the directory do not allow you to write in the directory, then you must log in as the root user (aka the 'super user') to write in that directory. One way to do this is to log in as root in the terminal by typing the following:```
su
``` (for Super User) and typing the root password. You will then be able to execute commands as root.

Another way to perform commands as root without logging in as the super user (aka root user) is to use 'sudo'. To make a directory in a location owned by root, type the following:```
sudo mkdir foo
``` Then type **your ** password (because the computer checks to make sure that **you** are allowed to use the 'sudo' command) and the directory will be created. You can use sudo before pretty much anything.

BTW, if you haven't yet set the password for the root user, you can type:```
sudo passwd
```

You can read all of this in the link in my signature, "Root & Sudo". Let me know if you need any more explanations.

---

### Post by rolfen on 2007-07-03
> **TheBlackWizard said:**
> Excellent.

Can you tell me what sudo does?

I am guessing by the su part, that means superuser.

Is my default login not the root? (The login I use to get into the GUI at startup.)

Will someone explain this in a bit more detail, how the user / su work?

duh
just do "man sudo"
you need to be super user to create directories outside your home folder. Your home folder is /home/YOURUSERNAME

look at your command prompt, it looks like this
[user@host directory]#
user being the user you are currently logged in as in the console

---

