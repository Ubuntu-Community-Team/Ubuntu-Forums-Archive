---
title: "logging in as root"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by mongooseman1128 on 2006-11-11
I'm having trouble logging in as root to both my desktop and in the text environment. what user name should I be using? I've just been trying root and its password, but it doesn't work.

---

### Post by moephan on 2006-11-11
Ubuntu has no root user by default. The system is designed to use "sudo" instead. The first user created is added to the sudoers list.

I don't know how much experience you have with sudo. In case you don't know, to get started simply type "sudo" in front of you command, such as:
$sudo apt-get install someprogram
Simply enter the password that you sign in with.

Cheers, Rick

---

### Post by punx45 on 2006-11-11
when you need to run a command that needs root access, preface it with the command "sudo"   for example, to reboot in command line you need root access, so you would type:
```
sudo shutdown -r now
```

and then it will ask for your password before it executes the command.

---

### Post by d3v1ant_0n3 on 2006-11-11
[ THIS](https://help.ubuntu.com/community/RootSudo) page does a good job of explaining Ubuntu's stance on Root/Sudo.

---

### Post by ebozzz on 2006-11-11
I did the same thing on my first install. I selected root as a user name but when I tried to log in I got an error message stating "Administrator Cannot Log In From This Screen." Is that what you get? 

I am still very new to Linux/Ubuntu and I could not find a work around. What I did was re-install and during that process I selected a user name other than root (first name for instance). I was able to log in just fine after that. It seems to me at least that the initial user that is created is designated as the Administrator/root. If I am wrong, would someone please correct me. I hope this helps.


EDIT: It appears that there are some more qualified answers posted by other members. Please listen to them! :)

---

### Post by aysiu on 2006-11-11
If you prefer to do things the point-and-click way, I suggest you read this guide:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by ebozzz on 2006-11-11
> **moephan said:**
> Ubuntu has no root user by default.

I'm not disputing what you are saying but I just wanted to add this tidbit. When I was trying to work my way through my issue I somehow managed to get into an interface that was command/text driven. I was able to log in there using root as my user name along with the password that I had created.

---

### Post by taurus on 2006-11-11
> **ebozzz said:**
> I'm not disputing what you are saying but I just wanted to add this tidbit. When I was trying to work my way through my issue I somehow managed to get into an interface that was command/text driven. I was able to log in there using root as my user name along with the password that I had created.
Yes, you can create a password for root with "sudo passwd root" and log in as root but you better be careful because one wrong command and you can kiss your system goodbye!!!

---

### Post by ebozzz on 2006-11-11
> **taurus said:**
> Yes, you can create a password for root with "sudo passwd root" and log in as root but you better be careful because one wrong command and you can kiss your system goodbye!!!

Understood. I didn't stay there very long and I'm still not sure if  I can recreate getting there. I wasn't trying to create a root password and it happened during the boot process. I was simply trying to get to my desktop but since I had created the my user name as root, I couldn't log in.

---

### Post by ebozzz on 2006-11-12
> **taurus said:**
> Yes, you can create a password for root with "sudo passwd root"

Doesn't root automatically get the same password as the initial user that is created during the installation? I'm looking at the user profile and there is a password populated for user/root.

---

### Post by taurus on 2006-11-12
> **ebozzz said:**
> Doesn't root automatically get the same password as the initial user that is created during the installation? I'm looking at the user profile and there is a password populated for user/root.
No, root doesn't have the same password as your regular user.  I think you confuse between root and sudo!!!

---

### Post by ebozzz on 2006-11-12
> **taurus said:**
> No, root doesn't have the same password as your regular user.  I think you confuse between root and sudo!!!

So when I look at the user profile information from the administrative menu, the user **root** displayed there is actually sudo?

---

### Post by ebozzz on 2006-11-12
I'm sorry if it appears that I'm not *getting it* but I just want to make sure that I have a clear understanding of what you are saying. Maybe it would help if I explained what I am seeing a little more. Here goes.

After installing Edgy, I rebooted, logged in and went in to set up additional users. In the that interface I found the user ID that I had created during install and root. What I am saying is that when I view the profile information for the user listed as root in that interface there is a password already populated. I did not add one. It was already there after the installation was completed. That's what prompted my question.

---

### Post by aysiu on 2006-11-12
> **ebozzz said:**
> So when I look at the user profile information from the administrative menu, the user **root** displayed there is actually sudo?
*root* is a user.
*sudo* is not a user.

*sudo* is part of a command that will allow a user to temporarily assume root-like privileges.

Here's the difference. If you had the root account enabled (it's not enabled by default in Ubuntu, however), and wanted to install krename, this is what you would do: ```
su
password:
aptitude update
aptitude install krename
exit
``` The password you'd be asked for is the *root* password, since *su* switches you to be the root user.

That is not the default behavior in Ubuntu, though.

