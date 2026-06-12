---
title: "Logging in as root"
date: 2005-11-08
forum: Absolute Beginner Talk
---

### Post by homersimpson on 2005-11-08
Does anyone have a quick and simple way that I can log into Ubunto 4.10 as root user?

I have read all I can find in all the help areas but it will just not let me log in as root.

From a boot up, I get the login screen and type in username 'root' and a password set by every method I can find but it just clears the fields and sits there asking for the username again.

All I am trying to do is see if I can install a program to have a look at it, nothing has worked so far, and so I just want to delete the programs folder and start again but it will not let me do so as an ordinary user.

I am fed up with 'sudo' as nothing has worked using it for the install attempts so I want to get in as root which is what the 'readme' file on the program suggests.

I have also tried the switching user menu option, random password generator and even booting from the installation cd and entering' rescue' which simply brings up 'kernel not found'.

It's Last Chance Saloon for this OS and me I'm afraid, as I have now spent all my spare time over three days trying to do simple tasks with no results!

Don't worry about any security issues in any answer as I am only on a spare disc that has no important tasks.

Very grateful for any help and for the help I have had so far.

---

### Post by lreyes6 on 2005-11-08
on a terminal windows... **su ** and password?

---

### Post by 23meg on 2005-11-08
Create a root password with "sudo passwd root", then enable GDM login in System / Administration / Login Screen Setup / Security / Allow root to login with GDM.

Disclaimer: Don't do it. You can delete/remove everything with "gksudo nautilus" if you *must* do so.

Which program are you trying to install?

---

### Post by samih on 2006-01-18
Hi...
I have the same problem i can not log in as root user.
and i did not have root user password!!!
how can know the pass?

---

### Post by kaamos on 2006-01-18
Just do
```
sudo su
```
More info: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by phido on 2006-01-18
Ubuntu works works with *sudo, *to remove the folder u will need something like this [I]sudo rm -rf /folder.
[/I]If you really have to use the root account you have to set a password for root, dont know the command right now, but often talked in the forum.
h2h

ha ok :cool: thats threaded view, little late

---

