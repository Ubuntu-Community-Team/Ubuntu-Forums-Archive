---
title: "Administrative Rights Denied"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by Prime_Numbers on 2007-01-13
Well seems I messed something up.  I am the sole user of this computer and I was trying to authorize myself to access the Synoptic Package Manager.  I must have stripped myself of administrative rights because when I try to access anything related to this I get the message:
"The underlying authorization mechanism (sudo) does not allow you to run this program.  Contact the system adminstrator."  I am the system administrator!!  How can I regain my administrative rights??](*,)   BTW, Ubuntu Dapper user

---

### Post by taurus on 2007-01-13
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
groups
```

Do you remember what you changed on your system?

---

### Post by Prime_Numbers on 2007-01-13
> **taurus said:**
> What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
groups
```

Do you remember what you changed on your system?

No I dont. AAARRRGGGHHH.  Sometimes I wish that I could leave well enough alone

---

### Post by taurus on 2007-01-13
Then what's the output of that command?

```
groups
```

---

### Post by TheRingmaster on 2007-01-13
> **Prime_Numbers said:**
> Well seems I messed something up.  I am the sole user of this computer and I was trying to authorize myself to access the Synoptic Package Manager.  I must have stripped myself of administrative rights because when I try to access anything related to this I get the message:
"The underlying authorization mechanism (sudo) does not allow you to run this program.  Contact the system adminstrator."  I am the system administrator!!  How can I regain my administrative rights??](*,)   BTW, Ubuntu Dapper user


all you have to do is go to system-->administration-->synaptic package manager and then enter you password when asked. what did you do differently??

ps. In linux you are NOT the system admin (root)

---

### Post by aysiu on 2007-01-13
taurus is trying to help you restore administrative privileges.

If you want to do it on your own instead, read this link:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by Prime_Numbers on 2007-01-13
> **taurus said:**
> Then what's the output of that command?

```
groups
```

the output is: 
krash adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin

---

### Post by taurus on 2007-01-13
Did you by any change modify your network files especially /etc/hosts & /etc/hostname?  Can you paste those two files here?

```
cat /etc/hostname
cat /etc/hosts
```

---

### Post by Prime_Numbers on 2007-01-13
> **taurus said:**
> Did you by any change modify your network files especially /etc/hosts & /etc/hostname?  Can you paste those two files here?

```
cat /etc/hostname
cat /etc/hosts
```

I went into system/administration/users and groups    I selected the second setting which I thought would give me more administrative rights.

---

### Post by Prime_Numbers on 2007-01-13
> **Prime_Numbers said:**
> I went into system/administration/users and groups    I selected the second setting which I thought would give me more administrative rights.

krash@Krash:~$ cat /etc/hostname
Krash
krash@Krash:~$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       Krash

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
krash@Krash:~$

---

### Post by taurus on 2007-01-13
Reboot and log in with your username and password.  Now, what happens when you run this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo aptitude update
```

---

### Post by Prime_Numbers on 2007-01-13
> **taurus said:**
> Reboot and log in with your username and password.  Now, what happens when you run this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo aptitude update
```
  

krash@Krash:~$ sudo aptitude update
Password:
krash@Krash:~$

---

### Post by taurus on 2007-01-13
So there's no output in the screen after you ran "sudo aptitude update" (after you typed in your own password) at all?

How about this command?

```
gksudo synaptic
```

---

### Post by Prime_Numbers on 2007-01-13
> **taurus said:**
> So there's no output in the screen after you ran "sudo aptitude update" (after you typed in your own password) at all?

How about this command?

```
gksudo synaptic
```

The terminal says: "krash is not in the sudoers.  This incident will be reported.
I also get an error window that says: "Failed to run synaptic    the underlying authorisation mechanism (sudo) does not allow you tu run this program.  Contact the system administrator.

---

### Post by taurus on 2007-01-13
Okay, it seems to me like you did play around with the /etc/sudoers!!!  Boot into recovery mode from GRUB menu and paste the content of it here.

```
cat /etc/sudoers
```

---

### Post by Prime_Numbers on 2007-01-13
> **taurus said:**
> Okay, it seems to me like you did play around with the /etc/sudoers!!!  Boot into recovery mode from GRUB menu and paste the content of it here.

```
cat /etc/sudoers
```

Hey Taurus, I just  noticed that you are helping a few of us noobs right now and really want to thank you for what you are doing.  I can see you are trully dedicated to help others.  But, Im kind of embarrassed to admit that I have no clue on how to do what you just suggested.  I hate to keep bugging you.

---

