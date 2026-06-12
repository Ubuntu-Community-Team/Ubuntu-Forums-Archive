---
title: "Remote login to ubuntu"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by MarioFerreira on 2006-04-18
Hi,

I need to login remotly, from Windows, to a Linux machine running the ubuntu distribution. From browsing around i have realised that i should use puTTY client at the Windows machine and SSH on the Linux box. Can anyone help me position my bearings regarding how to achieve this?

Thanks

---

### Post by pbaehr on 2006-04-18
It's pretty simple. I use that type of setup all the time.

For the simplest approach first install ssh on the ubuntu machine:
```
sudo apt-get install ssh
```

Install puTTY on your Windows computer.

Start up puTTY and connect to the IP address of your ubuntu machine. Just log in with your normal user name.

If you want to be able to run graphical applications you'll need to install an x-windows server on your Windows computer. I use cygwin-x. You'll also have to allow this somewhere in the X config. I forget where exactly, but it's not hard and I'm sure you can find it somewhere online if you decide to go this route.

If you need to transfer files via SSH, try WinSCP3.

---

### Post by WoodyMahan on 2006-04-18
I am using a program called FreeNX.  It works great and lets me choose whether to log in using my gnome or KDE desktops.  I like it a lot and mulitple users can log in and open sessions on the Linux machine at once.  You can search the posts here for freenx and one of them has the link to add to SYnaptic so you can download and install.  FreeNX (client side) for windows was very easy to find through Google.  No need to install anything but the program.

---

### Post by piller on 2006-04-18
In order to login remotely to your linux machine you will need to install the "openssh-server" package.  You can do this easily using synaptic on your ubuntu machine.

---

