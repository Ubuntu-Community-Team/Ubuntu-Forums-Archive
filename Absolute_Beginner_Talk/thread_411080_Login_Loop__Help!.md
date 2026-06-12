---
title: "Login Loop?  Help!"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by yerdon on 2007-04-16
Hi everyone,

I've been running Ubuntu on my machine for a while now and everything was going fine.  I went on vacation for a week and when I can back, can no longer log into the machine!

Version: Edgy with Beryl

I see the normal startup process and am prompted for my username and login.  At that point it starts loading the desktop.  I see the desktop starting to come up, but right before it does, the screen goes black with a flashing cursor.  and then I'm prompted for my login again...  The process repeats:

1. Username
2. Password
3. Screen starts to load and now pops up a message: "I've detected a panel already running and will now exit."
4. Black screen with flashing cursor for about 25 seconds.
5. NVIDIA splash screen flashes
6. Back to the username prompt...

HEEEELLLLLPPPP!

What can I do?  I'm pretty new to Linux and have no idea what could be going wrong.  I've restarted the computer several times, but this doesn't help.

Thanks!

Joseph

---

### Post by Happy_Man on 2007-04-16
Apparently, you've got another instance of gnome-panel running. Try cycling through ctrl-alt-f1 to f7 and see whether there's another desktop somewhere.

---

### Post by mendingo84 on 2007-04-16
i would try to reinstall the driver if i were you. that's what i do when things like this happen (they usually do after a kernel upgrade...have you done smth like that?). also Nvidia here. my advice does not guarantee a success, just take it as an advice...

---

### Post by yerdon on 2007-04-16
> **Happy_Man said:**
> Apparently, you've got another instance of gnome-panel running. Try cycling through ctrl-alt-f1 to f7 and see whether there's another desktop somewhere.

I did that and got a prompt.  I can log in there fine.  I then run:

sudo /etc/init.d/?dm restart 

and the login screen comes up again.  But then I get the same thing...

But no other desktops seem to be around.

---

### Post by taurus on 2007-04-16
Can you at least log in from a console with your username and password?

<Ctrl><Alt>F2

Then, what's the output of this command from a prompt?

```
df -h
```

---

### Post by 23meg on 2007-04-16
May your disk be full? It may be the GDM disk space problem.

[https://bugs.launchpad.net/gdm/+bug/35217](https://bugs.launchpad.net/gdm/+bug/35217)

---

### Post by yerdon on 2007-04-16
> **mendingo84 said:**
> i would try to reinstall the driver if i were you. that's what i do when things like this happen (they usually do after a kernel upgrade...have you done smth like that?). also Nvidia here. my advice does not guarantee a success, just take it as an advice...

Do you mean the Nvidia driver?  What command would I use?

---

### Post by yerdon on 2007-04-16
> **taurus said:**
> Can you at least log in from a console with your username and password?

<Ctrl><Alt>F2

Then, what's the output of this command from a prompt?

```
df -h
```

Yes, I was able to log in through a prompt.  I ran the command and it listed different areas.  All of them show available disk space.  most of them 1% use.  The highest usage is 61% on a separate drive.  21G of 36G used.

It doesn't seem to be this issue, but I can try deleting some stuff to test it.  Is there some command where I can clean out unnecessary files?

---

### Post by yerdon on 2007-04-16
I tried sudo apt-get autoclean and it didn't seem to do anything.  But I 

When I log in through the terminal I get an error that says: configuration error - unknown item 'FAIL_DELAY' (notify administrator).

---

### Post by yerdon on 2007-04-16
> **23meg said:**
> May your disk be full? It may be the GDM disk space problem.

[https://bugs.launchpad.net/gdm/+bug/35217](https://bugs.launchpad.net/gdm/+bug/35217)

I tried that command.  I also logged in and checked the /tmp folder.  It was completely empty.  But I copied 150MB of files into the /tmp folder just to see if it would fit.  It went in fine.

What is the minimum space that is needed and which folders need the space?

---

### Post by yerdon on 2007-04-16
It doesn't seem to be a space issue since I can copy 150MBs into the /tmp folder.  Any other ideas?

---

### Post by yerdon on 2007-04-16
> **mendingo84 said:**
> i would try to reinstall the driver if i were you. that's what i do when things like this happen (they usually do after a kernel upgrade...have you done smth like that?). also Nvidia here. my advice does not guarantee a success, just take it as an advice...

This fixed it. Thanks!  I completely reinstalled the NVIDIA drivers and now it is up and running again.

Thanks again!

---

### Post by Huss on 2008-01-20
Great. I'll try a driver reinstallation. 

I have the same problem after an xorg update

... ...

---

