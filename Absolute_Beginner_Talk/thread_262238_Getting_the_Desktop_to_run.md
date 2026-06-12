---
title: "Getting the Desktop to run"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by dejan007 on 2006-09-21
OK, most of you will laugh and make remarks, but i will take the punishment.  I am Extremely new to Ubuntu/Linux and have just installed the LAMP server option.  what is the password for 'root' logon?  I have created a user per the walkthrough, but to do anything on the system i need to know what the default administrative account is that is created during the setup, can anyone help?  many thanks folks

---

### Post by hyper_ch on 2006-09-21
there is none... at least not directly... login with the user you created and then use "sudo" in front of each command and enter your user pwd...
Or I think you can, once you're logged in, to change to root if you enter "sudo -i" followed by your user pwd.

---

### Post by jordanmthomas on 2006-09-21
Typically, in Ubuntu, you append *sudo* to a command to gain root privileges for that one command as a safety measure.  
So, root has no password and cannot login by default.  If you want to give root a password, type 
```
sudo passwd root
``` as your user and you will be asked for your password, then you can create a password for root.

Alternatively, you can type
```
 sudo su
```
as your user to get an interactive root shell for a while, leaving root unable to log in normally.  (this is the way I suggest you get root)

...and...beaten

---

### Post by dejan007 on 2006-09-21
How do i run the gui for the desktop?

---

### Post by dejan007 on 2006-09-21
I used the following:

     lampuser@lampuser$ sudo aptitude -y install '~tubuntu-desktop

but that did not work, can't get the desktop to run.

---

### Post by dejan007 on 2006-09-21
Installed LAMP Server; logged in and typed the following to get the desktop to load, but with no success?  Any help in how to get the GUI running?

lampuser@lampserver$ sudo aptitude -y install '~tubuntu-desktop'

did nothing got the following:  could not find any package that matched tubuntu-desktop.  how can i view all the packages?  many thanks everyone.

---

### Post by jordanmthomas on 2006-09-21
```
sudo aptitude install -y ubuntu-desktop
```
or 
xubuntu-desktop
kubuntu-desktop

---

### Post by bulldog on 2006-09-21
Well yes,hmmm what do you want to install anyway?

tubuntu is not a known desktop environment,but it could be a new one offcourse.

---

### Post by jordanmthomas on 2006-09-21
try
ubuntu-desktop
xubuntu-desktop
kubunutu-desktop

**edit** 
hey, it's you from the other thread

---

### Post by bulldog on 2006-09-21
Maybe you could open another topic??

That will help for sure:sad:

---

### Post by RoyArne on 2006-09-21
> **dejan007 said:**
> how can i view all the packages?

The **aptitude** command by itself will let you browse the available packages. It has an arcane interface though.

---

### Post by Perfect Storm on 2006-09-21
No need to start new...

The two thread is merged.

---

### Post by dejan007 on 2006-09-21
Thanks guys, i am totally new to this but really, really want to learn, i really appreciate your help.

---

### Post by dejan007 on 2006-09-21
I have installed the x11 package from the LAMP install CD.  I cannot get the x11 consolet to work, any suggestions?

---

