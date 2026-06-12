---
title: "sudo from diff account doesn't work"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by mikeserv on 2007-12-22
So I've created an account with only desktop user access.  There are a couple of things that I'd like to use sudo for to get this account set up, but everytime I try absolutely nothing happens.```
*desktop user account*@ubuntu:~$ sudo -i -u *admin account name* nautilus
*desktop user account*@ubuntu:~$ 
``` or ```
*desktop user account*@ubuntu:~$ echo "*admin account password*" | sudo -S -i -u *admin account name* nautilus
bash: echo: write error: Broken pipe
*desktop user account*@ubuntu:~$
```

A root nautilus window should be popping up, as it would if I were doing this from the admin account terminal.  What am I doing wrong?

-Mike

---

### Post by jken146 on 2007-12-22
A normal desktop user cannot use sudo.  If you want to make this new user an administrator, add them to the admin group.  Otherwise, you should do all your sudo-ing from your admin account (remember you can do anything with sudo).

---

### Post by mikeserv on 2007-12-22
I realize that, but shouldn't I be able to use it temporarily with an admin password?

-Mike

---

### Post by jken146 on 2007-12-22
No, you can't I'm afriad.  I don't see how you need to though.

---

### Post by mikeserv on 2007-12-22
Then what does the "Logging in as another User" section mean [here]("https://help.ubuntu.com/community/RootSudo#head-85ac78438bc420e5c6283b53e27c0aa4ec655f8a")?

And what does the "sudo -u" option do?

-Mike

---

### Post by jken146 on 2007-12-22
I think it lets you assume super user privileges, but with another user's settings being loaded (like the default directory, which shell to use, etc.).  You can still only run it as an admin user.

---

### Post by jken146 on 2007-12-22
I just tried it, and it does just what it says it does.  It gives you root privileges and then logs you in as the user you specify, just within that terminal.  Type **exit** and you'll stay in the terminal but see a logout message.


So I guess I was wrong -- what you were trying to do is possible.  You just need to log in as an admin user first, then use sudo -i -u to log in as the next user.

---

### Post by mikeserv on 2007-12-22
So I can only use sudo as another user if the user I'm changing from can already use sudo?  Or are you saying that within the desktop user's terminal I can login to an admin?  If so, how?

-Mike

---

### Post by jken146 on 2007-12-22
From the admin user's terminal you can log in as the desktop user, using sudo -i -u desktop-user's-username .

---