### Post by taurus on 2007-01-13
Yes, I have been keeping my eyes on a couple of threads so need to reply them as fast as I can type and click.  Reboot your machine and when you get to the GRUB (and don't see a menu), then press Esc.  Remember, you have three  seconds to press something or it will boot directly into Ubuntu.  And from the GRUB menu, use the down arrow key and highlight the Recovery mode and boot from that.  Then, paste the output of this command here.

```
cat /etc/sudoers
```

---

### Post by Prime_Numbers on 2007-01-13
> **taurus said:**
> Yes, I have been keeping my eyes on a couple of threads so need to reply them as fast as I can type and click.  Reboot your machine and when you get to the GRUB (and don't see a menu), then press Esc.  Remember, you have three  seconds to press something or it will boot directly into Ubuntu.  And from the GRUB menu, use the down arrow key and highlight the Recovery mode and boot from that.  Then, paste the output of this command here.

```
cat /etc/sudoers
```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo command as root
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

#Cmnd alias specification

# Defaults

Defaults      !lecture, tty_tickets,!fqdn
#User privilege specification
root     AAL=(ALL) ALL

#Members of the admin group may gain root privileges
%admin AAL=(ALL) ALL

---

### Post by taurus on 2007-01-13
> **Prime_Numbers said:**
> # /etc/sudoers
#
# This file MUST be edited with the 'visudo command as root
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

#Cmnd alias specification

# Defaults

Defaults      !lecture, tty_tickets,!fqdn
#User privilege specification
root     AAL=(ALL) ALL

#Members of the admin group may gain root privileges
%admin AAL=(ALL) ALL

Here we go.  The **AAL** for both lines (root & %admin) should be **ALL**.

So, you need to edit it and replace them.

```
nano -w /etc/sudoers
```
When you are done, hold <Ctrl> while pressing x to exit.  Answer the question with a Y (for Yes) and hit the return.  And when you are back at the prompt again, see if the changes stick by look at your /etc/sudoers again.

```
cat /etc/sudoers
```

---

### Post by Prime_Numbers on 2007-01-13
> **taurus said:**
> Here we go.  The **AAL** for both lines (root & %admin) should be **ALL**.

So, you need to edit it and replace them.

```
nano -w /etc/sudoers
```
When you are done, hold <Ctrl> while pressing x to exit.  Answer the question with a Y (for Yes) and hit the return.  And when you are back at the prompt again, see if the changes stick by look at your /etc/sudoers again.

```
cat /etc/sudoers
```

Ok I get the same message and the AAL on both lines in ALL

---

### Post by taurus on 2007-01-13
Now reboot with "shutdown -r now" and log in with your username and password.  See what happens this time when you run this command?

```
gksudo synaptic
```

---

### Post by Prime_Numbers on 2007-01-13
> **taurus said:**
> Now reboot with "shutdown -r now" and log in with your username and password.  See what happens this time when you run this command?

```
gksudo synaptic
```
 
A p/w window prompted me for my p/w
then I got the same error message window:
"Failed to run synaptic
The underlying authorisation mechanism (sudo) does not allow you to run this program.  Contact the system administrator."

---

### Post by taurus on 2007-01-13
Boot into recovery mode again and paste the outputs of these commands here.

```
id krash
cat /etc/hostname
cat /etc/hosts
cat /etc/sudoers
```

---

### Post by davesmith on 2007-01-13
when i type in a terminal <cat /etc/sudoers> after entering my password, it says permission denied. How come?

---

### Post by Prime_Numbers on 2007-01-13
> **taurus said:**
> Boot into recovery mode again and paste the outputs of these commands here.

```
id krash
cat /etc/hostname
cat /etc/hosts
cat /etc/sudoers
```

id krash
uid=1000(krash) gid=1000(krash) groups=1000(krash), 4(adm), 20(dialout), 24(cdrom), 24(floppy), 29(audio), 30(dip), 44(video), 106(lpadmin), 110(scanner)

cat /etc/hostname
Krash

cat /etc/hosts
12.0.0.1    local host
12.0.1.1    Krash

#The following lines are desirable for IPv6 capable hosts
::1        ip6-localhost  ip6-loopback
fe00::0  ip6-localnet
ff00::0  ip6-mcastpref ix
ff02::1  ip6-allnodes
ff02::2  ip6-allrouters
ff02::3  ip6-allhosts

cat /etc/sudoers
#/etc/sudoers
#
#This file MUST be edited with the 'visudo' command as root.
#
#See the man page for details on how to write a sudoers file.
#Host alias specification

#User alias specification

#Cmnd alias specification

#Defaults

Defaults        !lecture,tty_tickets,!fqdn

#User privilege specification
root         ALL=(ALL) ALL

#Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

---

### Post by Prime_Numbers on 2007-01-13
BTW,
Which recovery mode should I be using?
Ubuntu, kernel 2.6.15-27-386  or Ubuntu, kernel 2.6.15-23-386 ??  I have been using the first one.

---

### Post by aysiu on 2007-01-13
> **Prime_Numbers said:**
> BTW,
Which recovery mode should I be using?
Ubuntu, kernel 2.6.15-27-386  or Ubuntu, kernel 2.6.15-23-386 ??  I have been using the first one.
I don't think it matters, but you might as well use the one for the latest kernel.

---

### Post by taurus on 2007-01-13
Okay, you didn't belong to group admin (114) in /etc/group.  So boot into recovery mode and add yourself, **krash**, to group admin (near the end of the file) in /etc/group.

```
nano -w /etc/group
```

---

### Post by Prime_Numbers on 2007-01-13
ok so now my synaptic package manager opens but I get and error message telling me that the following problem was found in my system:
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."
But at leas the main problem was solved

---

### Post by TheRingmaster on 2007-01-13
> **Prime_Numbers said:**
> ok so now my synaptic package manager opens but I get and error message telling me that the following problem was found in my system:
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."
But at leas the main problem was solved
so now just close all synaptic windows open a terminal and put > dpkg --configure -a

that should solve your problem

---

### Post by Prime_Numbers on 2007-01-13
First of all I want to thank everyone who has help me today.  I can't tell you how much I appreciate it.  
Now, when I enter dpkg --configure -a, I recieve the message: "dpkg: requested operation requires superuser privilege.

---

### Post by Prime_Numbers on 2007-01-13
Thank you ALL!  I finally got it.  I just didnt really understand what the sudo command was ](*,) .  Thank you for your patience with this noob!

---

### Post by TheRingmaster on 2007-01-13
> **Prime_Numbers said:**
> Thank you ALL!  I finally got it.  I just didnt really understand what the sudo command was ](*,) .  Thank you for your patience with this noob!


that god for taurus huh...lol

---

