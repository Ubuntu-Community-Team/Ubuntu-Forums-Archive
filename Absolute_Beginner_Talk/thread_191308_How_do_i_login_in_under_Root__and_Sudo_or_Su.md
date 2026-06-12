---
title: "How do i login in under Root  and Sudo or Su?"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by truth on 2006-06-07
How do i login in under Root  and Sudo or Su? 

ive never set a password for any of these accounts so how can i access them or set them up so i may make changes to my system?  

Thx

---

### Post by uzi09 on 2006-06-07
root account is disabled by default (best to leave it that way).
sudo is a command used to run commands as admin (aka root).
just stick sudo in front of a command where you need admin permissions and it'll ask you for YOUR password. as in the password to log into your account. it'll double check to see if you're allowed to use sudo and continue, or tell you that you can't.

to run as root, you can type the following:
sudo -sH
then put in YOUR password for your own login.

su allows you to switch to a different user. su without any options will try to change you to root, but you need to have the password for that set to be able to do that. if you type su user2 where user2 is another username, it'll ask for their password then log you in as that user. enjoy :D

---

### Post by carlosqueso on 2006-06-07
To use commands which require you to be root, you just need to type sudo before the command.  The password that it asks you for is the USER password that you created for the account.  [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) has more details.

EDIT: Too slow....curses ;-)

---

### Post by Kilz on 2006-06-07
You can also use 
gksudo nautilus 
To use Nautilus as root if you want to use the gui instead of the terminal.

---

### Post by uzi09 on 2006-06-07
[QUOTE=carlosqueso][https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)[/QUOTE]

yeah, i've seen this all over, couldn't find it when i needed it though :S, thanks :D

[QUOTE=carlosqueso]EDIT: Too slow....curses ;-)[/QUOTE]
haha :P

---

