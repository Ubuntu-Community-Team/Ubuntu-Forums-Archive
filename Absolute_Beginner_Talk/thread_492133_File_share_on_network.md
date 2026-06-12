---
title: "File share on network"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by betterspud on 2007-07-04
Hi,

Have enabled sharing of a file on my Ubuntu machine and have pointed a shortcut to it on another machine on my network, running Windows XP.

The XP machine then asks for user password to access the file in the format DOMAIN\user.

I've entered my Ubuntu machine user name and password here, just as I would to log on, but it will not accept it.

Anyone have any ideas what I'm doing wrong? Maybe Linux won't allow me to log on because I'm already logged on directly? Do I need to set up a separate user for external access?

Cheers

BetterSpuD

---

### Post by AndyCooll on 2007-07-04
Not used Winderz for awhile (so it might be worth checking my advice before taking it as gospel),  however here goes ...

1. It's a good idea to make sure  logon and password for  Ubuntu and XP are the same.
2. I trust you're using Samba for these shares. There's lots of threads on these boards explaining how to setup Samba shares properly.
3. It seems to me you probably haven't set your Samba password. In a terminal type the following:
```
sudo smbpasswd -a
```
You'll then be asked for a username and password. You should set that to your login and password. You should then be ready to go.

:cool:

---

### Post by metallicamaster3 on 2007-07-04
or if you want to eliminate the password altoghether, 
open up your samba configuration file, and find

security = user

change it to 

security = SHARE



that will make it so that you wont need a username and password

happy ubuntu!

---

