---
title: "No Administrator acc ?"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by Randomwkh on 2007-11-05
Installed ubuntu on a VMware machine today (first linux ^^) and well, methinks i messed it up or im just a noob xD. I was trying to install something (vmware tools) and it said i had to have super user privaleges... so i tried making my account into root (yar noob¬¬) cos im not sure how to get the privaleges even tho im admin... 

After a while i ended up somehow removing my admin privaleges so now i cant do much on my acc (cant get onto user groups). any ideas how to get admin back and have super user privaleges ?

---

### Post by mivo on 2007-11-05
Ubuntu is a little different. Try:

```

sudo -i

```

---

### Post by Ferri on 2007-11-05
In Ubuntu there's no root account by default. Also by default, the first user you create at install can gain administrative privileges through the "sudo" command. You need administrative privileges to change this, so I'd guess you haven't really lost them. Just go to the command line and put something like that:
```
sudo whatever_command_you_need
```
It will ask you a password; it's just the same you use to login to Ubuntu.

---

### Post by Randomwkh on 2007-11-05
thx for reply... just says sorry my user cannot run it.

If I rly did mess it up dont worry about anything too complex, ill just reinstall and try and find out how to have super user properly.

edit: just saw your reply Ferri... So that sudo -commands is for installing packages right? but i still have applications missing from system etc. Unless theres a command to get the admin back which i dont know ><

---

### Post by psusi on 2007-11-05
Knowing if you messed up would require that we know what you did.  "Messing about" is not enough information to go on.

---

### Post by Randomwkh on 2007-11-05
I think i removed myself from the admin group =/

---

### Post by psusi on 2007-11-06
Well, you can boot into rescue mode and check if you are in the admin group, and add yourself if you aren't.

---

### Post by aysiu on 2007-11-06
> **Randomwkh said:**
> I think i removed myself from the admin group =/
Then follow this tutorial to add yourself back:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

