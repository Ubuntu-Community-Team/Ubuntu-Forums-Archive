---
title: "sudo shutdown -h now freeze"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by GreTTin on 2008-04-05
hi, I have an absolute linux setup on my laptop but i'm used to using ubuntu so i installed sudo.

now i'm trying to make a button for a user to click on the desk top to shutdown.i wrote a little script just saying ```
#!/bin/bash
sudo shutdown -h now
```

and linked to it from the icon. i added the user clair to the sudoers file. anyway i don't think that is the problem as i can use the executable file from my root account.

when ever i do sudo shutdown -h now in a terminal from clair's account the computer just hangs untill i press ctrl-z (no idea what this does by the way) but then the computer is so very slow until i reboot it manually. works fine from root so it makes me think it's something to do with pemissions.

I know this isn't ubuntu but i hope you guys could help, even if it's just pointing me in the right direction. i think i may be using the wrong terminology when i do searches. 

thanks in advance

Paul

---

### Post by ghost_ryder35 on 2008-04-05
edit i just re-read your post and saw it was aa sudoers account
one thing to look at is the terminal output when it runs from that account. it might be prompting for the password, and thus it is hanging

---

### Post by kerry_s on 2008-04-05
did you set it to not use a password in sudoers?
other wise you need to gksudo to enter your password before it can shutdown.

visudo

user    ALL=NOPASSWD: /sbin/shutdown

---

### Post by GreTTin on 2008-04-05
thanks for replying here is the elevent part from sudoers


```
# User privilege specification
root	ALL=(ALL) ALL
clair   ALL=(ALL) ALL

# Uncomment to allow people in group wheel to run all commands
# %wheel	ALL=(ALL)	ALL

# Same thing without a password
%wheel	ALL=(ALL)	NOPASSWD: ALL

# Samples
# %users  ALL=/sbin/mount /cdrom,/sbin/umount /cdrom
%users  localhost=/sbin/shutdown -h now
%users ALL=NOPASSWD: /sbin/shutdown, /sbin/hwclock
%disk ALL=NOPASSWD: MODUTILS
```

when i run it in a terminal it just hangs. does nothing at all no password prompt.

---

### Post by ghost_ryder35 on 2008-04-05
try your script using 
```

sudo halt

```

---

### Post by GreTTin on 2008-04-05
i get this from the clair account
```
clair: ~ > sudo halt
sudo: halt: command not found
clair: ~ > 
```
it works fine from the root account. 

also as an add to my previous post clair is in the group wheel.
would they conflict with each othersomehow?

---

### Post by ghost_ryder35 on 2008-04-05
> **GreTTin said:**
> i get this from the clair account
```
clair: ~ > sudo halt
sudo: halt: command not found
clair: ~ > 
```
it works fine from the root account. 
 
also as an add to my previous post clair is in the group wheel.
would they conflict with each othersomehow?
the most restrictive wins (unless explisitly stated).... whats wrong with the shutdown button in the upper right hand corner?  I know this kills your purpose.  Maybe there is a way to create a shotcut for the shutdown button in the upper right

---

### Post by kerry_s on 2008-04-05
> **GreTTin said:**
> thanks for replying here is the elevent part from sudoers


```
# User privilege specification
root	ALL=(ALL) ALL
clair   ALL=(ALL) ALL

# Uncomment to allow people in group wheel to run all commands
# %wheel	ALL=(ALL)	ALL

# Same thing without a password
%wheel	ALL=(ALL)	NOPASSWD: ALL

# Samples
# %users  ALL=/sbin/mount /cdrom,/sbin/umount /cdrom
%users  localhost=/sbin/shutdown -h now
%users ALL=NOPASSWD: /sbin/shutdown, /sbin/hwclock
%disk ALL=NOPASSWD: MODUTILS
```

when i run it in a terminal it just hangs. does nothing at all no password prompt.

are your user's in the %users group? /etc/group
default no 1 is in users(see pic)
if not you should use there name.

---

### Post by GreTTin on 2008-04-05
yeah she's definatley in the users group.

It's not a must i just thoughtit would be simpler for her to use than going through the menu, it just worries me that it didn't work. i thought the way i did it would be fine. maybe it's somethin to do with the way i set up sudo? is there a way to check sudo from my root account? (i know kind of defeats the purpose) thanks for your help guys

edit: heres my /etc/group ```
root::0:root
bin::1:root,bin,daemon
daemon::2:root,bin,daemon
sys::3:root,bin,adm
adm::4:root,adm,daemon
tty::5:
disk::6:root,adm,clair
lp::7:lp
mem::8:
kmem::9:
wheel::10:root, clair
floppy::11:root,clair
mail::12:mail
news::13:news
uucp::14:uucp
man::15:
audio::17:clair
video::18:clair
cdrom::19:root,clair
games::20:clair
slocate::21:
utmp::22:
smmsp::25:smmsp
tape:x:26:root
mysql::27:
rpc::32:
sshd::33:sshd
gdm::42:
shadow::43:
ftp::50:
apache:x:80:
messagebus:x:81:
haldaemon:x:82:
plugdev:x:83:root,clair
power:x:84:
pop::90:pop
scanner::93:
nobody::98:nobody
nogroup::99:
users::100:clair
console::101:

```

---

### Post by kerry_s on 2008-04-05
> **GreTTin said:**
> yeah she's definatley in the users group.

It's not a must i just thoughtit would be simpler for her to use than going through the menu, it just worries me that it didn't work. i thought the way i did it would be fine. maybe it's somethin to do with the way i set up sudo? is there a way to check sudo from my root account? (i know kind of defeats the purpose) thanks for your help guys

edit: heres my /etc/group code]root::0:root
bin::1:root,bin,daemon
daemon::2:root,bin,daemon
sys::3:root,bin,adm
adm::4:root,adm,daemon
tty::5:
disk::6:root,adm,clair
lp::7:lp
mem::8:
kmem::9:
wheel::10:root, clair
floppy::11:root,clair
mail::12:mail
news::13:news
uucp::14:uucp
man::15:
audio::17:clair
video::18:clair
cdrom::19:root,clair
games::20:clair
slocate::21:
utmp::22:
smmsp::25:smmsp
tape:x:26:root
mysql::27:
rpc::32:
sshd::33:sshd
gdm::42:
shadow::43:
ftp::50:
apache:x:80:
messagebus:x:81:
haldaemon:x:82:
plugdev:x:83:root,clair
power:x:84:
pop::90:pop
scanner::93:
nobody::98:nobody
nogroup::99:
users::100:clair
console::101:
[/code]

your missing a sudo group where clair needs to be in to use sudo, but i see you have a wheel group which is the old style, so->
change->
%users ALL=NOPASSWD: /sbin/shutdown, /sbin/hwclock
to
%wheel ALL=NOPASSWD: /sbin/shutdown, /sbin/hwclock

you can lose->
%users  localhost=/sbin/shutdown -h now

won't work, not even right

---

### Post by GreTTin on 2008-04-05
made those changes, but no change i'm afraid. still does exactly the same. maybe its not a problem with sudo but a problem with user using shutdown? (as absolute linux doesn't let users have access to root commands like slapt-get?) i'm still quite new to linux but trying to learn.

---

### Post by kerry_s on 2008-04-05
i'm out of ideas, i thought i knew how it worked, guess not. :(

---

