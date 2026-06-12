---
title: "inittab"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by ggaaron on 2007-05-08
My question is, where is /etc/inittab?:confused: There is no such file on my ubuntu linux... And I've searched whole system for this file, but I've got nothing. But it must be somewhere, or ubuntu doesn't use ir? :shock:

---

### Post by Cypher on 2007-05-08
I was equally surprised when I went looking for the /etc/inittab file and the various System V init files that I was used to. Ubuntu uses [Upstart]("http://upstart.ubuntu.com/") to manage the runlevels and loading of files.

---

### Post by fakie_flip on 2007-05-08
Ubuntu does not have an inittab! Want proof? You can try my commands yourself. A simple search before posting would have yielded numerous answers to your question.

[http://www.google.com/search?ie=UTF-8&oe=UTF-8&q=inittab+ubuntu](http://www.google.com/search?ie=UTF-8&oe=UTF-8&q=inittab+ubuntu)

[http://ubuntuforums.org/search.php?searchid=19759570](http://ubuntuforums.org/search.php?searchid=19759570)

```
chris@ubuntu:~$ sudo updatedb && locate inittab
Password:
/usr/lib/upstart/migrate-inittab.pl
/usr/share/ubuntu-docs/ubuntu/sample/inittab_disablectrlaltdelconsole
chris@ubuntu:~$ sudo find / -name inittab
chris@ubuntu:~$ 

```
From one of the search results, I found this.

> init has been replaced by upstart.

if you wish to change you runlevel upstart still looks for the inittab file for a user set runlevel. Just create the inittab file and put the following line in it to boot to runlevel 2

id:2:initdefault:

Next time search before asking. 9 out of 10 times it gives you an answer to your question much faster. If you have searched, and you didn't find an answer, then post. In other words RTFM!

---

### Post by ggaaron on 2007-05-08
After reading ubuntuguide.org where they say to edit /etc/inittab, I assumed that it exists. Thanks for info.

---

### Post by fakie_flip on 2007-05-08
That's a wiki. Someone should login and fix it. I would, but I have to leave soon. Whoever put it there was probably assuming that the inittab still was there like it was in Dapper Drake and previous versions, but it was discontinued after that.

---

### Post by ggaaron on 2007-05-09
I have one more question, where is /etc/modules.conf in ubuntu? There is file named /etc/modules, but there are are only three modules listed, and system loads much more. Is there a way to change the modules loaded at boot?

---

### Post by fakie_flip on 2007-05-09
There is not one. If you want to know why, why don't you search this forum for modules.conf?

```
chris@ubuntu:~$ sudo find / -name modules.conf
Password:
chris@ubuntu:~$
```

---

### Post by fakie_flip on 2007-05-09
I don't like the way Ubuntu has changed things around. It has gotten away from Linux. If you want all of these files to be where you expect them. then you might try Fedora Core 7. It is going to be released soon.

---

### Post by ggaaron on 2007-05-09
I've searched the internet prior to asking, but I haven't found a straight answer not leaving any doubts. Now I have one, quite unfortunate I think. I'm getting more and more disappointed with ubuntu's configurability. Fedora is based on Red Hat from what I recall, and I really prefer deb to rpm, on rpm based systems I had so much trouble with not working dependences. There is new gentoo and maybe if I find enough time, I will try to install it=)

---

### Post by Cypher on 2007-05-09
Fedora uses YUM, which is like APT and you can also run APT on Fedora to get similar functionality.

Each distro has it's own quirk, you just have to figure out what works best for you..

---

### Post by fakie_flip on 2007-05-09
> **ggaaron said:**
> I have one more question, where is /etc/modules.conf in ubuntu? There is file named /etc/modules, but there are are only three modules listed, and system loads much more. Is there a way to change the modules loaded at boot?

[http://ubuntuforums.org/showthread.php?t=2780&](http://ubuntuforums.org/showthread.php?t=2780&)

[http://ubuntuforums.org/showthread.php?t=121912&](http://ubuntuforums.org/showthread.php?t=121912&)

BTW, not all modules get loaded at boot time. If these threads do not answer all of your questions completely, then why don't you ask your questions in them sense the people who posted in them before seem to know about the modules.conf being missing. I know how to get modules not to load. Add the module names to /etc/modprobe.d/blacklist

Look at instructions for installing lm-sensors. I remember seeing instructions on how to get certain modules to load at boot for lm-sensors. Look at the man pages of depmod.

```
man depmod

apropos module
```

What is it that you are trying to do?

---

### Post by fakie_flip on 2007-05-09
I found plenty of search results, so there's no reason you can't either.

[http://ubuntuforums.org/showthread.php?t=56682&highlight=modules.conf](http://ubuntuforums.org/showthread.php?t=56682&highlight=modules.conf)

[http://ubuntuforums.org/showthread.php?t=14992&highlight=modules.conf](http://ubuntuforums.org/showthread.php?t=14992&highlight=modules.conf)

[http://www.devhardware.com/forums/operating-systems-18/ubuntu-question-no-modprobe-conf-91626.html](http://www.devhardware.com/forums/operating-systems-18/ubuntu-question-no-modprobe-conf-91626.html)

Here is a list of search results. You didn't put enough effort into searching. If you did, you would have found out about the modules.conf like I did. You just want someone to tell you all the answers.

[http://www.google.com/search?hl=en&q=modules.conf+ubuntu](http://www.google.com/search?hl=en&q=modules.conf+ubuntu)

---

### Post by Iokua on 2007-05-09
Install the graphical bootup manager from Add/Remove -> Other -> BootUp Manager. Works like a charm.

---

### Post by fakie_flip on 2007-05-10
> **Iokua said:**
> Install the graphical bootup manager from Add/Remove -> Other -> BootUp Manager. Works like a charm.

That's not for getting modules to load on boot. That is for getting services to start or not start on boot.

---

### Post by ggaaron on 2007-05-10
All of the above threads deal with loading modules, not deleting them. But sorry, maybe I should have searched more... I'll try next time, thanks for help and patience=) I've tried to replace modules that are loaded by default with those that fit my computer better. I've tried blacklisting before, but surprisingly modules got loaded anyway... Generic ubuntu kernel doesn't come with forcing rmmod so after boot I can't do anything, as the drivers are in use. Soon, I'll have much time and I'll probably install other distribution, or just recompile the kernel with only the modules I want. Once more, thanks for help=)

---

### Post by fakie_flip on 2007-05-10
$ cat /etc/modules 

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

---

### Post by fakie_flip on 2007-05-10
How did you blacklist them? Whenever I blacklist modules, it works just fine. The font module is still loaded because I haven't rebooted since adding it to my blacklist.

chris@ubuntu:~$ tail -n 4 /etc/modprobe.d/blacklist
blacklist floppy
blacklist bluetooth
blacklist ipv6
blacklist font
chris@ubuntu:~$ lsmod | grep floppy
chris@ubuntu:~$ lsmod | grep bluetooth
chris@ubuntu:~$ lsmod | grep ipv6
chris@ubuntu:~$ lsmod | grep font
font                    9216  1 fbcon
chris@ubuntu:~$

---

### Post by ggaaron on 2007-05-10
I've appended blacklist modulename, added to /etc/modules modules I want to use instead of those used automaicaly, restarted and there was no change. Is there a possibility, that ubuntu forces usage of modules if it would break the system otherwise?

---

### Post by fakie_flip on 2007-05-10
Don't append the modules you want to blacklist to /etc/modules. Append them to /etc/modprobe.d/blacklist like you see in my example. Add the modules that you want loaded to /etc/modules.

---

### Post by fakie_flip on 2007-05-10
If you really don't like what the Ubuntu kernel comes with, then you really ought to configure and compile your own.

---

### Post by ggaaron on 2007-05-10
> **fakie_flip said:**
> Don't append the modules you want to blacklist to /etc/modules. Append them to /etc/modprobe.d/blacklist like you see in my example. Add the modules that you want loaded to /etc/modules.

I did that, sorry for the ambiguous post. I've found a nice guide to making kernel on ubuntu, so probably I'll just not compile the modules I don't want.

---

### Post by bodhi.zazen on 2007-05-10
> **fakie_flip said:**
> Next time search before asking. 9 out of 10 times it gives you an answer to your question much faster. If you have searched, and you didn't find an answer, then post. In other words RTFM!

I do not own or police these forums, but this kind of language is uncalled for and against the Ubuntu code of conduct.

> RTFM, "Go look on google" are two inappropriate responses to a question. If you don't know the answer or don't wish to help, please say nothing instead of brushing off someone's question. Politely showing someone how you searched or obtained the answer to a question is acceptable, even encouraged.

And

> You can also show the user how to search the forums or tell them about the forum search utility. If you wish to remind a user to use search tools or other resources when they have asked a question you feel is basic or common, please be very polite. Any replies for help that contain language disrespectful towards the user asking the question, i.e. "STFU" or "RTFM" are unacceptable and will not be tolerated.

[http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

---

### Post by fakie_flip on 2007-05-11
How's the kernel compiling going? Compiling isn't the hard part. Configuring all the options is.

---

### Post by ggaaron on 2007-05-11
Unfortunately I don't have time now, so It will be at least a week until I start doing anything.

---

### Post by ggaaron on 2007-05-19
I have a new kernel and everything seems to work=)

---

### Post by lessthanjake on 2007-05-20
How do you change the number of tty's to spawn in upstart?

---

### Post by jtraub on 2007-05-20
> How do you change the number of tty's to spawn in upstart?

I guess /usr/share/doc/upstart/README.Debian.gz will help you

---

