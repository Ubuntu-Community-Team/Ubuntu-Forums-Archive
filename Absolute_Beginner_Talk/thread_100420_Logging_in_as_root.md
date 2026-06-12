---
title: "Logging in as root"
date: 2005-12-07
forum: Absolute Beginner Talk
---

### Post by Justus on 2005-12-07
I need to use my root account, so I activated it, and now I'm wondering how to log in to it...when I try logging in as root on the main login screen, it says something like "root is not allowed to log in from this screen". What do I do?

---

### Post by aysiu on 2005-12-07
Will you at least listen to alternatives to logging in as root, depending on what you're trying to accomplish? There may be simpler ways to accomplish the tasks you want.

If you hear these methods and still want to log in as root, that's cool.

First of all, if you have one command you want to type in a terminal, just preface that command with the word *sudo*. For example, instead of: ```
su
password:
apt-get update
apt-get install juk
exit
exit
``` you would ```
sudo apt-get update
password:
sudo apt-get install juk
exit
``` If you prefer to do root changes graphically, just create a launcher on the panel with the command ```
gksudo nautilus
``` It's a lot easier than logging out, logging in as root, making changes, logging back out of root, and logging back in again as user.

For more on why Ubuntu uses sudo instead of root, read this: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by kingsidy on 2005-12-07
Go to SYstem-->Administration-->Login Screen setup, then click on the security tab and check allow root login.

Make sure that you set up your root password. If not open the terminal and type: passwd root (as sudo). Then enter whatever password you want. Logout.
In the login screen, in the box that says username, type root, and then enter your root password. That is it. I hope it helps.

---

### Post by funkydan2 on 2005-12-07
Why do you want to log into GNOME as root?  This behaviour is normally frowned upon and considered unsafe.  There is probably a safer way to achieve what you want to do.

---

### Post by Qrk on 2005-12-07
Yes, logging in as root means every application you run is run as root. Thats a bad thing. Much, much better to use gksudo nautilus; and you get practically the same effect, just safer.

---

### Post by mistergq on 2005-12-07
[QUOTE=aysiu]If you prefer to do root changes graphically, just create a launcher on the panel with the command ```
gksudo nautilus
``` It's a lot easier than logging out, logging in as root, making changes, logging back out of root, and logging back in again as user.[/QUOTE]  Thanks for posting this.  I never thought about adding it as a launcher item on the panel. :p

---

### Post by Justus on 2005-12-07
I was able to do what I was trying to do with aysiu's solution (the launcher). Well, I wasn't actually able to do it, but that's just cause it can't be done ;) I was trying to read/write an ntfs partition. But anyway, that's beside the point.
But thanks the the info kingsidy, it's nice to know how to do at least.
Qrk: why is this so unsafe? Would it make it easier for a hacker to gain complete control? Or would it just be dangerous if someone had physical access to my comptuer? Thanks everyone

---

### Post by aysiu on 2005-12-07
[QUOTE=Justus]why is this so unsafe? Would it make it easier for a hacker to gain complete control? Or would it just be dangerous if someone had physical access to my comptuer? Thanks everyone[/QUOTE] You can read the pros and cons of the sudo security model here: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Qrk on 2005-12-07
(This is from what I have heard, not my own experience.)
Its unsafe because when you are logged in as root you run everything as root. Not only is this a security risk, if you say, run firefox. (Its probably all not that bad, because after all, this is Linux) Its also a risk because if any application malfunctions its able to affect your whole system... not just that part it has access too. So if you are logged in as root and something malfunctions; it could screw everything up, not just your home directory.

---

### Post by ardchoille on 2005-12-07
Ubuntu 5.10 is the first distro that I have not ever logged into the root accout on. I thought I wouldn't be able to get by without logging in as root at least once, but I was wrong. I love this distro and there really is no need to actually log into the root account, IMHO. sudo, gksu and gksuexec take care of anything you will ever need.

---

### Post by 23meg on 2005-12-07
Here's yet another practical method to open files as root:

[http://www.ubuntuforums.org/showthread.php?t=24008](http://www.ubuntuforums.org/showthread.php?t=24008)

---

