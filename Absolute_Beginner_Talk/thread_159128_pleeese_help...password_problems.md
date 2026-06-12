---
title: "pleeese help...password problems"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by Obor on 2006-04-12
I hope there is someone here that can help me.

I don't think I changed anything but while playing around with my sound I might have done something and now I can't run anything that needs my user password.

let me explain:
**e.g.1. **
I try to open synaptic and get this message (it never asks for password):
[I]Failed to run /usr/sbin/synaptic as user root:
 No password was supplied and sudo needs it.[/I]

**e.g.2.**
i try to run "sudo gedit /etc/esound/esd.conf" in terminal, it will ask me for password, i put it in, and then gives the following error:
*Sorry, user obor is not allowed to execute '/usr/bin/gedit /etc/esound/esd.conf' as root on localhost.localdomain*.

what have i done? how can i fix it? any ideas? ](*,)
Thanx

---

### Post by Mustard on 2006-04-12
I think you might need to explain in more detail what you were doing to your sound configuration just prior to this occuring.  If you were using the command line to make changes, a history of the commands entered can be found in your .bash_history file.

To access that use this command..

```
cat ~/.bash_history
```

---

### Post by localzuk on 2006-04-12
You appear to have removed sudo privileges from your account. To check this, type 'groups' on a terminal. If the group 'admin' is not in the list you will have to restart the computer into failsafe mode (select from grub boot menu). From here you are the root user. Simply type 'useradd -G admin username' where username is the username of the user that things went wrong for.

---

### Post by gborzi on 2006-04-12
Maybe you changed the sudoers file in /etc or you removed yourself from the admin group. Check if sudoers still contains the line
%admin  ALL=(ALL) ALL
if it is still there check that you are listed as a member of the admin group, e.g. in my system the /etc/group file contains the following line (without the backslash)
admin:\x:106:gborzi
I'm not sure if you need to be listed in /etc/gshadow too like this (without the backslash)
admin:\!::gborzi
In order to modify /etc/sudoers or /etc/group or /etc/gshadow, press the escape key at the grub menu and select recovery mode. It should automatically login you as root (if I remember correctly, I can't check right now!).
If the recovery mode doesn't work, use some live distribution, mount your root partition and check/modify the files. Good Luck !

---

### Post by Obor on 2006-04-12
Mustard - 
if think where i went wrong is the following:
gksudo usermod -Gaudio username

[QUOTE=localzuk]You appear to have removed sudo privileges from your account. To check this, type 'groups' on a terminal. If the group 'admin' is not in the list you will have to restart the computer into failsafe mode (select from grub boot menu). From here you are the root user. Simply type 'useradd -G admin username' where username is the username of the user that things went wrong for.[/QUOTE]

Group admin is not on the list but when i boot up to failsafe mode and type "useradd -G admin obor" (where obor is my username) it says "useradd:user obor exists" 
Should it be the other way around? i.e. useradd -G obor admin?

---

### Post by gborzi on 2006-04-12
Try adduser obor admin, if the admin group still exists.

---

### Post by Obor on 2006-04-12
Thanks for all your help.

At the end I used "visudo" when booted in failsafe mode and added "username ALL=(ALL) ALL"  to it

It all works now ;)

---

