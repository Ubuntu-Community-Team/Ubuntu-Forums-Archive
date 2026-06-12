---
title: "Some Programs or Command's won't load"
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by eklypze on 2006-01-06
Hello everyone!
I am currently having a few issues trying to get programs to open or some commands to work.

First problem I have is that my "Login Screen Setup" will not open at all, I have tried many times, and have even restart, yet it still would not open. Another program that does not seem to work is my "Add Applications" program, which has exactly the same situation.

Another problem I have is in Terminal whenever it asks for my password, I try to type but then nothing types, the cursor just stays still. If I type something such as "sudo passwd root", nothing happens either. I have also tried to install Automatix, the "wget http://beerorkid.com/automatix/automatix-ubuntu_4.3-1_i386.deb" line works properly, but after when I input the line "sudo dpkg -i automatix-ubuntu_4.3-1_i386.deb" nothing happens at all.

Is there I way I can fix this or should I re-install Ubuntu *again*? :???: 

Thanks.

---

### Post by carlosqueso on 2006-01-06
It sounds like you've removed yourself from the sudoers list somehow. Boot into recovery mode and type ```
visudo
```  to check and make sure it says ```
%admin  ALL=(ALL) ALL
``` if it does, while still in recovery mode, type ```
nano /etc/group
``` and make sure your user name follows "admin"

EDIT: By the way...when asked for your password, just enter your user password, the system won't show stars or anything, so just enter it and press enter

---

### Post by eklypze on 2006-01-06
OK, thanks for your help, I will try it in a bit. :)

---

### Post by eklypze on 2006-01-06
I have just tried this and when I entered "visudo", it did not have "%admin  ALL=(ALL) ALL", it actually said "root  ALL=(ALL) ALL", is this OK? or should I change it?

---

### Post by carlosqueso on 2006-01-06
you should ADD my text below that line.  Then it should work (at least it looks like my sudoers file).  Post back your results please.

---

### Post by Mustard on 2006-01-06
Alternatively you can just add your username to the bottom, like mine.  The way shown above is a method that sets up the possibility to add other users to a group known as admin, hence the %admin part.  My way would only set up sudo privileges (superuser privileges) for a specific user (me!).

```
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

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
mustard ALL=(ALL) ALL

```

---

### Post by eklypze on 2006-01-06
I got it to work now, thanks a lot guys for all your help. :)

---

