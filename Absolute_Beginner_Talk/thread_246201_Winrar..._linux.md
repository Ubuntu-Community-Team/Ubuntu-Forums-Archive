---
title: "Winrar... linux?"
date: 2006-08-28
forum: Absolute Beginner Talk
---

### Post by sunrex on 2006-08-28
Well im not a beginner, but this is the best place for me to ask this.

is there anything on linux that can compair to winrar?

---

### Post by Toxicity999 on 2006-08-28
sudo apt-get install rar unrar

then just use the default Ubuntu Archive manager.

And I assume you have extra repositories enabled already as you say you aren't particularly a Beginner... I think this is on a non default one.

---

### Post by Bachstelze on 2006-08-28
Could you be more precise please ? What exactly do you want the program to do ? If you want to extract RAR files, install the unrar package.

---

### Post by sunrex on 2006-08-28
what i want it to do is be able to extract all file types out there, or at least a lot.

---

### Post by Bachstelze on 2006-08-28
Then have a look at [this](https://help.ubuntu.com/community/FileCompression).

---

### Post by Toxicity999 on 2006-08-28
Yea just enable the repositories noted there and combine it to a nice apt line like what I showed you, at that point the Gnome Archive Manager can read and write to those types. Easy.

---

### Post by BaidareW on 2006-09-06
This helped me :) I am going to try ubuntu (now winxp) and some programs is just a must for me, and one of these is rar..

---

### Post by empcrono on 2006-09-06
you want to make sure if you want to be able to unzip all types of rar files that you install unrar-nonfree you might have to add a repository to you repository. if you need more help then that i'll help just post

---

### Post by masked_marsoe on 2006-09-10
Every time I try to install this, I get > Package rar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rar has no installation candidate

How do I get it?

---

### Post by MiKuS on 2006-09-10
you should use automatix, it installs alot of stuff you will want

[http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38)

---

### Post by masked_marsoe on 2006-09-10
I do have that, and EasyUbuntu. They have the same problem.

---

### Post by theillbehaviored on 2007-05-18
> 
theillbehaviord@Mainframe:~$ sudo apt-get install rar unrar
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.



I keep getting this error message

HELP!

---

### Post by localgod11 on 2007-10-21
Automatix has been accused of breakng many, many systems you may want to read up on it before you install it


> **MiKuS said:**
> you should use automatix, it installs alot of stuff you will want

[http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38)

---

### Post by ubuntu27 on 2008-06-08
> **masked_marsoe said:**
> Every time I try to install this, I get 
How do I get it?


The package that you want to install is **unrar** not rar

Do this command at the Terminal:
```

sudo apt-get install unrar
```

---

### Post by ubuntu27 on 2008-06-08
> **theillbehaviored said:**
> I keep getting this error message

HELP!


As the message says, dpkg was interrupted. To remedy that do the instructed command.

Open the terminal and type (or you can copy and paste)

```
sudo dpkg --configure -a
```

Then do what you were trying to do ;)


EDIT: WoW! Look at the dates! I... well, what is done is already done.

---

