---
title: "sudo doesn't work"
date: 2005-11-05
forum: Absolute Beginner Talk
---

### Post by juicybananahead on 2005-11-05
Ahem. Hello there!

Well, I'm posting in this forum so that suggests that I know little or nothing about Linux, which isn't far from the truth! Anyway, I have a pretty fundamental problem at the moment. Whenever I try to sudo something e.g. ```
sudo apt-get install firestarter
```nothing happens once I put in my password. The terminal just sits there. Similarly, nothing happens when I try to use any of the System-Administration programs. Once I put in my password... you guessed it, nothing happens. I feel ignored! To configure my system, I had to run as root in Gnome, which I'm told is **not** good practice.

Any ideas?

/juicy

---

### Post by PsychoTrauma on 2005-11-05
I'm not sure why sudo would be acting like that but you might try using the "su" command instead if you have already set a root password.

```
su
apt-get install firestarter
```

---

### Post by juicybananahead on 2005-11-05
[QUOTE=PsychoTrauma]```
sudo apt-get install firestarter
```

Is the way you would want to type it, or was that just a typo?[/QUOTE]
Sharp eyes! T'was a typo.

---

### Post by az on 2005-11-05
Is this a clean install?  Were there any problem during the install?

Boot into recovery mode and run

apt-get -f install

and if that does nothing, try

apt-get install --reinstall sudo


(In recovery mode, you are root, so you do not need to sudo)

Also, did you muck about with your sudoers file?

---

### Post by juicybananahead on 2005-11-05
Hi Azz,

After a bit of quick research I'm beginning to suspect a problem with my sudoers file. Here's the output, if you're interested:

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
juicy   ALL=(ALL)
```
I did muck about with sudoers originally (by modifying the last line to juicy    ALL=(ALL) ALL ) so that I could add root to the list of allowable gnome logins...

/juicy

---

### Post by juicybananahead on 2005-11-05
By the way, I had no problems during the install, although I did have to run it in expert mode because I wanted to install grub to a non-standard location.

---

### Post by juicybananahead on 2005-11-05
Fixed it! Followed the instructions on [http://www.ubuntuforums.org/showthread.php?t=77614](http://www.ubuntuforums.org/showthread.php?t=77614) . Seems the problem arises when you do an expert installation when you're not an expert... ;) 

/juicy

---

