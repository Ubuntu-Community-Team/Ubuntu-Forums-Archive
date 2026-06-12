---
title: "Can we get a GUI with root access"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by asimmittal on 2007-12-28
Hi,

I have two computers, a desktop (Intel Core2 duo) and a laptop (Pentium 4). On the desktop i have fiesty and on the laptop i have installed dapper. I dont have access to the internet on my laptop, cuz the desktop is at work and the laptop at home. 

I went to System>Adminstration>User and Groups. 

On fiesty, on the desktop, I can see root as a user... but not on the laptop (dapper). Also I can change the root password on fiesty. Since I cant see the root as a listed user on dapper, I cant change any properties. But when I try to create a user called root on dapper, it prohibits it saying that 'root' already exists. 

If it does how do i access root without knowing what the root password is. I dont wanna use sudo commands. When we press Ctrl+Alt+F1, we lose the GUI and come down to the terminal. How do i log on as the root without knowing its password. And why don't we have access to root anyway... I am the only user, its my OS... I should be able to access root or whatever place i want to. 

A friend of mine uses Red Hat and logs on as root every time. 

If I try to log on as root (on fiesty) from the GUI login window, it says "admin cannot login using this screen"... does that mean there is no other way to login as root except for at the terminal?? If so, that sucks.

Please help!?!

---

### Post by jken146 on 2007-12-28
Ubuntu uses sudo.  You can accomplish anything that root can do with sudo.  [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by nunnst on 2007-12-28
Try ....
```
$ sudo -s
```
This should allow you to enter multilple commands under sudo, without having to type it each time.

Good luck!

---

### Post by Zack McCool on 2007-12-28
There is a reason for the security model that Ubuntu uses.  It is the same reason that your machine is pretty near impervious to virus an malware attempts.

Should you choose to do it, the easiest way is to type ```
sudo -i
``` to get a root terminal prompt, then type ```
passwd
``` and enter the password you want for root.  That will set the password and unlock the root account.

Be aware of the drawbacks, though.  The most obvious is hacking attempts.  In order to gain access to your system, a person needs an ID and Password.  To hack a system with root disabled is not impossible, but it is more difficult, as they need to find out what user account you are using.  Joe or Mike or SlickWillie are not standard accounts found on every machine.  root is.  So now we have an account, and we can work on a password.

What is the problem with sudo?  If you need to type only one command with priv's, you just type sudo <command> and enter your password.  If you need a shell for several commands, use sudo -i, and you'll be logged in as root for as long as you like.  It's just more secure...

Running X as root and browsing the internet like that is just plain stupid.  Of course, you have the choice to do it.  I won't stop you.  I also don't care if you jump off the brooklyn bridge.  I'll still consider it stupid, though...

Either way, enjoy!

---

### Post by The Cog on 2007-12-28
<lecture>
You should not be using root as your normal login. Read here for an explanation:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
</lecture>

You should find that gaining root priviledge in a terminal with the command
**sudo -i**
or launching a root-priv nautilus with the command
**gksudo nautilus**
is prety-much all you ever need.

If you choose to ignore this advice, you can give root a password with the command:
**sudo passwd root**
and under System->Administration->Login Window, you can choose to allow root login.

---

### Post by LinuxIsInnovation on 2007-12-28
Try 
sudo nautilus

Thats all you need.. but be careful !! ;)

---

### Post by jordanmthomas on 2007-12-28
It sounds like you're wanting to log on as root.  You'd need to give root a password.

```
sudo passwd root
```
enter your password and then you can set root's.
Now you can log on as root, but to log into gdm as root you have to go into system --> administration --> login window and enable local administrator logins.

also, security, dumb idea, etc.

**edit**
nevermind, someone said this exact thing above.  Sorry.  Ignore this post (guess this should go at the top, huh?)

---

