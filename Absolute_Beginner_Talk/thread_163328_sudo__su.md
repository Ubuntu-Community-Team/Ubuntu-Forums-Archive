---
title: "sudo / su"
date: 2006-04-20
forum: Absolute Beginner Talk
---

### Post by Ecthelion on 2006-04-20
Hi, I was wondering, most time when you want to use root powers you use sudo and then have to give your password.
What is su for then?
I know it stands for superuser, but when i type su, it asks me for a password i don't seem to know...
It's anyway not the same password as for sudo, and it's not the password i had to gave in when i installed Ubuntu...
Is it a default password or aren't we suposed to use su? (which I doubt...)

Well, I'm just being curious about su...
Thanks for ALL information!:wink:

---

### Post by red_shrike on 2006-04-20
well su will log you ina as a superuser. For example, if I start terminal now it will say $ shrike@omikron $ and if I type root, it will log me in as root which means using sudo is becoming obsolete. (than I would get root@omikron: $) to get the correct passwrod for the root user type this

$ sudo passwd root
$ enter new UNIX passwrod: (enter some password for root)
$ confirm password... (confirm it)

now you can log in as root, which is an administrator. YOu can do this from gdm, but you can enable it. Remmember that as root you can delete everything, without being warned. This includes all system files, killing of all processes and eriting to all files anywhere on the disk; without using sudo. So be careful. Use this when u have a lot to write, so u dont have to use sudo all the time

---

### Post by nickj6282 on 2006-04-20
On *most* Linuxes the **su** command lets you temporarily log in as root (or some other user) without having to use sudo for every command. Since the root user is more or less disabled in Ubuntu, you can't just do a **su** to start a root session. Instead it's **sudo su**.

HTH
-Nick

---

### Post by Randomskk on 2006-04-20
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by catlett on 2006-04-20
Ubuntu and has made an easier way to become root, sudo (superuserdo). Ubuntu is based on Debian and Debian does not use sudo it uses su. That is why su is there as well.
Su is a way to let the computer know you are switching users. It isn't just a way to become root. You could also su user1 or su user2 etc.
In Linux you have to be root to make changes to anything that isn't in your home folder.
Way back when to become root you had to log out as user. Log in as root. Perform a command. Log out as root. Log in as user. To cut down on time su was created. Now you can change user/root status at the terminal. You type su then root. Give root's password and your root. Do your commands and when done type su and user, now your back to user.
Sudo took it one step further. When you type sudo you invoke root priveleges for that one command. You don't have to switch to root's account and then switch back. You just type sudo and your command. You type your password (this is important because there is a superuser file that you have to be in to use sudo. If your user account isn't part of the file sudo powers will be denied. But Ubuntu set up the file during install). This way you have root power for that command and then it goes away. No need to switch back to user. It just simplifies the change in status.

---

### Post by rubrboots on 2006-04-20
Great explanation catlett

I finally understand sudo and su. Thank you:p

---

### Post by Ecthelion on 2006-04-21
Yep, tx a lot...
I seem to learn more with every posted message...

---

### Post by gr0kzer0 on 2006-04-21
I enabled root login so if i had a lot of administrative tasks to do. But i've hardly used it cos - this is the way it seems anyway - if you do sudo, it stays active for a while, so if you use sudo again shortly afterwards it doesnt ask for your password.

---

