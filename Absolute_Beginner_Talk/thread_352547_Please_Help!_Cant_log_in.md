---
title: "Please Help! Cant log in"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by DeeK on 2007-02-03
Hello!

Installed Ubuntu just a few days ago and I absolutely love it!

However, i changed my users directory and now i cant log in.

This is the error i get.

"User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."

Please Help! I can't Log in!

DeeK

---

### Post by danielph on 2007-02-03
How did you change your home folder? What did you actually do / change?

You should be able to log on as root with the root password you entered when you installed ubuntu. With this you can either log into a Failsafe Terminal (choose session) or log into Gnome as usual, but be careful as you will be running as root. 

When you have done this we can look at trying to repair your user account.

---

### Post by ComplexNumber on 2007-02-03
at the login point, choose failsafe terminal as your session. type in '/home' so that you are just outside your home directory. 
right, i'm going to assume that your username is DeeK for this purpose.

change your username to what it should be (ie DeeK).

now type in 'sudo chown DEEK:DEEK DeeK' (NOTE: DEEK:DEEK should say DeeK semicolon DeeK, but i can't write that in this forum because the ":D" is substituted for a stupid smilie). then type in 'sudo chmod 700 DeeK'.

now go back to your login point and login normally.

the dmrc file error is nothing to do with th the dmrc file. its because your home directory permissions have somehow got mixed up.

the important thing to remember is that your home directory (ie /home/DeeK) must have the correct permission to allow you to access it.

---

### Post by DeeK on 2007-02-03
Thanx danielph & ComplexNumber for your replies.

However, i think the problem of mine is not with the permissions. 
It says that "User's $HOME/.dmrc file is being ignored" I changed the directory for my username "deek" under System -> Administration -> Users and Groups to /root.

I think thats what is causing the problem. :S

Tried the "sudo chown" but it does not work. :(

---

### Post by DeeK on 2007-02-03
Any Suggestions ?

---

### Post by shareMenaPeace on 2007-02-03
Change the settings back to /home/DeeK/ than post what you was intend todo and lets see how we find a better solution.

---

### Post by DeeK on 2007-02-03
Thanx shareMenaPeace for your reply.

However, i cant even log in to change the settings!

---

### Post by shareMenaPeace on 2007-02-03
Did you tried to login with failsafe session or as root?

---

### Post by danielph on 2007-02-03
You can log in to a failsafe terminal right?

---

### Post by DeeK on 2007-02-03
Yup i am able to log into failsafe terminal :) How do i change the settings from there ?

---

### Post by shareMenaPeace on 2007-02-03
Do it again with the user group utilitie to 

/home/DeeK


than hit ALT - STRG - BACKSPACE to relog normal.

---

### Post by DeeK on 2007-02-03
I cant log in. I cant get to the user group utility.

---

### Post by danielph on 2007-02-03
I am still not sure what you did to start with?
EDIT: Just read post about changing user directory to root

but take a look at the file in question once you log into a terminal.

Post the results of this
```
ls -al ~/.dmrc
```It should be something like this:
-rw------- 1 dan users 24 2006-12-09 16:18 /home/dan/.dmrc

---

### Post by danielph on 2007-02-03
I just read the post about changing the user directory. It won't hurt to create another account and see if you can log on from there. I have no idea what happens when you change a users account to use the /root folder.

 Create another account and user directory:

```
sudo useradd -m -G users -s /bin/bash test
```type exit and try logging on again with the test account.

---

### Post by danielph on 2007-02-03
Additional Info



To show the current folder DeeK is set to
```
cat /etc/passwd |grep DeeK

```
To change home folder to DeeK
```
usermod -d /home/DeeK DeeK
```

---

### Post by DeeK on 2007-02-03
Thanx danielph! Your a saviour!
I created another user named "test" with an administrator group account and went in to change my settings!

Cheers!
DeeK

---

