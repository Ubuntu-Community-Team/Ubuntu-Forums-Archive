---
title: "Problems with Update Manager"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by hairypete on 2006-10-26
Hi, on the recommendation of a friend, I have switched my laptop from XP to dapper this week.  All was working fine, I managed to configure my wirelss connection without any trouble and I was starting to fall in love with the layout and everything else about ubuntu.  However, I then went to install the 187 updates that were available to me, and once the process got to 
> Configuring capplets-data
the system froze, the terminal popped down, and gave no indication whatsoever of what was going on, then the system rebooted but the desktop was totally blank except for the mouse cursor, so I'm assuming that I'll need to reinstall Ubuntu.](*,) 
As I said, this is my first linux adventure, so is there anyone who could give me a clue to help avoid this happening again?
Thanks

---

### Post by slimdog360 on 2006-10-26
I'm not too sure what happened so I cant give you a fix but if I had to guess perhaps it just ran out of RAM and crashed in a bad spot. Pretty unlucky for that sort of thing to happen.

If you cant get a fix for it and decide to reinstall try making the swap partition bigger. I always make mine about 1GB just to be safe. But then again on both my computers I have big hard drives so space isnt a problem for me.

Also I prefer to use the command line to update my system.
```
sudo apt-get update
``` updates the repository list, checking for new versions of programs etc.
```
sudo apt-get upgrade
``` upgrades those packages.

The graphical updater basically just uses those commands for its self but Id guess using a small amount of RAM to do so. So using the command line would save this Id imagine. Every little bit helps.

---

### Post by dmizer on 2006-10-26
naw ... don't reinstall.

when you get to the point where all you see is a mouse cursor hit:
ctrl + alt + F2

that will drop you to a terminal.

then do:
```
sudo aptitude update
sudo aptitude -f
```

to restart your system from the command line:
```
sudo reboot
```

---

### Post by hairypete on 2006-10-26
> **dmizer said:**
> naw ... don't reinstall.

when you get to the point where all you see is a mouse cursor hit:
ctrl + alt + F2

that will drop you to a terminal.

then do:
```
sudo aptitude update
sudo aptitude -f
```

to restart your system from the command line:
```
sudo reboot
```


Cheers for that - I'll try it when I get home.  Hopefully that should save me a couple of hours tonight!
I think I'll update from the command line in future too!
Thanks guys

---

### Post by indica on 2007-03-17
i've had this problem every time i've tried to update through update manager, in any of my installs, at the exact same position in the process.  it's not an issue for me, i just reboot and run in terminal, but still, thought i'd mention it in case its a common thing.

---

