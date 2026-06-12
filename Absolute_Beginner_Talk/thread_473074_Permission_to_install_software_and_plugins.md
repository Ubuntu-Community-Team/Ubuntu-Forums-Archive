---
title: "Permission to install software and plugins"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by sachill on 2007-06-13
Hi 

I have a problem where when I try to install software.  I log in the terminal as superuser on my personal computer by typing 'su'.  It rejects my administration password, saying "su: Authentication failure". How can this be?? Only I use this PC and it is the same password I use to log in!! Please help!!!

---

### Post by gerscht on 2007-06-13
do 
```

sudo su

```
or just put sudo in front of the command you want to run (recommended), like
```

sudo apt-get install openoffice

```

---

### Post by sachill on 2007-06-13
So you suggest I type in " sudo apt-install skype-1.3.0.53-suse.i586.rpm" since 'skype-1.3.0.53-suse.i586.rpm' is the file I need to run from my desktop?

---

### Post by gerscht on 2007-06-13
> **sachill said:**
> So you suggest I type in " sudo apt-install skype-1.3.0.53-suse.i586.rpm" since 'skype-1.3.0.53-suse.i586.rpm' is the file I need to run from my desktop?
No, apt-get is getting the files via the repository, so no need to download them manually (*rpm is the wrong format anyway, ubuntu is using *.deb)
if you have downloaded a *.deb file, you would install it via
```

sudo dpkg -i filename.deb

```
Take a look over here, there are lotrs of ways explained, how to install software: [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware) for more information

---

### Post by GSF1200S on 2007-06-13
> **sachill said:**
> So you suggest I type in " sudo apt-install skype-1.3.0.53-suse.i586.rpm" since 'skype-1.3.0.53-suse.i586.rpm' is the file I need to run from my desktop?

Well, if youre using Ubuntu, than youd have to use alien to convert the .rpm to a .deb-

To install something:

sudo apt-get install openoffice

-or-

sudo aptitude install openoffice

apt-get and aptitude both 'get' things perfectly, but aptitude is better at removing the dependencies used by the program your removing (without removing depencies you need for others).

Im not familar with alien as Ive never used it...

---

