---
title: "root"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by wiizilla on 2006-07-15
I can't login as root in the start up screen and i want to be able to do that also how do i login as root in the desktop (not the terminal i know how to do that).

---

### Post by Jagot on 2006-07-15
You would have to set up a root user properly - see here:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by verbatim210 on 2006-07-15
use the account details from your default installation

---

### Post by catlett on 2006-07-15
First make a root password
```
sudo passwd root
```
It will ask for a new Unix password. Enter the password you want for root. It will ask you to repeat it.
Next go to the top panel and enter into System<Administration<Login Window. When the window comes up, enter the Security tab. Check off the box that says "Allow local system administrator login". Close the tab and that is it.
When you next get to the login screen, you can enter root at the username and then the unix password you just made for the password. You will then be logged in as root.
Just use care when logged in as root. Your system is open to any change in configuration and any command is acted upon as root.

---

### Post by verbatim210 on 2006-07-15
hey catlett i never did any of this?  i just use the information i supplied during the first installation and that seems to function as root fine

do you know how to create a guest account using console?

---

### Post by catlett on 2006-07-15
You're initial account info will get you root powers no problem. Some people like to use su and some want to log in to a root session. To each his own. But this is a way to enable a root password so you can get a root terminal with su and by editing the login window, you can enter a root session.

Anyways, adding a guest account should be as simple as adding a user. I don't really use it so I am not that experienced with it. But adding a user doesn't make them a superuser. You have to add them to that group. So adding a user should just give them a basic access and no sudo powers. Add a user by entering 
```
sudo useradd whoever
```
Delete a user by entering 
```
sudo userdel whoever
```
This doesn't give them sudo powers. To give a user sudo powers, you have to follow up the useradd with one of 2 things. Edit the sudoers file by calling up the file with visudo ```
export EDITOR=gedit && sudo visudo
``` Then entering a line at the bottom like this 
```
whoever    ALL=(ALL) ALL
```
Or you can do it by entering them into the administration group 
```
sudo sudo adduser whoever admin
```
Check out the Dapper Guide. It gives a good base for a system. It will help you install the basics and give you the basic system commands. 
sudo adduser system_username admin

---

