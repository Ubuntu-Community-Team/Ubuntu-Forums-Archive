---
title: "single line for a root termianl"
date: 2007-08-12
forum: Absolute Beginner Talk
---

### Post by uclalinux on 2007-08-12
I would like to start a root terminal  automaticly  when i start ubuntu, i dont know how to do this. 

i tried

" 'password' | sudo -i"

 what is the correct line of code?

 thanks

---

### Post by felicity on 2007-08-12
Maybe 'gksudo gnome-terminal'? You would still need to enter your password though unless you edit the sudoers file.

---

### Post by uclalinux on 2007-08-15
that is the whole point of using one line, i want to inclused the password in my command.

---

### Post by p_quarles on 2007-08-15
As far as I know, it's impossible to do that without storing your password as a clear text file. Not a very good idea.

---

### Post by uclalinux on 2007-08-25
how would i do that i want to store it in a "clear text file",  this is my home computer, i am the only one who goes on it.

---

### Post by mcduck on 2007-08-26
> **uclalinux said:**
> how would i do that i want to store it in a "clear text file",  this is my home computer, i am the only one who goes on it.

As long as you are connected to Internet you can never rely on being the only user on the computer ;)

---

### Post by Nikron on 2007-08-26
from the man page

> 
-S  The -S (stdin) option causes sudo to read the password from the standard input instead of the terminal device.


I would not advise this, but it's your computer...

---

### Post by aysiu on 2007-08-26
Here's how to do it (even though I think the idea is a terrible one from a security standpoint): 

**Step 1**
Edit the /etc/sudoers file by typing ```
sudo visudo
``` in the terminal.

**Step 2**
Add this line to the end of the file: ```
*userame* ALL = NOPASSWD: /usr/bin/gnome-terminal
``` where *username* is your actual username. Save (Control-X, Y, Enter)

**Step 3**
Add ```
gksudo gnome-terminal
``` to System > Preferences > Sessions > Startup Programs.

---

### Post by rich.bradshaw on 2007-08-26
As mentioned, if you are on the internet, this is a stupid stupid stupid idea.

You *will *get hacked.

---

### Post by uclalinux on 2007-08-26
thank's for the info.

---

### Post by Dr Small on 2007-08-26
> **rich.bradshaw said:**
> As mentioned, if you are on the internet, this is a stupid stupid stupid idea.

You *will *get hacked.
Rich, the attacker has to get past the firewall first, and then find an open port, guess a username and then the password in order to OBTAIN the password, so it's not like it is a big security issue after all.

Dr Small

---

### Post by p_quarles on 2007-08-26
> **Dr Small said:**
> Rich, the attacker has to get past the firewall first, and then find an open port, guess a username and then the password in order to OBTAIN the password, so it's not like it is a big security issue after all.

Dr Small
Not exactly. Now that "sudo" doesn't require a password, it would just take a well-placed script on a web site to take over the system. It's like running an unpatched copy of Win2K. 

Fortunately, there is little incentive for any scripter to try to take over a Linux system with "sudo," since, umm, most of us realize that this is a terrible idea.

---

