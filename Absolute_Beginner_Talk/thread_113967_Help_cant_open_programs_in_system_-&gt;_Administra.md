---
title: "Help cant open programs in system -&gt; Administration"
date: 2006-01-07
forum: Absolute Beginner Talk
---

### Post by KingTiger on 2006-01-07
i cant open any of the programs in the system -> Administration menu
it asks for my password than nothing happens please help

KingTiger

---

### Post by s6dalane on 2006-01-07
Use your user's password for that. Then it must work.

---

### Post by etc on 2006-01-07
What happens when you open a terminal and type
```
gksudo synaptic
```

---

### Post by KingTiger on 2006-01-07
an other thing if i try to do any sudo commands it will ask for my password 
than just go back to the username@ubuntu:-$

KingTiger

---

### Post by KingTiger on 2006-01-07
[QUOTE=etc]What happens when you open a terminal and type
```
gksudo synaptic
```[/QUOTE]

nothing it just gos back to the  user@ubuntu:- $

KingTiger

---

### Post by KingTiger on 2006-01-07
using "gksu synaptic" seems to  work

KingTiger

---

### Post by KingTiger on 2006-01-07
the fallowing programs wont open

add application
disks
login screen setup
networking
services
time and date
update maneger
users and groups

the fallowing programs work

device maneger
printers

synaptic will work by doing "gksu synaptic"

for the program that wont work it some times says starting program for a minute than nothing happens and some it gives this error:
failed to run shares-admin as user root:
child terminated with 1 status

KingTiger

---

### Post by deNoobius on 2006-01-07
Are you running as root?  Have you tried running as a regular user and using "sudo" (or gksudo in Gnome)?

---

### Post by KingTiger on 2006-01-07
ya thats what iv been doing running gnome and using gksudo
and it dosent work 

but i found a fix
if i put a sortcut on the desktop and change it to "gksu" instead of "gksudo" it works. so there seems to be somthing worng with sudo

KingTiger

---

### Post by GreyFox503 on 2006-01-07
The first user account created during an Ubuntu installation is given use of the 'sudo' command, but others created after that probably do not have that ability by default.  Is the user account you're using the one created during installation?

---

### Post by KingTiger on 2006-01-07
no the user account i created during an Ubuntu installation takes 20 minutes to load and takes forever to do any thing so i dont use it

KingTiger

---

### Post by GreyFox503 on 2006-01-07
Ok, I think you need to add your current user account to the admin group, which will let you use sudo.  I'm not at my Ubuntu box right now so I can't test this, but I think this will do it.

You can't give yourself sudo privileges if you don't already have them, so you need to log in as root.  Reboot the computer, and in GRUB, choose the option for recovery console.  It should drop you into a black-and-white root terminal.

Then try this command:

```
gpasswd -a *your_username* admin
``` 

Of course, replace *your_username* with the name of the user you wish to give sudo privileges to.

Type 'exit' when you're done, and then see if you can use sudo properly, under your regular account.

---

### Post by KingTiger on 2006-01-07
ok i'll give that a try thanks

KingTiger

---

### Post by KingTiger on 2006-01-08
nope dident work

KingTiger

---

### Post by KingTiger on 2006-01-08
i also tryed to add me to the sudo group in users and groups
gut it dident work
KingTiger

---

### Post by KingTiger on 2006-01-08
i found
[this page]("https://wiki.ubuntu.com/RootSudo?highlight=%28sudo%29#head-3f8a7e5ae5fe6b048ffecef0bf38c811eede7aec") on Allowing other users to run sudo but there is no Executing system administration tasks option

KingTiger

---

### Post by KingTiger on 2006-01-08
and an other thing theres no admin group (theres a adm group) but adding me to that dosent work

KingTiger

Edit: if i make a new user i can check Executing system administration
edit: turning on Executing system administration is what makes it take 20 minutes to load (in fact i cant get it to load)

---

### Post by GreyFox503 on 2006-01-09
Can you print out what your /etc/sudoers file looks like?  Run this command as root:

```
cat /etc/sudoers
``` 
Mine looks like this:

> # /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL


---

### Post by KingTiger on 2006-01-09
i fixed the problem by adding my username to the sudoers list

KingTiger

---

### Post by djlilyazi on 2006-01-09
[QUOTE=KingTiger]i cant open any of the programs in the system -> Administration menu
it asks for my password than nothing happens please help

KingTiger[/QUOTE]

i have the exact same problem right now....
i tried everything u tried nothing is workink i dont have permission to do shit

---

### Post by djlilyazi on 2006-01-09
[QUOTE=GreyFox503]Can you print out what your /etc/sudoers file looks like?  Run this command as root:

```
cat /etc/sudoers
``` 
Mine looks like this:[/QUOTE]

wheni type this line 
/etc/sudoers

i get permission denied

---

### Post by Perfect Storm on 2006-01-09
Did you run it as root?

```

sudo cat /etc/sudoers

```

---

### Post by djlilyazi on 2006-01-09
[QUOTE=Artificial Intelligence]Did you run it as root?

```

sudo cat /etc/sudoers

```[/QUOTE]

how do i do that..sorry i am newbie ...

---

### Post by Perfect Storm on 2006-01-09
Open the terminal. 

Application tab ---> Accessories ---> Terminal

and write in ther terminal

```

sudo cat /etc/sudoers
```

sudo gives you adminstration priveleges

---

### Post by djlilyazi on 2006-01-09
[QUOTE=Artificial Intelligence]Open the terminal. Application tab ---> Accessories ---> Terminal and write in ther terminal ```
 sudo cat /etc/sudoers
``` sudo gives you adminstration priveleges[/QUOTE] ohh.. yeah that is what i was doing the whole time sorry..

if i do this
[http://www.ubuntuguide.org/#gainrootmodifykernel](http://www.ubuntuguide.org/#gainrootmodifykernel)

will it fix everything for me ?

---

### Post by djlilyazi on 2006-01-09
ohh  man i am so scred now ...how do i know what type of user i am right ?

---

### Post by GreyFox503 on 2006-01-09
If you are unable to use sudo properly, then the easiest way to gain root access is to reboot your computer.  At the GRUB menu (you might have to press ESC to see it), choose the Ubuntu that says "recovery mode" or something to that effect.  It should drop you into a root terminal.

For future reference, if your terminal prompt ends with '$', then you are a regular user.  If it ends with '#', then you are the root user.  You can also type 'whoami'.

I have never needed to edit the /etc/sudoers file, but it looks like KingTiger fixed it by adding his username to the sudoers list.  To edit the sudoers file, use this command *as root*:

```
visudo
``` 
then add a line like this:

```
*username* ALL=(ALL) ALL
``` 
Where *username* is the user account you want to give sudo privileges to.

Hit Ctrl + X to exit the editor, then 'Y' to save changes, then enter.  That username should now have sudo privileges.

---

