---
title: "[SOLVED] HELP! Cannot login Xubuntu as administrator"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by Faten Rezk on 2008-03-14
Hi, I've just updated Xubuntu (update manager). I re-booted my machine...and cannot longer log in as administrator. Before updating I had added different users. They can all log in (but none of them have administrator privileges), except for the administrator. Please help!

---

### Post by xeth_delta on 2008-03-14
Normally, in Ubuntu you are not able to log-in as root. This is done for security reasons, as regular programs should not be run with administrative privileges.

I am not sure if you have enabled the root account, but the usual way to do administrative tasks in Ubuntu is to precede the command with sudo, for example:
```
sudo command_name
```
If this is what you are unable to do any longer, it might be that your group file was changed. Please post the contents of "/etc/group" between CODE tags.

---

### Post by chlorinekid on 2008-03-14
go to System > Admin > Login Window and select the Security tab.there you'll find a check box that allows root to login from the initial login screen.

---

### Post by Faten Rezk on 2008-03-14
Thanks for getting back to me.

How do I "post the contents of "/etc/group" between CODE tags"? I can't access Login Windows if I log in as any of the three users I created before updating Xubuntu. 

I tried to type in terminal the sudo command_name but nothing happens...I replaced "name" with "sharabiyya" (the name I registered with when I installed Xubuntu)

---

### Post by xeth_delta on 2008-03-14
> **Faten Rezk said:**
> Thanks for getting back to me.

How do I "post the contents of "/etc/group" between CODE tags"? I can't access Login Windows if I log in as any of the three users I created before updating Xubuntu. 

I tried to type in terminal the sudo command_name but nothing happens...I replaced "name" with "sharabiyya" (the name I registered with when I installed Xubuntu)

Ah, sorry for not being more concise. Let's start with sudo. This command will provide temporary administrative privileges for running a program, when I said "command_name" I mean that you can replace that with the name of the command you want to run. Here is an example:

Open a terminal and let's say you want to run nano as root. In the terminal, type:
```
sudo nano
```
Your regular password will be asked and then the program will run.
Now, if you want to run a program that has a GUI, use gksudo (in Gnome) or kdesu (in KDE):
For example, we want to run gedit as root:
```
gksudo gedit
```
or run kate as root:
```
kdesu kate
```

Now, how to copy the contents of /etc/group:
Open  a terminal and type:
```
gedit /etc/group
```
copy the contents and paste it in the posting page, where you type.

---

### Post by xeth_delta on 2008-03-14
For more information on how Ubuntu uses sudo, you can read [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
Another great resource for Linux and in particular Ubuntu information is [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

Don't hesitate to ask in the forums should you have more questions.

Good luck!

---

