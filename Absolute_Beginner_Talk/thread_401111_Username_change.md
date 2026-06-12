---
title: "Username change"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by owerio on 2007-04-04
Hello. During the installation process I have miswritten my username. Therefore I need to change it. I used Preferences/Users way but it didn't change my home directory and computer name appropriately. How can I fix the issue?
Thanks.

---

### Post by mikeyphi on 2007-04-04
Have a look here -  [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)
you might find the way to do it!

---

### Post by hyper_ch on 2007-04-04
Ok, first copy the home dir to the new location (in command terminal)

```

sudo cp -R /home/OLDUSER /home/NEWUSER

```

Then change the home dir of the user
```

sudo usermod -d /home/NEWUSER NEWUSER

```

Then logout and log back in and remove the old home
```

sudo rm -Rf /home/OLDUSER

```

Computername is different from the username. Those aren't related. I think the computer name can be changed somewhere in the network settings.

---

### Post by owerio on 2007-04-04
> **hyper_ch said:**
> Ok, first copy the home dir to the new location (in command terminal)

```

sudo cp -R /home/OLDUSER /home/NEWUSER

```

Then change the home dir of the user
```

sudo usermod -d /home/NEWUSER NEWUSER

```

Then logout and log back in and remove the old home
```

sudo rm -Rf /home/OLDUSER

```

Computername is different from the username. Those aren't related. I think the computer name can be changed somewhere in the network settings.

Hello . After I log out I cant log 'nto my desktop anymore. It says the home directory must be directed to a user. What to do now.

---

### Post by hyper_ch on 2007-04-04
can login at the terminal?

If so, try this:

```

sudo chown -R NEWUSER:NEWUSER /home/NEWUSER

```

---

### Post by owerio on 2007-04-04
> **hyper_ch said:**
> can login at the terminal?

If so, try this:

```

sudo chown -R NEWUSER:NEWUSER /home/NEWUSER

```

Hello. The terminal output

> chown NEWUSER:NEWUSER  group is not valid

I didnt work.

---

### Post by sisco311 on 2007-04-04
```
sudo chown -R NEWUSER:OLDUSER /home/NEWUSER
```

---

### Post by compmodder26 on 2007-04-04
Just do "sudo chown -R NEWUSER /home/NEWUSER" for now.  This should get you into your desktop.  You can then create a new group for your new username using the users and groups dialog under System->Administration->Users and Groups.

After that, in a terminal, type "sudo chgrp -R NEWGROUP /home/NEWUSER".

*Note: Obviously replace NEWGROUP and NEWUSER with the new group and user names you created.

---

### Post by hyper_ch on 2007-04-04
And if that doesn't work post the following outputs here:

```

whoami

```

```

ls -al /home

```

```

tail -n100 /etc/group

```

```

tail -n100 /etc/passwd

```

---

### Post by owerio on 2007-04-04
> **compmodder26 said:**
> Just do "sudo chown -R NEWUSER /home/NEWUSER" for now.  This should get you into your desktop.  You can then create a new group for your new username using the users and groups dialog under System->Administration->Users and Groups.

After that, in a terminal, type "sudo chgrp -R NEWGROUP /home/NEWUSER".

*Note: Obviously replace NEWGROUP and NEWUSER with the new group and user names you created.

Hello. Thanks . It helped. But I didnt understand why I should create a new group. Because I have removed the  old username home directory as other friends described. Till now I used these commands;



> sudo cp -R /home/OLDUSER /home/NEWUSER



> sudo usermod -d /home/NEWUSER NEWUSER




> sudo rm -Rf /home/OLDUSER


> sudo chown -R NEWUSER /home/NEWUSER

Could you please explain  Group creating? Thanks to all of you again.

---

### Post by owerio on 2007-04-04
Hello . after the 4 command do I still need to a new group? I dont have any problem now. But the OLDUSER group resides in System->Administration->Users and Groups

---

