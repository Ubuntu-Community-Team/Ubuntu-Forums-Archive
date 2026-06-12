---
title: "root login trouble"
date: 2005-12-25
forum: Absolute Beginner Talk
---

### Post by evaderus on 2005-12-25
hi, I can't log in with root, not only do I not know the password, but I do not remember inputting it during installation. Is there a way to change my password, or edit any of the root login settings?

---

### Post by 23meg on 2005-12-25
Ubuntu doesn't create a root account during install. You should prefer to use [sudo]("http://wiki.ubuntu.com/RootSudo") instead. If you **must** have a root account, you can enable it with ```
sudo passwd root
```

---

### Post by evaderus on 2005-12-25
what is sudo? and it says I need to be logged in with my root account in order to set the permissions to view certain drives...

---

### Post by dueY on 2005-12-25
[QUOTE=evaderus]what is sudo? and it says I need to be logged in with my root account in order to set the permissions to view certain drives...[/QUOTE]

sudo is the SuperUser DO command.  It's there to help you not break your install.

---

### Post by evaderus on 2005-12-25
would it work, and how do I log in with it?

---

### Post by brummieman on 2005-12-25
I  had the same problem and asked yesterday...see this post...

[http://www.ubuntuforums.org/showthread.php?t=108001](http://www.ubuntuforums.org/showthread.php?t=108001)

:p

---

### Post by dueY on 2005-12-25
[QUOTE=evaderus]would it work, and how do I log in with it?[/QUOTE]

sudo is basically used one line at a time.  You type sudo then whatever commands you wanted to do.  It will prompt you for your account's password and you enter it.  You don't really "log in" with sudo, it's a command.

---

### Post by bscbrit on 2005-12-25
There are 2 main ways of running as 'root' in the various linux distros.  One allows you to actually log on as 'root' in the same way that you would as any other user.  While this might seem convenient, it does effectively remove several security features from the system.  Firstly, while logged on as root you can do anything - even something that deletes your entire installation.  Secondly, any program running does so with the same powers as its owner.  So even a program that misbehaves will not be stopped by the system from causing damage.
The second method, using 'sudo', allows you to assume root powers from your normal user area.  Each command that requires root powers must be preceded by the sudo command.  The first time that you use it, it will ask for a password.  It wants your normal user password, not a special password allocated to root.  It will give you root power for, say , 10 minutes after which you will have to reauthenticate yourself by giving your password again.  The main advantages of this are:
You are less likely to make a dangerous mistake because each command that you want to execute with root powers _must_ be preceded by sudo i.e. you have to make a conscious action and are less likely to do something by mistake.  Not cannot make a mistake - just less likely!
Secondly, as you remain logged on as a normal user, any program that you begin without 'sudo' will only run with normal user powers and the system can prevent that program from doing serious damage to the system.  It will not prevent a program from deleting data in your 'home' directory, but at least it cannot delete the entire installation or even change critical settings.

For more explanation, try this link:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

