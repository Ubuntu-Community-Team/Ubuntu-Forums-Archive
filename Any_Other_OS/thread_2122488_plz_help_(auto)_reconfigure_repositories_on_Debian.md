---
title: "plz help (auto?) reconfigure repositories on Debian via cli"
date: 2013-03-05
forum: Any Other OS
---

### Post by Nikolai D. on 2013-03-05
Hi there,
Just installed a Debian 6 VM. Now the local repos i have chosen during install do not work or something like that.
I get temporary faliure resolving repo.
How do i reconfigure this? Cuz i want to install vim to setup static ip address.
Ive googled abit already, and im googling some more now. Ill let it know if i have some progress.
Thanks in advance,
Nikolai

---

### Post by Cheesemill on 2013-03-05
You can use vi to edit your /etc/apt/sources.list file. Vi is already installed by default in a Debian installation.

If you need to find out what changes to make you can use the Debian sources.list generator here...
[http://debgen.simplylinux.ch/](http://debgen.simplylinux.ch/)

---

### Post by varunendra on 2013-03-05
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by kiyop on 2013-03-05
Have you got root privilege?
Execute
```
su -
```
and then, type root password.

Can your installed debian access to internet?
```
apt-get update
```

What is the current /etc/apt/sources.list?
```
cat /etc/apt/sources.list
```

Maybe nano is easier than vi. I hope nano is installed on your debian.
```
nano /etc/apt/sources.list
```
Ctrl+k to cut (and copy) a line. Ctrl+u to paste it. Ctrl+o to save. Ctrl+x to quit nano.

---

