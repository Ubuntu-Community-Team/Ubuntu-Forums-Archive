---
title: "Root Access [Resolved]"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by Sethalos on 2007-04-25
Hi there,

Simple question. I'm trying to copy files into /usr/share/themes folder, however, when I try I get a "You don't have permissions" error.

How do I go about getting permissions, entering my root pw I guess, but how do I do it?

thanks.

Seth

---

### Post by Bachstelze on 2007-04-25
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by aysiu on 2007-04-25
This will help you do it point-and-click style:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Sethalos on 2007-04-25
Thanks for your response, and I know this must be simple, but I still can't seem to get it to work.

The file is a tar.gz file.  So, I've tried to basically just drag and drop it into the usr/share/themes folder, but still get the error, so then I tried using the command line:

sudo tar xvzf 42967-LiNsta-GTK2.tar.gz -C /usr/share/themes

with no luck.

Is there a way that I can just drag and drop this file into the folder? Or does this have to be done via the command line?

thanks.

Seth

---

### Post by Bachstelze on 2007-04-25
> **Sethalos said:**
> so then I tried using the command line:

sudo tar xvzf 42967-LiNsta-GTK2.tar.gz -C /usr/share/themes

with no luck.

What happened exactly instead of what you expected ?

---

### Post by orb9220 on 2007-04-25
How about System>Prefs>theme and click on Install button and browse to where the package is.

---

### Post by Sethalos on 2007-04-25
Well, darn.  That worked, I just browsed to it, lol.  

See, I knew it was an easy fix, I'm just not firing on all cylinders today I guess.

Thanks all for the help.

Seth

---

### Post by sisco311 on 2007-04-25
System -> Preferences -> Theme
Install Them...
select your theme file and click open
your them is installed

---

### Post by aysiu on 2007-04-25
I know you fixed this particular problem, but did you read the link I posted earlier? That gives you instructions for how to drag and drop into system folders.

---

### Post by Sethalos on 2007-04-25
Thanks Aysiu,

Actually I clicked on the link and it took me to the Ubuntu SUDO page, lol.  I just scrolled down, and read and tried the command, and that worked as well. Thanks so much.

I really do appreciate all of the responses. I have completely removed WinXP from both my laptop and my desktop as of yesterday, and I have yet to find anything that hasn't worked for me through Linux.  

It's certainly a learning process, but with great community support like this, I have no fear my migration to Linux will be relatively painless.

Thanks all.

Seth

---

