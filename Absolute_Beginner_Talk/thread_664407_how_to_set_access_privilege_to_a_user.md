---
title: "how to set access privilege to a user"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by darklight74 on 2008-01-11
Hello everyone ... 
im having problem getting my into manual configuration?
both of my other user access .. unable to unlock or enter the configuration due to no administrative access.
I do have root access. But i dont know to login as root in GUI .. the screen prevents login to GUI as root.  

How i can give administrative access to a username by command line?

---

### Post by jken146 on 2008-01-11
You really shouldn't enable logging in as root if you ask me.  It would be much safer (and easier) to add the necessary users to the **admin** group.  You can do this in System > Administration > Users and Groups by selecting the user you want, clicking on the Properties button, clicking on the Privileges tab, then ticking the box labelled "Administer the system".

---

### Post by Xavieran on 2008-01-11
You could go into recovery mode and do sudo passwd root WhateverYourPassIs
do a man passwd first though,to make sure...

---

### Post by darklight74 on 2008-01-11
> **jken146 said:**
> You really shouldn't enable logging in as root if you ask me.  It would be much safer (and easier) to add the necessary users to the **admin** group.  You can do this in System > Administration > Users and Groups by selecting the user you want, clicking on the Properties button, clicking on the Privileges tab, then ticking the box labelled "Administer the system".

thats the problem bro .. cant find any "Users and groups" at the designated row ..

---

### Post by plucky on 2008-01-11
darklight74,

Goto **System > Preferences > Main Menu > ** a gui will open, in the left column go to **Adminintration** click on that and in the right column make sure ** Users and Groups** box is filled in. You should now have Users and Groups in the system menu.


Good luck

---

### Post by capink on 2008-01-11
You have to options (I recommed option 1):

1. Add the user to the admin group from the command line:

```
sudo usermod -a -G admin username
```

2. Enable the root account so that you can access GUI as root. To this:

```
sudo passwd root
```

and enter the password you want to use for the root.

Now you can access GUI as a root. After solving your problems you can disable root:

```
sudo passwd -d root
```

---

