---
title: "Getting out of Root"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2008-03-18
Having failed to install Ubuntu on a laptop I've tried Debian based Kanotix which installs ok. Unlike Ubuntu In Kanotix I have to sign in as Root to make system changes. I believe its important to not remain signed in as Root. How do I  sign out of Root please?

---

### Post by TJCIB on 2008-03-18
I am pretty new, but this is how I understand it....I hope I'm correct, someone correct me if I'm not...

There is a user that is "root".  While it is possible to log in to that account, it is not activated by default.  The user that you create on install is an administrative user with "sudo" abilities.  When performing system changes, you will be prompted for a "sudo password" which gives you temporary "root" privileges.  It will not prompt for a password every time you execdute a sudo command (that would get annoying), but it will prompt you after a certain number of minutes.  This ensures that you are not remaining as root without knowing it.  I'm not sure if its possible to change the frequency of sudo password prompts, but its frequent enough that I have appreciated it.

That might be over simplified, and there are explanations of the sudo thing on the forums and wikis.

---

### Post by JoshuaRL on 2008-03-18
Well, thats how Ubuntu and most Linux distros handle root priviledges.

However, the OP said that Kanotix automatically signs in as root.  I couldn't find anything about it installing as root, but it is a LiveDistro that runs KDE as a Live environment.  So the Live environment will be a root system by default.  That might be the issue.

To fix this, go into the Kmenu and add a user (not sure how to do this exactly, I've never used Kanotix).  Make sure the user you add is a sudo user so that you can have root priviledges as needed but you still keep your system secure.

As a side note, what issues did you have on the Ubuntu install?

---

### Post by Junglizer on 2008-03-18
You should be able to setup sudo on your current distro anyways, its just the default setup of Ubuntu. On a side note you can, from the terminal as your regular user do the following:

```
user@system~$ su -
```
This will prompt you for the root password, if entered correctly will change you into a root prompt (i.e. you are now logged in as root) and you will probably see something similar to 
```
root@system~#
```

Alternately you can run:
```
user@system~$ su
```
This will also prompt you for the root password and upon successfull entry grants root abilities to your current user.

At any point with either of these, you can simply type ```
root@system~# exit
``` and it will exit your root session and return you to your original session.

---

### Post by a.v.l on 2008-03-19
Thanks for the replies.

---

### Post by bodhi.zazen on 2008-03-19
> **Junglizer said:**
> You should be able to setup sudo on your current distro anyways, its just the default setup of Ubuntu. On a side note you can, from the terminal as your regular user do the following:

```
user@system~$ su -
```
This will prompt you for the root password, if entered correctly will change you into a root prompt (i.e. you are now logged in as root) and you will probably see something similar to 
```
root@system~#
```

Alternately you can run:
```
user@system~$ su
```
This will also prompt you for the root password and upon successfull entry grants root abilities to your current user.

At any point with either of these, you can simply type ```
root@system~# exit
``` and it will exit your root session and return you to your original session.

Just a FYI, Ubuntu uses sudo.

So for a root terminal use ```
sudo -i
```

For graphical apps use gksu (kdesu in kde).

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
	
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by forrestcupp on 2008-03-19
> **a.v.l said:**
> Having failed to install Ubuntu on a laptop I've tried Debian based Kanotix which installs ok. Unlike Ubuntu In Kanotix I have to sign in as Root to make system changes. I believe its important to not remain signed in as Root. How do I  sign out of Root please?

For your situation, the exit command is what you are probably wanting.

---

