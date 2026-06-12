---
title: "synaptice package manager"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by keithpaw on 2008-03-21
Hi all
how do I install compiz from the synaptice package manager
the boxes in the manager are shaded for compiz and compiz plugins
but the options are not available in apperance preferances
i also have used envy for my nvidia card drivers they are installed ok
speck 
asus crossfire M/B duel core proccesor 2 GB ram 6600GT PCI express Graphics
internal 250 sata HD external WD 320 GB
thanks all
Keith

---

### Post by buntu_Geek on 2008-03-21
no need for synaptic...
goto terminal... and type the following...

```

sudo apt-get install compizconfig-settings-manager

```

This will give you a new menu in your preferences...

System >> Preferences >> Advanced Desktop Effects Settings 

Go there and enable cool plugins...

---

### Post by keithpaw on 2008-03-21
im getting this !

keith@keith-desktop:~$ sudo apt-get install compizconfig-settings-manager
[sudo] password for keith:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
keith@keith-desktop:~$ sudo apt-get install compizconfig-settings-manager
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
keith@keith-desktop:~$

---

### Post by billgoldberg on 2008-03-21
> **keithpaw said:**
> im getting this !

keith@keith-desktop:~$ sudo apt-get install compizconfig-settings-manager
[sudo] password for keith:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
keith@keith-desktop:~$ sudo apt-get install compizconfig-settings-manager
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
keith@keith-desktop:~$

Close synaptic before running the command

---

### Post by keithpaw on 2008-03-21
Now its workin thank you very much i have been trying to get this thing goin for hours (and three ubuntu installs:)

---

### Post by buntu_Geek on 2008-03-21
It is what all ubuntu users proud of... the security.... Any updates done can be done only by a single source...

I love ubuntu coz of this fantastic functionality...

Btw dont forget to mark the thread as solved ..... :)

It will be one of the options in the thread tools ( at the beginning of this thread...

---

