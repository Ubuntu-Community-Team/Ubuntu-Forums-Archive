---
title: "Vmware on Ubuntu"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by UnXpected on 2006-04-19
Ok, so i have this problem..  and I'm completely new to Ubuntu. Not a newbie with computers though..

Someone installed Vmware for me on Ubuntu. I've worked with it once but the next day when he was gone and i tried to start vmware i see it apear on my taskbar for a few seconds saying: "Starting VmwareServer" and then it's gone and no application has started.

I'm thinking because he started it through terminal? (i'm just ranting >_<)

When i checked the Home folder I see a vmware directory with a yellow square with a lock in it. Assuming this means it's being secured with a password? I'm Not sure if this is the location of the user's home directory or a vmware directory.  When i open the directory I see an empty directory with no VMware files.  I know the Root password so basicly that's not the problem. The administrator username is Vmware..

I tried to install the VMware-server again but when i'm in the terminal and try to do SU root  and type the password it says i got the wrong password >_<

My main objective is to get Vmware booted up, so i don't mind trying to install it again! 

Please help

---

### Post by UnXpected on 2006-04-19
could someone at least try to help me run through the installation?

---

### Post by lg3 on 2006-04-19
Maybe it was installed in root or only has root permissions. have you tried to run it from the terminal?

I am also very new to Ubuntu and linux. 

I am interested in a walk through installation.

Anyone got one somewhere to post?

---

### Post by UnXpected on 2006-04-19
what's the command to run it through the terminal?

---

### Post by AndyCooll on 2006-04-19
IIRC the vmware folder and items need to be owned by the person trying to run the VMWare program (the fact that it has a lock on it means you are currently not the owner). To do this, at the command line you type:

```
sudo chown -R yourname /address/of/vmwarefolder
```

You might also need to change the group of the vmware folder. This is similar

```
sudo chgrp -R yourname /address/of/vmwarefolder
```

:cool:

---

### Post by Borniet on 2006-04-19
The problem will most probably be that you are indeed not owner of the files. The commands as AndyCool said should solve this.

---

### Post by UnXpected on 2006-04-19
woohoo, that worked! 

Thanks

---

