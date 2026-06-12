---
title: "No Graphical Interface"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by ooolongT on 2006-08-13
Admittedly, I am out of my league with Ubuntu.  I am now cursing the fact that I didnt do a dual installation with Windows, but I was hoping that I could avoid windows altogether.

Here's my situation.  I have a copy of Ubuntu 5.04 for Intel x86.  I also hae an old laptop on which I was trying to install it.  The laptop is a Toshiba Satellite 2065CDS.  I put in the install disk and went through the installaion process, and didnt seem to have any problems.  However, for soem reason, I get no graphical interface when I start the computer.  All I get is a prompt that says:

t@ubuntu:~$

The one thing that I notice when I start it is that i get a message saying that there is a

"ror * Temporay failure in name resolution    [fail]" 

So I put in the installaion disk and was going to try to reinstall Ubuntu, figuring that there was something wrong with the install, but while I can hear the disk spin up during startup, I cant seem to get to the CD drive and it is not booting from it. 

So then i tried booting in safe mode.  That doesnt sem o help at all, I get the same prompt.

I tried:

sudo /etc/init.d/gdm start 

but it says command not found

So THEN I tried:

sudo aptitude update
Sudo aptitude install 

Both of which seemed to go alright, so then I used:

sudo aptitude install sysv-rc-conf 

and as it was running, all kinds of errors started until it finally said 

Processing was halted becuase there were too many errors.
REading package lists... done
Building dependency tree
Reading extended state information
Initializing package states... Done
t@ubuntu~$

Darn!  Sooo....What do I do now?  Why is the graphical interface not coming up?  How can I make it come up?

---

### Post by taurus on 2006-08-13
What happens if you run this at the prompt?

```

startx

```
If you get command not found, then perhaps you have installed the server version what doesn't come with any window manager.  Therefore, you need to install it with

```

sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm start 

```

---

