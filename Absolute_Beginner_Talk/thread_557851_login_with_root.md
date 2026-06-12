---
title: "login with root"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by apparle on 2007-09-23
how to logon via root

---

### Post by Steveway on 2007-09-23
On Ubuntu we don't have a root-account.
If you need root-privileges for a program then ask the superuser to do it.
The command is sudo.
Just use:
sudo <programname>
or 
gksu <programname>
gksu is for graphical programs.

---

### Post by jw5801 on 2007-09-23
The root account is disabled by default in Ubuntu as it provides a potential security hazard and is also generally unnecessary. If you need to run a command from the commandline (or open an app via commandline) with root permissions, then prefix the command with "sudo" (minus the quotation marks of course).

What are you trying to do that requires root permissions?

---

### Post by exile on 2007-09-23
Do you mean have a root shell?

try:

sudo -s

then enter your password.

Or do you mean login at the login screen as root? Then you will have to enable the root account by setting the root password.

In ubuntu you can execute su commands by typing 'sudo <command>' then enter your password at the prompt.

---

### Post by lmlypfan on 2007-09-23
What is the command to temporarily open a GUI as root?

---

### Post by banewman on 2007-09-23
If you login as a user then go to - system - admin - login window - enter the password - then go to security tab - choose allow local system administrator login - then logout and login using root as the user. Most things you can do as sudo  - what is the issue ?

---

### Post by juantovarm on 2007-09-23
Ubuntu comes configured with disabled root. In order to activate root: you have tp change root's password through the terminal using sudo

In terminal type.
sudo passwd root

It will first ask you for your passwd and then for the new root passwd,

In order to relock root passwd just type in the terminal:
sudo passwd -l root 

Nevertheless being a child of debian, you might not be able to graphically log in under root in ubuntu, just as debian and unlike mandriva and such

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by jw5801 on 2007-09-23
What would you like to do with your root permissions? There's guaranteed to be a way to do it without needing to log out and back in again, or even enabling the root account. If you'd give us some more information we can help you out.

---

### Post by radioraheem8 on 2007-09-28
I'm trying to change ownership of a folder, that's how I stumbled onto this topic.  Friend recommended I set up the superuser, I've just been using the sudo commands, but the ownership of this folder is killing me!  

It's a vpnclient folder, I'm trying to add the .diff file into the directory, but it's locked and the owner is 1002.  I just tried sudo chown -R <user> <folder>.  Nothing happened.  Suggestions?

---

### Post by Kilz on 2007-09-28
> **lmlypfan said:**
> What is the command to temporarily open a GUI as root?

```
gksudo nautilus
```
Will open up nautilus as an admin without using root. Then move files, change permissions, and edit files to your hearts content.

```
ksudo konqueror
```
Will do the same thing with konqueror if you are using kde or kubuntu

```
gksudo thunar
```
Will do the same thing in xubuntu with thunar

---

### Post by jw5801 on 2007-09-28
```
sudo mv <file> /<folder>/<file>
```Will move it there, or use "cp" in place of "mv" to copy the file. If that doesn't work, post the error output here and we'll analyse.

---

### Post by Kilz on 2007-09-28
> **jw5801 said:**
> ```
sudo mv <file> /<folder>/<file>
```Will move it there, or use "cp" in place of "mv" to copy the file. If that doesn't work, post the error output here and we'll analyse.

True, but sometimes its easier to select then drag and drop. Like if you want just 8 files from a group of 50 that have nothing in common in their name.

---

