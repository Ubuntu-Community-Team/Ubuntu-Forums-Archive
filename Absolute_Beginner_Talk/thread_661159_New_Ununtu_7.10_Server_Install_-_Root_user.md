---
title: "New Ununtu 7.10 Server Install - Root user"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by smithwk2 on 2008-01-07
I just installed server version 7.10.  During installation, I was never asked to set a root user password.  How to I set that password or how to I get the installation to ask me for it.  Thanks in advance for any help on this matter.

---

### Post by reckless2k2 on 2008-01-07
you were asked for a username and password combo and that is your admin sudo user. understand?

you can create a root password by using sudo now if you want one.

---

### Post by qpieus on 2008-01-07
The root user is disabled by default in ubuntu. The sudo command is used instead. Here is an explanation: 
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You can re-enable the root account if you want to, although the ubuntu documentation advises against it. See this page:
[http://www.debianadmin.com/enable-and-disable-ubuntu-root-password.html](http://www.debianadmin.com/enable-and-disable-ubuntu-root-password.html)

---

### Post by smithwk2 on 2008-01-07
Thanks for the information!!!

---

### Post by tonydm on 2008-01-07
Yes, my question was similar.  I understand that there is not active root user.  But when I issue the command sudo apt-get install ubuntu-desktop I get the following error:

"xxxuser is not in the sudoers file.  This incident will be reported."

I just completed the server 7.10 LAMP install.  I defined myself as the user and a MySQL root password.  What gives?  I know I am missing something here.  Thank for your help!

Tony

---

### Post by qpieus on 2008-01-07
tonydm - are you using the account name you made when you installed ubuntu? The first user created during install is normally automatically added to the admin group, which gives the user sudo powers. You can check what groups you are in by typing```
id
```at a terminal prompt. If you find you are in the admin group, then something else must be wrong.

---

### Post by tonydm on 2008-01-07
Thanks for the swift reply.  Yes, I am logged in as theonlyuser sitting at the command line.  id gives me the following:

snippet:

uid=1000(theonlyuser), gid=1000(theonlyuser), groups=4(adm), 20, ..., ..., ..., ..., 1000(theonlyuser)

Tony

---

### Post by qpieus on 2008-01-07
Add yourself to the admin group and your sudo should work again. Since you can't currently sudo, adding yourself to the admin group might be kinda tough though :)
Follow this great info from aysiu to fix the situation:

[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by tonydm on 2008-01-07
Thanks.  I am curious though.  How does this happen on a fresh install.  It's not like there are a slew of screens and dialogs to respond to.  I clearly defined myself and my password/confirmed and the only other place a password was called for was the MySQL root user.  There is no way I screwed this up.  In fact, I installed the server twice thinking I had missed something.  Thanks Again!

Tony 

Edit:  I'm up and running thanks to qpeius's link.  Thanks again!!

@make_root - I selected no function key during install.  Simply selected new install.  Thanks for your response!

---

### Post by make_root on 2008-01-07
Hi Folks

I just registered to let you know, how this happened or how you can do it different next time ;-)
In my case I got to a preinstalled 6.06 and was very confused that there was a Root-Account, but on the other hand added users could not do a sudo…
After several hours I found out,** it was due to the install option "Expert mode"** (F6 on the boot screen as you start installing).

So if you want a Root-Account and no sudo, go for "Expert mode"
If the standard "Ubuntu way" is yours, go for "Normal mode"

Cheers
make

---

### Post by qpieus on 2008-01-08
Yeah, I don't know why this happens. I just read another thread within the last few days that had the same problem as you did. I've not had this problem (with the first user created). If you add a user, though, that second user does not automatically get added to the admin group, so if you want sudo for that person, you have to manually add the user to the group. I had to do this on my daughter's computer. On install, her account was the first created. I also wanted an account for me, so I could log on and do stuff if needed. I found that I didn't have sudo powers...

I'm glad you got your situation fixed.

---

