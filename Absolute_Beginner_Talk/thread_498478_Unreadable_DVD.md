---
title: "Unreadable DVD"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by savage.stoo on 2007-07-11
Currently trying to install Medieval II, would be doing it through wine but the disk just sits in the drive and goes round and round and round, give the error "unable to mount media"

Other DVDs, and CDs work, was wondering if anyone else had experienced this problem.

All help welcome.

TY

Stoo

---

### Post by Espreon on 2007-07-11
Is this a game, if so probably a Windows game? If so then try to install it under Wine

```
sudo apt-get install wine
```

If it still does not work than buy Cedega or download the CVS and compile a free Cedega, search for a tutorial of compiling Cedega from CVS, it is on the Gentoo wiki.

---

### Post by splintercellguy on 2007-07-11
I think he's trying to do that, but he's got a media problem.

---

### Post by savage.stoo on 2007-07-11
Yes Medieval II is a game designed for windows, I have Wine installed.

Wine isn't the problem

I'm having problems mounting the disk.

"unable to mount media" then after about 15mins I get an dialog box saying that the disk is blank.

Trying to perform in Terminal, IE,  /media/cdrom0 : dir

brings nothing back

Any further ideas?

---

### Post by Inxsible on 2007-07-11
> **savage.stoo said:**
> Yes Medieval II is a game designed for windows, I have Wine installed.
 
Wine isn't the problem
 
I'm having problems mounting the disk.
 
"unable to mount media" then after about 15mins I get an dialog box saying that the disk is blank.
 
Trying to perform in Terminal, IE, /media/cdrom0 : dir
 
brings nothing back
 
Any further ideas?
Try disabling your auto mount CD Drives feature and then try again. The Windows CD might be trying to run the "AutoStart" of the game which might be a problem in a Linux environment since its a Windows game.
 
System--> Preferences --> Removable Drives and Media

---

### Post by savage.stoo on 2007-07-11
Still no luck. Grr
Will soon start throwing things! ;)



I haven't had any trouble with other installs of MS designed games.

But something really isn't right, i returned the first copy I had to the shop and exchanged for a new copy, and out of the 4 disk I have tried only one has mounted.

---

