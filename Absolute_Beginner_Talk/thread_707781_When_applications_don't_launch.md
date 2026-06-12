---
title: "When applications don't launch"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by BetterSense on 2008-02-25
I just upgraded to Gutsy from XP, things are going pretty good. I just found my first windows-like-issue...When I click on synaptic, the bouncing mouse icon appears, and an icon appears in the taskbar with an hour glass, but after about ten seconds these go away and nothing happens. I really want to run synaptic right now but I can't. My first instinct was to reboot, but that's legacy logic, right? 

Nothing is different trying to run synaptic as a command.

---

### Post by PeterJS on 2008-02-25
> **BetterSense said:**
> I just upgraded to Gutsy from XP, things are going pretty good. I just found my first windows-like-issue...When I click on synaptic, the bouncing mouse icon appears, and an icon appears in the taskbar with an hour glass, but after about ten seconds these go away and nothing happens. I really want to run synaptic right now but I can't. My first instinct was to reboot, but that's legacy logic, right? 

It certainly couldn't hurt, but there are probably other ways.

> 
Nothing is different trying to run synaptic as a command.

This however piques my interest, nothing as in nothing at all, or visually it's the same but produces a bunch of error messages in the terminal?

---

### Post by taurus on 2008-02-25
What happens if you run these commands from a terminal?  Do you get any outputs at all?

```
sudo apt-get update
sudo apt-get upgrade
```
If you get nothing in return, then post the output of your ID to see which groups you belong to.

```
id
```

---

### Post by BetterSense on 2008-02-25
Clarification: Running the command 'synaptic' (in the 'run command' area of the Kmenu)  produces identical results, however running 'sudo synaptic' in the terminal actually launched synaptic without error messages (I was hesitant to run synaptic from the console because I thought launching graphical apps from the console was a no-no).

My problem still exists though because when I try to go to 'Administrator Mode' to click 'enable restricted drivers', I can't. I think this has something to do with things requiring root access.

Running apt-get update did a lot of stuff, running apt-get upgrade returned this:

[PHP]chaz@0-1-29-d5-1a-8e:~$ sudo apt-get upgrade
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
chaz@0-1-29-d5-1a-8e:~$       [/PHP]     




BTW what's wrong with this:

[PHP]
chaz@0-1-29-d5-1a-8e:~$ kdesu kwrite /etc/apt/sources.list
Xlib: connection to ":0.0" refused by server
Xlib:
Invalid MIT-MAGIC-COOKIE-1 key


kwrite: cannot connect to X server :0.0

chaz@0-1-29-d5-1a-8e:~$ sudo nano /etc/apt/sources.list=
[sudo] password for chaz:
chaz@0-1-29-d5-1a-8e:~$ kdesu kate /etc/apt/sources.list
Xlib: connection to ":0.0" refused by server
Xlib:
Invalid MIT-MAGIC-COOKIE-1 key


kate: cannot connect to X server :0.0
[/PHP]

Why couldn't I launch kwrite or kate that way?

---

### Post by PeterJS on 2008-02-25
Looks like the problem is with kdesu, that should work, I haven't used KDE in a while so my memory's getting a bit fuzzy, you might try using kdesudo instead and see if that works. That won't help with the menu entries and so forth but it might be a stop gap solution.

Was synpatic open when you tried to run apt-get? The error message it produced was because something else was using the package database (probably synaptic).

---

### Post by aysiu on 2008-02-25
Maybe one of these two threads might help?
["Xlib: Invalid MIT-MAGIC-COOKIE-1 key" on gksu/gksudo](http://ubuntuforums.org/showthread.php?t=248331)
[su wont open apps.](http://ubuntuforums.org/showthread.php?t=115634)

---

### Post by BetterSense on 2008-02-25
Thanks, i closed out synaptic and now i'm downloading a bunch of stuff. I've discovered another manifestation of what I'm hoping is the same problem.....I cannot set my clock. Nothing happens. I suspect it's because it requires root access.

---

### Post by taurus on 2008-02-25
Use sudo/gksudo if you need root privilege.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by BetterSense on 2008-02-25
I understand sudo. To be clear, the problem here is that 

-I cannot graphically launch synaptic
-I cannot enter administrator mode to enable restricted drivers, and I don't know how to do it from the  command line
-I cannot set my clock, clicking on 'adjust date and time' results in absolutely nothing happening, and I don't know how to do it from the command line.

---

