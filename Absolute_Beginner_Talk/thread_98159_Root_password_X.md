---
title: "Root password :X"
date: 2005-12-02
forum: Absolute Beginner Talk
---

### Post by khoma on 2005-12-02
Just installed Ubuntu 5.10. Apparently, the system has chosen to set a root password, because I cannot login as root. Which basically leaves me with a useless system. I don't remember ever being asked for a root password during the install, but I guess I must've been at some point. Or am I missing something here?

---

### Post by earobinson on 2005-12-02
I searched the forums for (root password) and found this [http://www.ubuntuforums.org/showthread.php?t=97052&highlight=root+password](http://www.ubuntuforums.org/showthread.php?t=97052&highlight=root+password) (and many others)

---

### Post by linbetwin on 2005-12-02
The root account is disabled by default in Ubuntu.

Use your user passwd that you were asked to create during install. Ubuntu will ask you for your user passwd whenever you need root privileges.

To become root in a terminal session (for 15 min) type sudo instead of su before the command.

You can also type sudo -s -H but remember to exit after you've finished.

To open an app as root ALT+F2 gksudo app_name

---

### Post by khoma on 2005-12-02
[QUOTE=earobinson]I searched the forums for (root password) and found this [http://www.ubuntuforums.org/showthread.php?t=97052&highlight=root+password](http://www.ubuntuforums.org/showthread.php?t=97052&highlight=root+password) (and many others)[/QUOTE]

Actually, that's very helpful thank you. However, still doesn't answer my question really. I need the actual root password. I want to be able to log in as root, and use su.

---

### Post by linbetwin on 2005-12-02
[quote=khoma]Actually, that's very helpful thank you. However, still doesn't answer my question really. I need the actual root password. I want to be able to log in as root, and use su.[/quote]

Then you must create a root account.

---

### Post by earobinson on 2005-12-02
that link and the many others will show you how to make a root account

[QUOTE=linbetwin]Also, read this:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)[/QUOTE]
[http://www.ubuntuforums.org/showthread.php?t=97052&highlight=root+password](http://www.ubuntuforums.org/showthread.php?t=97052&highlight=root+password) (same link)

That artical tells you this
> Note: This is not recommended! It will break all the GUI admin tools

To enable the root account (i.e. set a password) use:

sudo passwd root

Enter your existing password
Enter password for root
Confirm password for root 

---

### Post by aysiu on 2005-12-02
I'm finding my Ubuntu system quite useful without root. To read more on why this is:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by etc on 2005-12-02
Why you'd want to log in as root and use su is beyond me when a big part of the Ubuntu security model revolves around having no root password and using sudo
But to answer your question
```
sudo passwd root
```
note that it's insecure and you really should use sudo

---

### Post by khoma on 2005-12-02
Thanks guys, setting the root password using sudo worked out enough for me to use su =)

To answer the question of why... tbh I do use sudo quite often, but anything that requires a wee bit of work and it gets annoying. Thus I always have an su terminal open.

Oh well... now I need to download gcc (no way to get networking without it), burn it to a cd, copy it to my ubuntu system, and pray that it will install, so that I can build the necessary network drivers and get my wlan card to work... getting this distro up n running is proving to be quite the challenge ;)

---

### Post by JohnnyV on 2005-12-02
I'm new to Ubuntu and had the same problem. I fixed it by using sudo to change the root password to one that I chose. This defeats the implied security of sudo only operation but I found it a pain in the neck not being able to log in as root. I'm going from memory but this should do it.

sudo passwd root

Give your password when asked by sudo. Then follow the dialog for changing the root password. From then on you can log in as root or su with the new password.

---

### Post by khoma on 2005-12-02
Hmm, ok. Continuing to use this thread... did a search for ndiswrapper, people seem to be under the impression that it doesn't work at all on AMD64 systems. I refuse to believe this, as it works just fine under other distros I've tried, but I'm assuming I'll have to compile it myself. So the question then becomes, where can I find some nice ubuntu gcc package to download off the web? Using another computer obviously...

---

### Post by khoma on 2005-12-02
"The system administrator is not allowed to log in from this screen"

Asking very calmly without doing any physical harm to any nearby electronic equipment: how do I fix this?

---

### Post by earobinson on 2005-12-02
Im not sure what you are asking here? If you are trying to look in as root that is very unwise and im not sure how to fix it, why not just open a terminal and type su?

EDIT: if you read the whole artical i think you are looking for this i
> It is highly not recommended to allow root to login graphically.
In Ubuntu

    *Open System --> Administration --> Login Screen Setup (Actions --> Administration --> Login Screen Setup in Ubuntu 4.10 (Warty Warthog))
    *Click on the security tab
    *Check Allow root login

In Kubuntu

    *Open Konqueror and open the /etc/kde3/kdm/ folder
    *Right click the kdmrc file and then Actions --> 'Edit as root'
    *On line 246 should be AllowRootLogin=false change it to 'true'
    *Save and exit.


And im not saying its a good set up but using su it seems unlikley that the "admin" would leave without exiting the su terminal.

---

### Post by khoma on 2005-12-02
Okey, screw calm!

Now it refuses to run the synaptics package manager, since I am apparently not providing the correct root password. Which I am. It works just fine when I'm su'ing.

---

### Post by khoma on 2005-12-02
No, there is nothing unwise about logging in as root. It is my right and priviledge, and denying me that right strikes at the very core of my belief that a linux environment provides me with the opportunity to BE IN CHARGE of my computer, unlike the windows way of babysitting.

So! Hope that explains my point of view ;)
Yes, I want root access.

---

### Post by earobinson on 2005-12-02
you dont use your root password you must use your sudo password (same as user log in password) you should really read that link

you can do this
```
su
<password> 
synaptic
```
if you want to run synaptic with the root settings

[QUOTE=khoma]No, there is nothing unwise about logging in as root. It is my right and priviledge, and denying me that right strikes at the very core of my belief that a linux environment provides me with the opportunity to BE IN CHARGE of my computer, unlike the windows way of babysitting.

So! Hope that explains my point of view ;)
Yes, I want root access.[/QUOTE]
Also everything can be done in ubuntu without ever loging in as root just using sudo or su. There is no reason you should ever have to or want to log in as root, but you can if you follow the steps in the provided link.

(aysiu I am not defending loging in as root just the su command lol)

EDIT: wow my spelling and typos are extra bad today

---

### Post by aysiu on 2005-12-02
Read [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) **in its entirety**. It'll explain **everything** including the sudo security model and how to log in as root if you feel you must.

---

### Post by earobinson on 2005-12-02
I assume it works now khoma?

I hope we can all agree that
```
suod su
``` is the worst way to do things lol!

---

### Post by khoma on 2005-12-02
Aye, it works fine now, thank you. I understand the reasons for disabling the root account. I may not necessarily agree, but I do understand them. I still wanted the ability to log on as root, and oh well, that's fixed now.

---

### Post by earobinson on 2005-12-02
Well at least come back me up [http://www.ubuntuforums.org/showthread.php?t=98176](http://www.ubuntuforums.org/showthread.php?t=98176) and sorry for gunking up your tread with a war.

---

