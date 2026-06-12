---
title: "Help with sudo and some other things..."
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by i.herteleer on 2006-02-03
Hello,
I am a complete beginner, installed Ubuntu yesterday, it's great fun :) .
I have a few problems though.
Whenever i try to run a 'sudo ___ ___' command in the terminal, it asks me for a password. I supply it (the password is identical for the root user and the one account i log into), and hit return, after which nothing happens. Typing 'su' first, then inputting my password allows me to work around this, but it's quite annoying, since i have to do this every time i want to execute a sudo command in a new terminal.
Furthermore, i can't access many things, such as synaptic (package manager) or view the list of updates available. Upon starting up my computer, the first time i try running any of these, it asks me for a password, which i supply, and after this it does nothing. After this, if i try to run 'Login screen setup' or view the available updates, for instance, nothing happens either. 
How can I solve these problems? I would like to log in as the root user every time, following instructions found on [http://ubuntuguide.org/]("http://ubuntuguide.org/") but this requires me to open the 'Login screen setup', which as i said, doesn't work. So i'm stuck in a bit of a vicious circle :P. 
Thanks for any help :),
Inti

---

### Post by steve.horsley on 2006-02-03
Not sure what's going on here. The problem is that the GUI tools lose all the error messages. Try opening a command prompt and doing **sudo nautilus** (for want of a better idea), and see if any error messages pop out.

---

### Post by i.herteleer on 2006-02-03
Yet again, asked me for password and did nothing after i entered it.
Typing su, then password allows me to be at root@Inti, and running sudo nautilus there worked fine. But it's frustrating having to type su, then password every time, and still no applications which are password-protected work...
Help!
(Ps. thanks :) nautilus seems to be quite useful, but what exactly is its purpose?)

---

### Post by gravediggers on 2006-02-03
Try reading the wiki on RootSudo.

By default root is locked in Ubuntu. Have you unlocked it ?

Anyway, in the default situation, sudo will want your password, not the root password. This can be changed, but try your own password first and see how you go!

---

### Post by hashimoto on 2006-02-03
Sounds like your username is not in the sudoers list. Check this thread:

[http://www.ubuntuforums.org/showthread.php?t=116195&highlight=visudo](http://www.ubuntuforums.org/showthread.php?t=116195&highlight=visudo)

---

### Post by i.herteleer on 2006-02-03
I followed the instructions in the last post, which solved my problem. But still, I'm confused, since my username (inti)'s password is the same as the root password, so typing that at any password prompt should have allowed things to run fine, though that was not the case. Any explanation for this?

---

### Post by hashimoto on 2006-02-03
Sudo is not equal to su/root. AFAIK all the graphical admisnistrative tools are run as sudo, not root, so they expect that your username is in the sudoers list.


Actually, I just found out that the correct way to add you into the sudoers is to  add ```
%admin ALL = (ALL) ALL
``` to the sudoers file and then add you (user) to the admin group (or any user who should have the sudo rights).

Hope this makes sense. See my sig... ;-)

---

