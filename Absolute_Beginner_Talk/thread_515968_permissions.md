---
title: "permissions??"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by safora on 2007-08-02
Hi there,

I'm just trying to install DDclient from DynDNS and as i'm new to linux i'm struggling with everything!!

Anyway it says I do not have permission to copy the DDclient to the /usr/sbin directory

I tried in terminal and in windowed mode and no joy, help please!!??!


Thanks a million

sa-fora

---

### Post by Inxsible on 2007-08-02
> **safora said:**
> Hi there,

I'm just trying to install DDclient from DynDNS and as i'm new to linux i'm struggling with everything!!

Anyway it says I do not have permission to copy the DDclient to the /usr/sbin directory

I tried in terminal and in windowed mode and no joy, help please!!??!


Thanks a million

sa-fora

Did you try a sudo before the command in the terminal ?

```
sudo cp <path to the file to copy> /usr/sbin
```

---

### Post by zeekay on 2007-08-02
Probably because you must be root to copy inside those directories.

Try using "sudo" before the command:
```
$ sudo cp <file> /usr/sbin 
```

---

### Post by safora on 2007-08-02
That worked thanks:):):):), how do you use sudo in windowed mode?

---

### Post by Inxsible on 2007-08-02
> **safora said:**
> That worked thanks:):):):), how do you use sudo in windowed mode?

in a terminal type in

```
sudo nautilus
```that will log you in as root in nautilus and you can cut copy paste to your hearts content. 
But [COLOR=Red]BEWARE !! This is not recommended since you can seriously harm you system if you don't know what you are doing.[/COLOR]

It's much better to do something like this in the terminal, because the sudo only applies to that one command and not the subsequent commands. 



Now if you use su instead of sudo....well......

atleast that much of typing will knock some sense into you before you do something foolish ;)

---

### Post by asmoore82 on 2007-08-02
ddclient is already in the software repositories and can be installed automagically with the command
```
~$ sudo apt-get install ddclient
```
:KS

---

### Post by zeezan on 2007-08-03
Why we cannot login as root in terminal?

---

### Post by atomkarinca on 2007-08-03
> **zeezan said:**
> Why we cannot login as root in terminal?

try
```
su
```

---

### Post by zeezan on 2007-08-04
zeezan@ihost:~$ su
Password: 
su: Authentication failure
Sorry.
zeezan@ihost:~$ 


still cannot login as root

---

### Post by wormser on 2007-08-04
> **zeezan said:**
> zeezan@ihost:~$ su
Password: 
su: Authentication failure
Sorry.
zeezan@ihost:~$ 


still cannot login as root

Ubuntu disables the root account as default.  It is highly recommended not to log into root but use **sudo** and gksudo (for gui apps) to get root privileges.  So do not do it.  For your knowledge to set up root use passwd command to set up a password for root.

```
sudo passwd root
```

Then put your user password to get privileges to run the command then it will let you create a password for root.  But, do not do it.  Use sudo and gksudo instead because there is no reason for you to use root.

---

### Post by zeezan on 2007-08-04
Thanks , i just want to know and explore ubuntu linux congfiguration and want to test the code.

---

### Post by bodhi.zazen on 2007-08-04
> **Inxsible said:**
> in a terminal type in

```
sudo nautilus
```that will log you in as root in nautilus and you can cut copy paste to your hearts content. 
But [COLOR=Red]BEWARE !! This is not recommended since you can seriously harm you system if you don't know what you are doing.[/COLOR]

It's much better to do something like this in the terminal, because the sudo only applies to that one command and not the subsequent commands. 

```
sudo nautilus
```

Should be ```
gksu nautilus
```

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

> **zeezan said:**
> > zeezan@ihost:~$ su
Password: 
su: Authentication failure
Sorry.
zeezan@ihost:~$ 

still cannot login as root

LOL

Try ```
sudo -i
```

---

### Post by Aurdal on 2007-08-04
> **zeezan said:**
> zeezan@ihost:~$ su
Password: 
su: Authentication failure
Sorry.
zeezan@ihost:~$ 


still cannot login as root

If you really want to log in as root in the terminal (not at all recommended) try "sudo su".

---

### Post by coolen on 2007-08-04
I cannot tell you how thoroughly this question has been answered.
sudo will allow you to execute a single command with root priveleges. The password is saved for fifteen minutes to avoid furstration, but every root command must begin with sudo.
gksudo will give you a graphical password prompt (kdesu for Kubuntu, I believe). This, too, will save your password for fifteen minutes.
sudo -i will give you a root terminal. Not recommended, but in some cases, rather useful. Use with caution, and don't forget to log out.

Between these options, there's really no need to activate the root password.

---

### Post by Nekiruhs on 2007-08-04
> **coolen said:**
> I cannot tell you how thoroughly this question has been answered.
sudo will allow you to execute a single command with root priveleges. The password is saved for fifteen minutes to avoid furstration, but every root command must begin with sudo.
gksudo will give you a graphical password prompt (kdesu for Kubuntu, I believe). This, too, will save your password for fifteen minutes.
sudo -i will give you a root terminal. Not recommended, but in some cases, rather useful. Use with caution, and don't forget to log out.

Between these options, there's really no need to activate the root password.
Quoted for truth.

---

### Post by zeezan on 2007-08-06
hehe... I mean sudo -i is what i want to use ...thanks all

---