This is how it works in Ubuntu: ```
sudo aptitude update
password:
sudo aptitude install krename
``` The password you're asked for is your *user* password, which allows you (since you're in the *admin* group, and not just a regular user) to temporarily assume root-like privileges and install software.

All of the administrative interfaces (like Users and Groups, Login Window, Synaptic Package Manager), use a graphical version of *sudo* called *gksudo*, and will ask for your *user* password.

Unless you do something weird to your Ubuntu installation, you don't need a root password or a root account, and you will never be asked for a root password to do administrative tasks.

**Forget about root**

For administrative tasks, just enter your only user password. When you want to do root-like tasks from the command-line, preface the command with the word *sudo* and then enter your only user password.

---

### Post by ebozzz on 2006-11-12
> **aysiu said:**
> *root* is a user.
*sudo* is not a user.

That's the understanding that I had initially. I guess that I got a little confused by the way taurus was explaining it or I misinterpreted what he posted. No disrespect intended taurus and I do  appreciate your assistance! :) 

> *sudo* is part of a command that will allow a user to temporarily assume root-like privileges.

I totally understood that until I got off track.

> Here's the difference. If you had the root account enabled (it's not enabled by default in Ubuntu, however), and wanted to install krename, this is what you would do: ```
su
password:
aptitude update
aptitude install krename
exit
``` The password you'd be asked for is the *root* password, since *su* switches you to be the root user.

Clear on that.

> That is not the default behavior in Ubuntu, though.

This is how it works in Ubuntu: ```
sudo aptitude update
password:
sudo aptitude install krename
``` The password you're asked for is your *user* password, which allows you (since you're in the *admin* group, and not just a regular user) to temporarily assume root-like privileges and install software.

Got that part also.

> All of the administrative interfaces (like Users and Groups, Login Window, Synaptic Package Manager), use a graphical version of *sudo* called *gksudo*, and will ask for your *user* password.

I'm still with you here.

> Unless you do something weird to your Ubuntu installation, you don't need a root password or a root account, and you will never be asked for a root password to do administrative tasks.

One more question. When an install is done does root get a password automatically assigned? The reason that I ask this is that when I look at the profile in the Users and Groups interface, it appears that one is populated there. As I mentioned in my previous post, I never added one for root. 

> **Forget about root**

For administrative tasks, just enter your only user password. When you want to do root-like tasks from the command-line, preface the command with the word *sudo* and then enter your only user password.

The use of root never was a big issue to me as you and others have clearly stated that root-like tasks can be completed with sudo. It's also safer with sudo. I just go back to the fact about me being able to successfully log in as user *root* from the command-line along with my personal user ID password. Don't ask me how but I was able to access the command-line from the login screen when I was unable to get to my desktop because the only user ID that I had created during install was *root*. That's why I asked if the password belonging to the original user created during install goes to *root* by default. I may still be missing something but I am coming along! :D Thanks for the help aysiu.

---

### Post by aysiu on 2006-11-12
What I've read is that a root password is randomly assigned, making it essentially not assigned, since you can't know what that random password is. You can always *reset* the root password to one you know, but in the beginning it doesn't exist for all practical purposes.

---

### Post by ebozzz on 2006-11-12
Got it and I am gone! Thanks **very** much for your help.

---

### Post by mongooseman1128 on 2006-11-14
okay that makes sense, I was trying to just us su in order to sh and was running "su sh" didn't realize the command was always sudo. Also, I just found out (for anyone who's interested and sorry to anyone who already said this) if I go into Users and groups and add myself to the group root (in the properties) I suddennly become root.

---

### Post by Brando569 on 2006-11-30
how can i get root to login via KDM, i know ive done it before, the user is enabled and the password is reset. i just like to use it when my account is really FUBAR and recovery mode or creating a new user doesnt help much

---

### Post by aysiu on 2006-11-30
> **Brando569 said:**
> how can i get root to login via KDM, i know ive done it before, the user is enabled and the password is reset. i just like to use it when my account is really FUBAR and recovery mode or creating a new user doesnt help much
I believe it's ```
sudo nano -B /etc/kde3/kdm/kdmrc
``` which will allow you to edit the KDM settings. Find the part about logging in as administrator and make sure it's true (as opposed to false).

If you prefer the GUI, press Alt-F2 and type ```
kdesu kcontrol
``` Then go to the very bottom part and change the login configuration there.

---

### Post by Zaen on 2006-11-30
All you need to do is press ctr-alt-f1 and it will take you to a command line
(ctr-alt-f7 brings you back to the gui) and if you already have a root account setup, you can login, do what you need to, and get out. 

Also, I know gnome doesn't allow you to login as root ( at least it didn't used to, haven't tried it in a long time)

---

### Post by aysiu on 2006-11-30
> **Zaen said:**
> 
Also, I know gnome doesn't allow you to login as root ( at least it didn't used to, haven't tried it in a long time) That's a setting that can be changed. It has nothing to do with Gnome or KDE and everything to do with *buntu.

---

