---
title: "root password"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by sudhir on 2007-05-20
hello frnds,
                 few weeks ago i installed ubuntu6.01.my user password doesnot match with my root password. anyone know how to get the root password? thanks

---

### Post by diatribe on 2007-05-20
are you saying when you use sudo your password doesnt work or when you try to login as root?

---

### Post by taurus on 2007-05-20
There is no root password since root is locked as a default.  If you need to run something as root, use sudo and the same password that you log in with.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by sudhir on 2007-05-20
hey i used the su command.i entered the user password. but it dint accept password. my frnd told me that OS will randomly select  root password. is it true?

---

### Post by AlanD on 2007-05-20
If you are an administrator on your linux box and you really must log in as root, you can do so easily by:

1) go into user accounts (system -> administration -> user accounts). Open the root account, and set the password as you like. Make sure it's a secure password!

2) Go into login window (system -> administration -> login window). Click security. Check off "allow local system administrator login"

3) log out of your account, and login as root (username: root  password: whatever you set root password to)

4) Do the dirty work, log out and log in as yourself, and uncheck the "local system administrator login" when you're done.

Note that being logged in as root is dangerous as you have the power to mess up any file you wish. Make sure you know what you are doing before logging in as root, as it gives you 100% access to every file. Only do this if you absolutely must, and use it as little as possible. It is preferable to use the sudo command for administrative tasks, under your own account, and sudo will suffice for 99.9% of tasks.

---

