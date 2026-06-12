---
title: "su command"
date: 2006-02-09
forum: Absolute Beginner Talk
---

### Post by dannyliu on 2006-02-09
Hi,


Could anybody tell me why this command does not work even I enter a
correct password?

Thanks.
Dan

---

### Post by darf681 on 2006-02-09
don't su

if you need to run a command from root

use:

sudo *command*

it will then prompt you for your root password (which should be the same as your first account)

---

### Post by darkbullet87 on 2006-02-10
Someone should explain this and make it a sticky thread. I myself being new to Ubuntu didn't realize the power of sudo at first and had to ask. I'm sure if theres a sticky about it, it will help many people a lot faster. 

Just a though :D

---

### Post by atoponce on 2006-02-10
[quote=darkbullet87]Someone should explain this and make it a sticky thread. I myself being new to Ubuntu didn't realize the power of sudo at first and had to ask. I'm sure if theres a sticky about it, it will help many people a lot faster. 

Just a though :D[/quote]

This is one of the most frequently asked questions in the forums.  Why is root disabled, and what is this sudo thing anyway?

Basically, it works like this:

The root account has been disabled by default (there are a number of security benefits for this).  Your personal account has been added to the sudoers file with administrative priviledges.  With this, every administrative command in the terminal can be accessed without root using the sudo command.  When a password is requested, it is your *personal password*, no other.

Sudo stands for 'switch user and do' something.  By default, you switch user as root to execute the commands.  You can switch user as another user on the system if necessary using the -u switch and the user name in the terminal.

After using sudo, you will see why root was disabled in Ubuntu, and you will come to love the command.  It just makes sense.

---

### Post by SectionThree on 2006-02-10
Well, some flavors of Linux use su, and some use sudo. Ubuntu (Debian) uses sudo, and in case you happen to also be running OS X, so does Darwin.  Anyway, su and sudo are *basically the same thing.*

---

### Post by newuser111 on 2006-02-10
sudo -i iwll give you access to the root shell

---

### Post by darkbullet87 on 2006-02-10
Oh, I realize what sudo does LOL. I'm just saying, that if it's such a frequently asked question why not sticky it? 

IDK...maybee im missing something here...I probably am LOL...never mind

---

### Post by newuser111 on 2006-02-10
[QUOTE=darkbullet87]Oh, I realize what sudo does LOL. I'm just saying, that if it's such a frequently asked question why not sticky it? 

IDK...maybee im missing something here...I probably am LOL...never mind[/QUOTE]

because people dont read the guides or readmes first

---

### Post by darkbullet87 on 2006-02-10
People are lazy :P 

That makes sence though...no point in stickying something no one will read. LOL

---

### Post by aragorn2909 on 2006-02-10
We should keep in mind that some things require su to be active.  Installing nvidia drivers, perhaps.  I couldn't do it without it.  I find that both sudo and su have thier place.  Every distro I have run, I've enable both su and sudo.

---

### Post by darkbullet87 on 2006-02-10
Very true...you make a very good point.

---

### Post by newuser111 on 2006-02-10
not true, sudo -i produces a root shell environment without the need to login through the actual root account (su)

---

### Post by dannyliu on 2006-02-10
Thanks for the answers. 

And here is the link for that.
[https://wiki.ubuntu.com/RootSudo#head-6357ee1f3ec93078a7d7cbc2c627208117e9499d](https://wiki.ubuntu.com/RootSudo#head-6357ee1f3ec93078a7d7cbc2c627208117e9499d)

---

### Post by Klaidas on 2006-02-10
[QUOTE=darkbullet87]Someone should explain this and make it a sticky thread. I myself being new to Ubuntu didn't realize the power of sudo at first and had to ask. I'm sure if theres a sticky about it, it will help many people a lot faster. 

Just a though :D[/QUOTE]

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) :)

---

