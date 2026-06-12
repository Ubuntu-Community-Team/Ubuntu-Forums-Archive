---
title: "No Xserver - No root passwd - Need HELP!"
date: 2006-02-14
forum: Absolute Beginner Talk
---

### Post by USA1 on 2006-02-14
Hello,

So far I have been using FC4 on my new labtop but it overheats.

My teacher adviced to switch distribution and highly recommended Ubuntu.

I managed to install Ubunto 5.10 on this Compaq v2570NR labtop.
This is a member of the V2000 family.

First, I choose the default installation, but I can't recall of it asking me to type a root passworld. At this point I can't login as root due to lack of password.

Second, due to my ATI Radeon 200M card on this computer, the X Server was not able to load and now all I get is one of the terminal prompts.

How do I fix this situation so that I can get back into the x graphical interface and how do I gain root access?

Thanks,
USA1

---

### Post by kaamos on 2006-02-14
[QUOTE=USA1]Hello,

So far I have been using FC4 on my new labtop but it overheats.

My teacher adviced to switch distribution and highly recommended Ubuntu.

I managed to install Ubunto 5.10 on this Compaq v2570NR labtop.
This is a member of the V2000 family.

First, I choose the default installation, but I can't recall of it asking me to type a root passworld. At this point I can't login as root due to lack of password.

Second, due to my ATI Radeon 200M card on this computer, the X Server was not able to load and now all I get is one of the terminal prompts.

How do I fix this situation so that I can get back into the x graphical interface and how do I gain root access?

Thanks,
USA1[/QUOTE]

The installer will not ask you for a root passwd because ubuntu uses sudo as much as possible instead of separate a root account. [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) (in short, if you want to use "su", just type "sudo su"). You should be able to login with the username and password created during install.

For X, you can use the command
```
dpkg-reconfigure xserver-xorg
```to configure your settings.

Hope this helps.

---

### Post by USA1 on 2006-02-14
I figured how to login as root, but I still cant fix the X server so that I can have a graphical interface.

---

### Post by kaamos on 2006-02-14
Try the command above (with sudo in front if you are not root) and choose the "vesa" driver.

---

### Post by USA1 on 2006-02-15
Hello all,

In my case, I got lucky!

The default installation of Ubuntu does install the correct driver for the ATI radeon 94318.  It just doesn't use the right options so it needs to be configure correctly, basically just one change will get you fixed.

Edit the xorg.conf file located at /etc/X11/xorg.conf
I advice to make a copy of that file before you start editing it.
Open the file with an editor, locate the section for the ATI and the following:
Option="noacel" (not sure of the correct syntax do a search on the forum).
That should be all you need to get xServer not to crash and boot into a full resolution screen.  Nothing to install or uninstall....

With regard the WIFI card, just follow one of the tutorials here on the book.
Basically all you have to do is:
Run commands to uninstall the diswrapper if it is install and the WIFI driver.
Then install a fresh copy of diswrapper.
Then run diswrapper to install the bcwL5.inf and bcwL5.sys files by just running the diswrapper bcwl5.inf.
Again do a search for one of the tutorials here to get the correct syntac.

Once you have the card installed, reboot your computer and finish the configuration from the gnome desktop in a much friendly maner.

That was all that it took to get the computer functional.

My advice, stop wasting time reading through so many tutorial, just pick a tutorial and try to follow it the best you can, at times is best to read less and do more....

If you need help, ask questions and be patient :)

Welcome to Ubuntu from a newbee himself.... The Merengue King!

---

