---
title: "Help to get Quake wars to run"
date: 2007-11-08
forum: Absolute Beginner Talk
---

### Post by DawnDisciple on 2007-11-08
I cant get it to work. I got the client on my desktop and am trying to run it from the terminal, so whats wrong with this?

dd@dd-desktop:~$ sudo ETQW-client-1.2.-full.r2.x86.run

Just tells me  command not found

---

### Post by eldragon on 2007-11-08
to run a executable you have to
a. set its permission right
b. call its interpreter :D

since i dont know who interprets ETQW-client-1.2.-full.r2.x86.run we will set its permissions:

```

chomd a+x ETQW-client-1.2.-full.r2.x86.run

```

then you must specify a full path to run files...
so the correct way to do this would be
```

sudo ./ETQW-client-1.2.-full.r2.x86.run

```


hope it helps

cheers

---

### Post by carlosjuero on 2007-11-08
First of all, don't run a game as sudo - the only things you run as sudo are administrative tasks like installation of drivers, resources, etc.

Secondly - have you followed the official instructions? [http://zerowing.idsoftware.com/linux/etqw/](http://zerowing.idsoftware.com/linux/etqw/)

Third, when running from the terminal, you either have to be in the folder the script is in - or you have to specify the path. (eg - ~/Desktop/ETQW-client-1.2-full.r2.x86.run).

Last - this post sorta belongs in the Gaming & Leisure forum.

---

### Post by DawnDisciple on 2007-11-08
When I boot the terminal it has this which you can't take away, is this some form of path?

dd@dd-desktop:~$

edit: Just put this command in my terminal and it starts the install procedure.

~/Desktop/ETQW-client-1.2-full.r2.x86.run

But now its asking for a directory where to install it to, what should I tell it?

---

### Post by samjh on 2007-11-08
> **DawnDisciple said:**
> When I boot the terminal it has this which you can't take away, is this some form of path?

dd@dd-desktop:~$

To put simply, dd is your user name, and dd-desktop is the name you gave your computer.  Linux is an operating system that caters for multiple users  at the same time, so the terminal will show who you are logged in as, and into what computer.  So all dd@dd-desktop means is that a user called "dd" (that's you) is using computer "dd-desktop".

The :~$! is just the prompt, like the > prompt in Microsoft DOS.

As for your other question, I think you've just read my answer in the ETQW forum!!! :D
> When it asks you to specify the directory to install it to, just give it some place in your home directory.
Example: /home/dd/etqw/

---

### Post by DawnDisciple on 2007-11-08
Yes but threw up a Mkdir error.:(

Edit: Okay installing.

---

### Post by samjh on 2007-11-08
Try ```
/home/dd/etqw
```

If that doesn't work, open up your terminal and type ```
mkdir etqw
``` and then run the installer again and type that same directory.

---

### Post by &#12465;&#12452;&#12488; on 2007-11-08
> **carlosjuero said:**
> First of all, don't run a game as sudo - the only things you run as sudo are administrative tasks like installation of drivers, resources, etc.
Running the installer as a superuser is good, unless he's intending to install the game to his home directory.

---

### Post by carlosjuero on 2007-11-08
> **&#12465 said:**
> Running the installer as a superuser is good, unless he's intending to install the game to his home directory.
True, I didn't realize until just now that the file is an installer and not just a wrapper (I don't have Quake Wars).

---

### Post by DawnDisciple on 2007-11-08
Installed it, ran it and got a blank screen, not very good game, nothing to do.:)

---

