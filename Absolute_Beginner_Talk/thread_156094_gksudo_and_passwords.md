---
title: "gksudo and passwords"
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by Keith_Beef on 2006-04-06
Hi, everybody.

I'm new to Ubuntu, but not to Linux.

I started with RedHat back in 1996 or 97 and used that for a couple of years; Then I went on to use Mandrake until early this year when I switched to Mandriva.

a couple of days ago, I tried out a live Ubuntu on an old PC I found in the garage, and decided to download 5.10 and install it on a new hard drive.

So, there it is, an old HP Vectra with a 160 GB drive, and a new NetGear W311 wireless card.

Now, I know I'll have trouble with the W311, so for the moment, I'm trying to get wired ethernet going.

I can ping Ubuntu from my main (Mandriva) machine, and ping the Mandriva from Ubuntu... OK so far. But I'd like to get ssh running on the Ubuntu so I can have a terminal on Ubuntu here on my Mandriva screen...

But, I can't get the services-admin program to work.

If I choose it from a menu, I am prompted for a password. I thought this would be the root password, but this doesn't work.

If I run services-admin from the command line, as a normal user, I am promted for a password; I give that of root, and the program starts, but the dialog isnever properly drawn, as if it is looking for running or available services and gets stuck in an endless loop.

If I do "gksudo services-admin", I am prompted as when I choose from the menu; password is rejected.

Trying network-admin from the menu, command line, and gksudo gives the same results: rejection or eternal wait.

Any help would be greatly appreciated.


Beef.

I just tried to install ssh-server from the CD.

gnome-app-install from the menu prompts for a password, but doesn't like root's passwd.
From a command line, as a normal user, I'm notified that I need to be root to run this program.
So:
su -
[root passwd]
#gnome-app-install
gtk complaint "RuntimeError: could not open display".


Why?

---

### Post by joe_gosse on 2006-04-06
I don't know all the answers.

When you're prompted for the password in any admin window situation you should input the password of whatever user you're logged in as. This should help you change the settings from a menu.

---

### Post by Keith_Beef on 2006-04-06
[QUOTE=joe_gosse]When you're prompted for the password in any admin window situation you should input the password of whatever user you're logged in as. This should help you change the settings from a menu.[/QUOTE]

Thanks. That helps me get past the gksudo rejection. Now I understand that it wants my password, not root's.

But the services- and network-admin programs still don't work. :(

A bit later today, I'll pull out the wireless card and try again.


Beef.

---

