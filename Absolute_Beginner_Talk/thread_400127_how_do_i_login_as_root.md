---
title: "how do i login as root?"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by colonist on 2007-04-03
how do i login as root?  I'm trying to install ntfs for linux and it needs me to be logged in as root.

---

### Post by kc5hwb on 2007-04-03
login to the GUI?  Or with command line?

cmd line:
sudo passwd root
create a new password and confirm

---

### Post by palmerthegeek on 2007-04-03
Ubuntu uses [sudo] which is a super user... aka root.   When installing really anything you can use sudo.   

example for the ntfs:  
sudo apt-get install ntfs

when ubuntu prompts you for a password, enter your user password.

Hope this helps.

---

### Post by TitanKing on 2007-04-03
> **colonist said:**
> how do i login as root?  I'm trying to install ntfs for linux and it needs me to be logged in as root.

This question is being asked allot. You would normally use sudo in front of your command or application to run things as root. The password is your normal login password. Some people prefer using root though, so as mentioned above after creating a password for root you can continue logging in as root as usual...

---

### Post by Obor on 2007-04-03
Use sudo instead.  [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by bikeboy on 2007-04-03
That's what sudo is for. In Ubuntu there are rarely any circumstances you need to actually enable the root account.

A good place to have a read is the [RootSudo community doc](https://help.ubuntu.com/community/RootSudo).

edit:
Doh! Beaten. But just so you know, there are some occasions where you need to enable the root account. If you need to do that (ie. sudo or sudo -s don't work) post back for how to temporarily do that.

---

### Post by carverj on 2007-04-03
You cannot login as root in Ubuntu as far as I know. You must change to root user via the command line with the sudo su - command. **WARNING** One must be careful with this power, and you should use it sparingly by changing back to regular username straight away,
such as, su jeremy -
The dash is apparantly to retain the environment. But not sure whether that means the command history for that user??

---

### Post by finferflu on 2007-04-03
Never login as root, it puts your security at risk. Always use sudo. The root password is disabled by default and it must be left so. Anyway, you never need to login as root on Ubuntu.

If you need to be root in a terminal, you can run this command:

```
sudo su
```

---

### Post by Skrynesaver on 2007-04-03
Actually you can **S**witch **U**ser to any user using su, however to switch user in such a way as to inherit the new users environment you must use a - thus```

su skryne - 
``` asks me for skryne's  password and reads their environment settings
```
sudo su skryne -
``` asks me for **my** password and then switches to skrynes a/c using skryne's settings.
sudo **do**es things as the **s**uper **u**ser  su switches user, if no username is given it defaults to root and finally to enable an account for root
```
sudo su -
passwd

```

---

### Post by Peter1234123 on 2007-04-04
In order to use root on a command line you must type "sudo passwd root", the unix command to add a root account, it will ask you for "UNIX PASSWORD" and give the password that you would like as root, to log onto KDE or GNOME as root is harder, you must change some config files, I saw a post, but I don't remember where, on how to log on to KDE or GNOME as root, looking atm.

---

