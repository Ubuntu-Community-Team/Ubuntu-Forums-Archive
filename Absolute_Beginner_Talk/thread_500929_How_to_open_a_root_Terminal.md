---
title: "How to open a root Terminal"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by Dennis123 on 2007-07-14
This question should be very simple to aswer to, but my problem is that i have to execute a pl file withe the terminal. If I use sudo it says that the file is no command(that is 'berechtigt').
The I thought that I could type su and then enter the root password for 'evaluating' the 
terminal to root level. But this seems impossible cause it says "su: Authentication failure".
The password is the right one, i can use sudo with it so there's no problem.
I guess I'm using su in the wrong way or something can anyone help?
(I'm also sorry for not digging deep enough in some FAQ etc. to find an appropiate solution).

---

### Post by Nekiruhs on 2007-07-14
> **Dennis123 said:**
> This question should be very simple to aswer to, but my problem is that i have to execute a pl file withe the terminal. If I use sudo it says that the file is no command(that is 'berechtigt').
The I thought that I could type su and then enter the root password for 'evaluating' the 
terminal to root level. But this seems impossible cause it says "su: Authentication failure".
The password is the right one, i can use sudo with it so there's no problem.
I guess I'm using su in the wrong way or something can anyone help?
(I'm also sorry for not digging deep enough in some FAQ etc. to find an appropiate solution).
use sudo -i instead of su.

---

### Post by earobinson on 2007-07-14
Note
>  -i  The -i (simulate initial login) option runs the shell specified in
           the passwd(5) entry of the user that the command is being run as.
           The command name argument given to the shell begins with a - to
           tell the shell to run as a login shell.  sudo attempts to change to
           that user&#8217;s home directory before running the shell.  It also ini&#8208;
           tializes the environment, leaving TERM unchanged, setting HOME,
           SHELL, USER, LOGNAME, and PATH, and unsetting all other environment
           variables.  Note that because the shell to use is determined before
           the sudoers file is parsed, a runas_default setting in sudoers will
           specify the user to run the shell as but will not affect which
           shell is actually run.
> -s  The -s (shell) option runs the shell specified by the SHELL envi&#8208;
           ronment variable if it is set or the shell as specified in
           passwd(5).


Im pretty sure you should use sudo -s

---

### Post by Dennis123 on 2007-07-14
Thanks for that reply. But how du I invoke the pl file from the e... terminal?

---

### Post by Dennis123 on 2007-07-14
Oh i found out that it has changed the current directory
now it works as expected thank you all

---

### Post by Nekiruhs on 2007-07-14
> **earobinson said:**
> Note



Im pretty sure you should use sudo -s
sudo -i just asks for your password and logs you into root. It works, its what i've been using for a while now.

---

### Post by The Seeker on 2007-07-14
Another thing you could do is add a root terminal to your menu.

Right-click on Applications > Edit Menus > System Tools > Check 'Root Terminal'.

---

### Post by earobinson on 2007-07-16
> **Nekiruhs said:**
> sudo -i just asks for your password and logs you into root. It works, its what i've been using for a while now.
just because it works dose not mean its the correct way to do things you could also do ```
sudo su
``` I did that for a while and that is not correct.

I was just trying to suggest other options

---

