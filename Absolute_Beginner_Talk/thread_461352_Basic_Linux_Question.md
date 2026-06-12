---
title: "Basic Linux Question"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by james.gravley on 2007-06-01
Ok, in Windows you have to uninstall a program to remove the program and all of the files, but in Linux do you have to "uninstall" the program or can you just delete a programs files? I am not really sure how all of that works. Thanks for the help.

jmg

---

### Post by krisfrajer on 2007-06-01
Check in applications>> add/remove software if the program you want to uninstall is there.  What type of program you want to remove?

---

### Post by james.gravley on 2007-06-01
I'm trying to uninstall Songbird and its not in the Add/Remove menu or in the synaptic package manager.

---

### Post by Inxsible on 2007-06-01
use
```
sudo aptitude remove songbird
```

---

### Post by james.gravley on 2007-06-01
I typed in the above command and this is what the terminal posted:

Couldn't find any package whose name or description matched "songbird"

I mean the program is installed, it is under applications. So, um, what now?

thanks for the help so far.

---

### Post by BHelts on 2007-06-01
you can try:
```
sudo aptitude remove Songbird
```
linux is case sensitive

how did you install it?

---

### Post by Inxsible on 2007-06-01
How did you install the app ?
 
did you compile from source ?

---

### Post by james.gravley on 2007-06-01
I downloaded it from the website and installed it from the desktop.

---

### Post by Cypher on 2007-06-01
In the terminal try
```

dpkg -l | grep songbird

```
If that doesn't yield anything, go to the Songbird entry under Applications, right click and choose Properties. Go through the tabs and see what the launch executable is called. Then with that info
```

dpkg -I <executable>

```
this should tell you which package songbird is installed as, then you can do
```

sudo apt-get purge <package>

```

---

### Post by BHelts on 2007-06-01
[this link]("http://www.ubuntugeek.com/install-songbird-music-player-in-ubuntu.html") towards the bottom says to remove /opt/songbird and remove from the Applications menu.

---

### Post by Cypher on 2007-06-01
> **BHelts said:**
> [this link]("http://www.ubuntugeek.com/install-songbird-music-player-in-ubuntu.html") towards the bottom says to remove /opt/songbird and remove from the Applications menu.

That article assumes that Songbird was installed with sources (tar.gz) as opposed to Synaptic/Apt-get

---

### Post by james.gravley on 2007-06-01
Ok I tried the first one and nothing happened

I looked through the tabs and under the tab "Launcher" the section "Command" says "Songbird" but when I try that with the next step it says no such file or directory.

---

### Post by BHelts on 2007-06-01
> That article assumes that Songbird was installed with sources (tar.gz) as opposed to Synaptic/Apt-get

yeah, but didn't he say he downloaded from the website and install that way?

---

### Post by james.gravley on 2007-06-01
I downloaded it, but I didn't add it to any kind of menu or any of that stuff. I just double clicked the downloaded package on my desktop. (forgive me, I am a long time Windows user and I am still learning Ubuntu).

---

