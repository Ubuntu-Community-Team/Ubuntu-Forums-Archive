---
title: "Help me understand sudo"
date: 2005-12-19
forum: Absolute Beginner Talk
---

### Post by Adrian on 2005-12-19
Hello!

I must admit that the sudo command puzzles me a little. If I do this:
```

sudo -s
echo -n "disk" > /sys/power/state

```
I will hibernate my machine (doing it from the log out menu doesn't work).

But... If I instead write this:
```
sudo echo -n "disk" > /sys/power/state
```
I get the following error:
```
bash: /sys/power/state: Permission denied
```
without even being asked to type my password.

Why does it "execute" the command BEFORE entering sudo mode?

---

### Post by az on 2005-12-19
[QUOTE=Adrian]Hello!

I must admit that the sudo command puzzles me a little. If I do this:
```

sudo -s
echo -n "disk" > /sys/power/state

```
I will hibernate my machine (doing it from the log out menu doesn't work).

But... If I instead write this:
```
sudo echo -n "disk" > /sys/power/state
```
I get the following error:
```
bash: /sys/power/state: Permission denied
```
without even being asked to type my password.

Why does it "execute" the command BEFORE entering sudo mode?[/QUOTE]

Sudo -s or sudo su makes you root.

sudo (whatever) makes whatever run as you, but with SuperUser priviledges.  It only asks you for your password every five minutes whitin the same session.  So, if you open another terminal, you will need to enter your password again for something you sudo.  But if you run sodu more than once in the same terminal, you will only have to enter your password theone time, and then every five (or is it ten?) minutes.

---

### Post by bb002 on 2005-12-19
I'm only guessing here but i think when you run ```
sudo echo -n "disk" > /sys/power/state
```
i think only the ```
echo -n "disk"
``` runs as root while /sys/power/state runs as yourself without Root writes. I believe that the ">" operator acts a seperater and splits your command into two commands.

try this instead```
echo -n "disk" > sudo /sys/power/state
```

Once again I'm only guessing here.

---

### Post by Adrian on 2005-12-19
Thank you azz for taking the time to answer. However, I'm still puzzled.

[QUOTE=azz]Sudo -s or sudo su makes you root.
sudo (whatever) makes whatever run as you, but with SuperUser priviledges. 
[/QUOTE]
Ok. But sudo -s is just a "permanent" sudo, right? That is what I've always thought, but my problem above seems to contradict that theory.

[QUOTE=azz]It only asks you for your password every five minutes whitin the same session.  So, if you open another terminal, you will need to enter your password again for something you sudo.  But if you run sodu more than once in the same terminal, you will only have to enter your password theone time, and then every five (or is it ten?) minutes.[/QUOTE]

I've experienced this as well, and I think it's a great feature. The problem is, whenever I do the sudo mentioned above (with the hibernate command), I will NEVER be asked to type my password. I will get the error immediately. If I for instance do a "sudo echo blahblah", it will work as described above. It's just acting strange in combination with the hibernate command.

---

### Post by Adrian on 2005-12-19
[QUOTE=bb002]I believe that the ">" operator acts a seperater and splits your command into two commands.[/QUOTE]

It must be something like that. Thanks!

[QUOTE=bb002]
try this instead: echo -n "disk" > sudo /sys/power/state
[/QUOTE]
That will output text to a file named "sudo". I must say that I'm still puzzled :)

---

### Post by bb002 on 2005-12-19
Crap...Knew I should have test that first. Alright I do some proper experimenting and try to come up with something.

---

### Post by az on 2005-12-19
[QUOTE=Adrian]Thank you azz for taking the time to answer. However, I'm still puzzled.


Ok. But sudo -s is just a "permanent" sudo, right? That is what I've always thought, but my problem above seems to contradict that theory.



I've experienced this as well, and I think it's a great feature. The problem is, whenever I do the sudo mentioned above (with the hibernate command), I will NEVER be asked to type my password. I will get the error immediately. If I for instance do a "sudo echo blahblah", it will work as described above. It's just acting strange in combination with the hibernate command.[/QUOTE]


sudo su (or sudo -s) means "put me into a root shell"  everything you run in that shell has nothing more to do with sudo - you are root.

As for the other issue, I do not know that much about sudo internals - perhaps it does not even try to do the authentification - I dunno.  The principle, though, is that you are not root.  You are you, but with elevated priviledges.

---

### Post by Adrian on 2005-12-19
[QUOTE=bb002]Crap...Knew I should have test that first. Alright I do some proper experimenting and try to come up with something.[/QUOTE]

Thanks, that is much appreciated :)

[QUOTE=azz]The principle, though, is that you are not root. You are you, but with elevated priviledges.[/QUOTE]

Thanks. I think I get the idea. However if I do a "sudo mkdir test", it will be created by root. So me with superuser privileges is root? Then what is the real difference? Sorry I ask a lot of stupid questions here, but I'm not a very experienced Linux user :)

By the way, if i do a "sudo echo blah > test.txt" that file will be created by me (and not by root, as opposed to the mkdir case), so I guess we have the problem here, since I'm not allowed to write to /sys/power/state

---

### Post by bb002 on 2005-12-19
Got it.

here's what I did.
I opened up gedit (or use kwrite if you use KDE) and enter in the following:
```

#!/bin/bash
sudo -s
echo -n "disk" > /sys/power/state

```
I saved the file to my Desktop as "hib-test".
I then right clicked on it and gave it execute permissions (under the premissions tab).

Now I can double click the file, select run in terminal, and enter my password. Then my machine hibernates.


BTY: what happens when you try to hibernate by using the menu? On my laptop the machine will not go into hibernation after selecting the command unless I shut the lid. Otherwise It just goes to a black screen that I can't don't anything on until i either shut the lid to complete the hibernation process of remove the battery.....

---

### Post by Adrian on 2005-12-19
[QUOTE=bb002]Got it.
...
I then right clicked on it and gave it execute permissions (under the premissions tab).
Now I can double click the file, select run in terminal, and enter my password. Then my machine hibernates.[/QUOTE]

Nice solution. A lot more convenient than doing it manually every time :)
Thanks for taking the time to help.

[QUOTE=bb002]BTY: what happens when you try to hibernate by using the menu? On my laptop the machine will not go into hibernation after selecting the command unless I shut the lid. Otherwise It just goes to a black screen that I can't don't anything on until i either shut the lid to complete the hibernation process of remove the battery.....[/QUOTE]
After a couple of seconds my laptop screen is turned off. Then... nothing... for about 10 seconds. Then the computer is shut off. When I start it again, it acts like I never hibernated, i.e. I have to type my user name and password on the login screen to start a totally new session.

---

### Post by bb002 on 2005-12-19
Well I have been googling around and found out why ```
sudo echo -n "disk" > /sys/power/state
```
doesn't work. I'm going to have to write this down ;) this is some need to know info.

> 
In the above context, "echo" does not edit the file, the shell does.


When you redirect output with the '>' or '>>' operators, the shell opens the file to the right of the operator and attaches it to the stdout file descriptor before it launches the command to the left of the operator. That's why the command:

$ sudo echo 59 > /proc/sys/vm/swappiness


.. doesn't work. Although "echo" would run as the root user, the shell that the hypothetical user is running is not. Because it's the shell's job to open /proc/sys/vm/swappiness before running "sudo", the attempt to modify the file will fail.

Found that in a completely unrelated topic here [https://www.redhat.com/archives/fedora-list/2005-July/msg02797.html](https://www.redhat.com/archives/fedora-list/2005-July/msg02797.html)

So what ended up happening in your command is that the file "/sys/power/state" is opened for writing before the sudo even command runs. but "/sys/power/state" is writeable only by root so the command fails before it even starts... :(

---

### Post by Adrian on 2005-12-19
> **bb002]Well I have been googling around and found out why ```
sudo echo -n "disk" > /sys/power/state
```
doesn't work. I'm going to have to write this down  said:**
> https://www.redhat.com/archives/fedora-list/2005-July/msg02797.html[/url]

So what ended up happening in your command is that the file "/sys/power/state" is opened for writing before the sudo even command runs. but "/sys/power/state" is writeable only by root so the command fails before it even starts... :(

Thanks a lot! That was exactly the kind of information I was looking for :)

---

