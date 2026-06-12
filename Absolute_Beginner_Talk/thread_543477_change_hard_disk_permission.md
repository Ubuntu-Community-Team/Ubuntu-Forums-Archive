---
title: "change hard disk permission"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by Ice_man^^ on 2007-09-05
I've installed ubuntu 7.04 4 days ago and I can't change the permission of the hard drives.
The owner of Disk and Disk 1 is the root account but I cant log in whit the root.The file system is ext3.I've changed the root password but whet I try to log in - "the system administrator cant log in from this screen". :(

---

### Post by mikewhatever on 2007-09-05
I think the problem is that it is mounted with wrong permissions. Check the link, bottom of the page [http://psychocats.net/ubuntu/mountlinux](http://psychocats.net/ubuntu/mountlinux)

---

### Post by Ice_man^^ on 2007-09-05
I cant understand some of those thing in that link ..........

---

### Post by hyper_ch on 2007-09-05
What can't you understand in that link?

---

### Post by Ice_man^^ on 2007-09-05
Where should I add /dev/hda5 /storage ext3 defaults 0 0 ?????

---

### Post by vanadium on 2007-09-05
mikewhatever refers to the "sudo chown" and "sudo chmod" commands. In a unix/linux system, users can only write into their home directory by default. this is a very good approach, because this way, it is hardly possible that one user breaks the system (by accident or intentionally).

Drives by default belong to the root user. You can give an entire drive to a particular user by changing the ownership of the mount point, this is the directory through which you can reach the drive.

I prefer another approach, though. I suggest to create a directory on the drive (as a root) and give that directory to the user, instead of the root folder of the drive. If you have more users, you can do the same for them as well. You create the directory as root, of course, because only the root can write. You can do this with the command line

sudo mkdir /media/Disk/userdata

or using Nautilus as root ("gksudo nautilus").

Then, you give the directory to the user

sudo chown youruser:youruser /media/Disk/userdata

You can also do this with nautilus as root.

From this point, it is an excellent idea to create a symbolic link to that directory under the home directory of the user. That way, the user will be able to reach his space on the drive from within his home directory (where al his other data are as well).

sudo ln -s /media/Disk/userdata /home/youruser/userdata

would create a directory (in fact a link) userdata in the home directory of user "youruser". The user will now see what looks and behaves as a new directory in his home folder. Going to that brings him on the drive.

Again, you can use a root nautilus as well: right-click the directory  userdata on the drive, select "Make link". A link named "Link to userdata" is created in the same directory where userdata lives. Now move this link to the home directory of the user and rename it simply to "userdata" (or a name of your choice).

---

### Post by mikewhatever on 2007-09-05
As vanadium kindly pointed out, I was referring you to the permission section.
> Now I need to give it the proper permissions. Let's just assume, for this example, that my username is marie.
sudo chown -R marie:marie /storage
sudo chmod -R 755 /storage
You do not need to mount it, since it seems to be mounted already. You mount point may different then /storage. Drives are often mounted in /media. If this is too confusing, post the output of the following > cat /etc/fstab

---

### Post by nilufer on 2007-09-18
hi. you have tried to login as root using the login screen.
by default it is restricted and not allowed.
but if u want to login as root.do as follows.

go to System -> Login Window
then it will ask you the password. type in ur password.
then it will show you a window.
from it you can select your preferred login screen among several given by default.
there is a tab called security.
open the tab.
you should see a unchecked checkbox called 
"Allow root (administrator) to login using XDM"
check it.
then close it.
now you should be able to login as root.

to change the root password, do one of the following 
in the terminal type
```

1) sudo passwd root
it will ask ur password. so type it
then it will ask new password for root. type the password 
and retype againg when it asks.
that's it. you have changed the password for root.

```
or
```

type 'sudo su' and enter
type ur password
now you are root.
type the command 'passwd' and enter
type the new password.

```

to login as root type 'su' enter
give ur new password.
it should work.


> Though possible, it is disabled by default because of security reasons. Anything you do to the system areas will be reflected. so it is not a good idea to login as root graphically. always login using your account and use the terminal to log as root. you can do whatever using ur own account. just use the terminal for administrative purposes. i don't enable this in my ubuntu.  

---

### Post by matty_b_1000 on 2007-09-18
I have a similar problem... I want to change the owner of one of my disks from root to me. I open Nautilus as root, navigate to the drive's folder in /media, right-click > properties, permissions, owner, scroll down and select my username. It stays on that for about a second, then becomes root again. What is going on?

---

