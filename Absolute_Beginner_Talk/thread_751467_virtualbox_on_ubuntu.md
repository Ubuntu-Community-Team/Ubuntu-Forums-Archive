---
title: "virtualbox on ubuntu"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by vinceUUUU on 2008-04-10
Hello Forum people,

Please can you help me to get Virtualbox going...on my pentium 3 ubuntu here...

VB installed and runs fine.

When i try to put Dam Small Linux onto a virtual machine...it gives the following error message
=================================

The VB kernel driver is not accessible to the current user
Make sure the user has write permissions for /dev/vboxdrv by adding them to the vbox usersgroup.

you will need to reboot your machine after this...

=================================


so how do i do that step above?

what is the command i need to type and where do i need to go in a terminal to do it?

thanks

Vince.

ps...i assumed that Dam small Linux was a 2.2 linux distro?...right?

---

### Post by Therion on 2008-04-10
System menu > Administration > Users and Groups > Manage Groups

Select the “vboxusers” Group > Properties > check any users you want to be able to use VB.

Now log out, and log in again for these changes to become effective.

---

### Post by thegreenblob on 2008-04-10
Go to: System>Administration>User and Groups

Then go to Manage Groups, and look for "vboxusers".

Click properties and make sure your name is checked after that, click ok and reboot.

---

### Post by smurphy_it on 2008-04-10
Right click on the username in the taskbar (assuming you have user switcher in your taskbar -- which is default), then choose edit user's and groups.

Click on your userid and then click manage groups.
Scoll and hi-light vboxusers and click properties.
Place a checkbox next to your name.

Hit ok and close... Close out the rest of the windows, and reboot.

Upon logging in you should have the rights.

Too late, I took too long...

---

### Post by keratos on 2008-04-10
open a terminal (from the menu) and use command:
```

sudo usermod -aG vboxusers <user>

```
where <user> is your login name

it will ask for a password, enter the admin password you used when installing.

logout (completely) and log back in.

---

### Post by vinceUUUU on 2008-04-10
Hello

thanks so much

tried it and it worked right away

virtualbox looks such a good tool...doesn't  it

:-)

Vince.

---

### Post by IcemanV9 on 2008-04-10
You need to add your userid to the vboxusers group.
```
sudo gpasswd -a `whoami` vboxusers
```
Here's [[COLOR="Orange"]wiki[/COLOR]]("https://help.ubuntu.com/community/VirtualBox") on VirtualBox running on Ubuntu.

---

