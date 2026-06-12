---
title: "installing java"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by gavinvasquez on 2006-12-31
im trying to install jre for frostwire but everytime i type su and enter it asks for a password which i dont have i tried using my login password but it aint working plz help

---

### Post by gavinvasquez on 2006-12-31
oh and im running 6.10

---

### Post by MkfIbK7a on 2006-12-31
try "sudo" instead of "su" and use your login password

---

### Post by taurus on 2006-12-31
Please use the sudo command with the password that you use to log in...  To install Sun's jre, you need to enable both universe & multiverse in /etc/apt/sources.list first.  So, open a terminal, Applications -> Accessories -> Terminal, and type

```
gksudo gedit /etc/apt/sources.list
```
Now, remove the # in front of all the lines that have universe and multiverse at the end or near the end (with deb at the beginning).  Save the changes and run

```
sudo aptitude update
```
Then, use synpatic, System -> Administration -> Synaptic Package Manager, and search for jre...

---

### Post by steve.horsley on 2006-12-31
When you use **su**, you are prompted for root's password. But in Ubuntu, root's password is disabled. The nearest equivalent, that gives you a command prompt as root is the command **sudo su**. In this case, you have to give your own password instead.

You can use **sudo** in front of any command to make it execude as root instead of as your user ID. So **sudo su** is actually running the su command as root - you have to give your password to keep sudo happy, but su doesn't ask for a password when root runs it.

---

### Post by PigCorpse on 2006-12-31
Okay, first enable all your repositories in /etc/apt/sources.list. Uncomment every address line.

Then,

sudo aptitude install sun-java5-jdk
Agree to all the license terms that come up.

Then, 

sudo update-alternatives --config java

And set the Sun JRE as the default, rather than the GCJ one.

---

### Post by gavinvasquez on 2006-12-31
when i type sudu at the terminal i get bash: sudu: command not found
admin@seven-of-nine:~$

---

### Post by Sef on 2006-12-31
> when i type sudu at the terminal i get bash: sudu: command not found
admin@seven-of-nine:~$

The command is **sudo**, not sudu.

---

### Post by MkfIbK7a on 2006-12-31
just wondering did my suggestion help?

---

### Post by gavinvasquez on 2006-12-31
yes tnx guys

---

### Post by MkfIbK7a on 2006-12-31
no prob thats what we are here for:D

---

### Post by Sef on 2006-12-31
You're welcome.  Please post any other questions that you have.

---

