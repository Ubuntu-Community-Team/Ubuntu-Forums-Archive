---
title: "Wine Uninstall Help"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by james.gravley on 2007-06-01
Ok guys, I've got an easy one for you (I am still very new to Ubuntu). I tried Wine and realized I hate it. I am going to go with VirtualBox instead. Anyway, I have two questions. 

1. How would I go about uninstalling a program installed with Wine? (I have tried the obvious route and the program is still in the uninstall list and none of the files are removed)

2. What is the best way to uninstall Wine? (I am almost positive there is a command but I have no idea what it would be.)

Thanks for the help.

jmg

---

### Post by S29K on 2007-06-01
To get rid of wine completely simply remove the package and delete the .wine folder from your home folder.  All installed apps will go with it.

sudo apt-get remove wine
cd
rm -R .wine

---

### Post by Hobo Joe on 2007-06-01
A better command would be:
```

sudo aptitude purge wine

```

That should get rid of the folders and configuration as well.(I think)

---

### Post by james.gravley on 2007-06-01
It worked. Well, it uninstalled wine and then I just deleted the files for the program that was installed with wine. Once again, thanks.

jmg

---

### Post by lukanikos on 2007-07-10
used the last command and got that...

```
lukanikos@lukanikos-desktop:~$ sudo aptitude purge wine
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
lukanikos@lukanikos-desktop:~$ 
```


Is it correct?

---

### Post by S29K on 2007-07-11
This message typically appears when you try to use the terminal to install/remove something while you have Synaptic open.  Close Synaptic and try again.

If this isn't the case, post again and we'll try something else.

---

### Post by lukanikos on 2007-07-11
Uninstalled!!

Thanks!!

---

