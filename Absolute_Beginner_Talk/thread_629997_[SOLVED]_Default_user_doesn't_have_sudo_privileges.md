---
title: "[SOLVED] Default user doesn't have sudo privileges?"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by ian_ryeng on 2007-12-02
Hi all,

I hate that the first post i have on this forum is a problem...

Anyway, i have tried searching for a solution for this issues but found nothing useful that was remotely relevant.

*I just installed Ubuntu Server Edition 7.10 and after install i attempted to install a graphical environment by running:

sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo apt-get install gdm
sudo /etc/init.d/gdm start
sudo dpkg-reconfigure xserver-xorg

The problem was that the default user created during install isn't on the list of sudo users (?) or a warning to that effect. So right now i have a fresh install with no administrative privileges.

If anyone has any advice as to how i can resolve this issue it would be greatly appreciated.

---

### Post by ian_ryeng on 2007-12-02
So, to reiterate.

I need to figure out how to enable or add sudo privileges to the default account created during installation. As for whatever reason (i am assuming this is not normal) my default account has no privileges so i cant install, well, anything...

Please, if anyone has an advice that could be relevant it would be greatly appreciated.

Thank you in advance.

---

### Post by PointyWombat on 2007-12-02
Hello.

Can you get to a privileged shell by any means?

We may have to boot off the live CD, mount your disk, and make changes that way.

---

### Post by ian_ryeng on 2007-12-02
I have not tried to use the live cd to change any settings. I didn't realize you could even do that...

how would i go about doing that? for example, what is it that i can change to create or modify a user to have sudo privileges?

i realize this is a very noobish question, but i suppose thats what i am :)

---

### Post by ruibernardo on 2007-12-02
Hi ian_ryeng,
> **ian_ryeng said:**
> 
The problem was that the default user created during install isn't on the list of sudo users (?) or a warning to that effect. So right now i have a fresh install with no administrative privileges.This is very strange.

Reboot with the recovery option in GRUB (press esc right after the computer boot to see the menu if you don't see it). You will be as root on a console, be careful with what you'll do there.

Add your user to the admin group with:
```
adduser username admin
```Then reboot with
```
reboot
```Next time the computer boots, your username will be able to run sudo.

---

### Post by aysiu on 2007-12-02
Try this:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by ian_ryeng on 2007-12-03
Add your user to the admin group with:
```
adduser username admin
```



I just tried this, but i got the message: "The group 'admin' does not exist"

recovery mode did log me in as a root user though. So this is a step in the right direction. Is there another group that i could try to add to? or where would i find out what group it would be that i need to add my user to?

thank you for your help.

---

### Post by ian_ryeng on 2007-12-03
aysiu. I visited the link you posted and may have discovered the problem in the sudoers file there is no mention of admin group at all

i.e.

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults !lecture,tty_tickets,!fqdn

# User privilege specification
root ALL=(ALL) ALL

# Members of the admin group may gain root privileges                  <--- These two lines are missing
%admin ALL=(ALL) ALL

---

### Post by aysiu on 2007-12-03
> **ian_ryeng said:**
> aysiu. I visited the link you posted and may have discovered the problem in the sudoers file there is no mention of admin group at all ```
# Members of the admin group may gain root privileges                  <--- These two lines are missing
%admin ALL=(ALL) ALL
``` I don't know why those two lines are missing, but definitely add them.

---

### Post by ian_ryeng on 2007-12-06
Thank you so much for your help everyone.

I followed the directions in the link you provided me aysiu and afterwards i could sudo.

It was quite odd that admin just didnt exist! i had to add it to both of the files mentioned in that tutorial.

Thank you all again!

Ian

---

### Post by thelatinist on 2007-12-06
Glad you got the help you needed.  Please be sure to edit the first post to add [Solved] at the beginning of the title.  That way people won't keep clicking on here thinking you still need help.

---

