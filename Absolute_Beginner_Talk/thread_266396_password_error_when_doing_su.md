---
title: "password error when doing su"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by ty_oftrans on 2006-09-27
Hi all!

I am new to Linux and love it so far. I'm am not sure if I'm trying the wrong things, but when I try to log in as su in the terminal, I am given an error message with regard my password.
On other distros when installing, I was asked for a separate password for root an another one for user. With Ubuntu I was only asked for one - I'm not even sure which one was that for: admin or user?
If I try to do something that reqires admin privileges I am asked for password (of course!) and it accepts the one I typed at install. (the only one, that is). If I try to messup with the terminal and do su, it does not take that one.
Am I missing anything? 
Cheers!
Ty

---

### Post by wieman01 on 2006-09-27
You need to enable the root account first:
> sudo passwd root
But a better way to do administrative tasks is the prefix "sudo". E.g.:
[U]> sudo cp file_1 file_2
Wiki:[/U] [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ty_oftrans on 2006-09-27
Can't belive you guys already replied!
Cheers, Wieman01, I try that!
Ty

Woops, hold on. Do I need to do  "sudo passwd root" before I do anything else? That is 'enable once for all', and then just sudo before any future admin tasks?

---

### Post by wieman01 on 2006-09-27
No, actually you don't need the root account. Use 'sudo' with your current user and type in the password when prompted. Your current user has the 'sudo' ability.

However, I usually enable root because I need it in case I forget/lose my current user's password.

You can go ahead with 'sudo' right away.

---

### Post by ubuntuuser on 2006-09-27
Whoops, I misread your post.
wieman01 is right, you don't have to do this if you want to use sudo. But to use su to become root permanently, what I say is true, too :)

That's right. Let's examine this:
```
sudo
```lets you run the command as a different user, usually root.```
passwd root
```changes the password for the root account. If your username was Ben, you could do```
passwd Ben
``` without root privileges. Once you set a password, it's there until you change it again.

With a root password set, you can log in as the root user, which is generally not a good idea as a beginner. To get a root shell, you can also use ```
sudo -s
```, without having set a root password. But remember to close the shell once you're done.

---

### Post by Ben Sprinkle on 2006-09-27
To enable root password when typing su:

Step one:
Go to system=>manage accounts

Step two:
Go to your accound, enable all groups/users

Step 3:
Drag all abilityies to your account.

Step 4:
Set a password for root, then drag your user to the root usergroup and enable all options. :)

---

### Post by wenzlicker on 2006-09-27
You don't have to enable the root account. You can type 

sudo su

to get a root terminal

---

