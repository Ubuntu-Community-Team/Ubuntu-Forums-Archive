---
title: "[SOLVED] 1st User Account"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by minutest on 2008-01-18
When installing Ubuntu 7.10 is the 1st account made during the install the Root account or is it just an accound with some Admin. Privileges?

I have read that I do not want to be logged in as the root account.
Just checking if I need to make a new account or if is ok ( safe security wise) to keep using the account made during the install?

thx.

---

### Post by vikram on 2008-01-18
you are good to go with the default account. if you want to exevute any command with root access use the sudo command. more details 
[https://help.ubuntu.com/community/RootSudo?highlight=%28sudo%29]("https://help.ubuntu.com/community/RootSudo?highlight=%28sudo%29")

---

### Post by LowSky on 2008-01-18
ubuntu kinda hides the root user.

The first account you make is a regular account that has the ability to do root work

basically you can use root privaleges without being logged in as root

---

### Post by aysiu on 2008-01-18
The root account is disabled for login in Ubuntu.

Your 1st account operates as a limited user most of the time, and you can temporarily elevate your privileges to root level with password authentication.

---

### Post by sumguy231 on 2008-01-18
The 1st account created is a member of the admin group which allows doing administrative tasks with sudo. It's safe to run as this user.

Edit: Arg, 3x simulpost!

---

### Post by nikoPSK on 2008-01-18
you can use sudo move or others to move, make or delete folders, or the chown command.

---

### Post by minutest on 2008-01-18
thx everybody. Just needed that cleared up for me.

:)

---

### Post by nikoPSK on 2008-01-18
no problem, please mark this thread as "SOLVED". :)
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

nikoPSK

---

