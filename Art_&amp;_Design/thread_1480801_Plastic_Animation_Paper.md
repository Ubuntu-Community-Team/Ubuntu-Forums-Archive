---
title: "Plastic Animation Paper"
date: 2010-05-11
forum: Art &amp; Design
---

### Post by Metalclay on 2010-05-11
I'm trying to install this:

[http://plasticanimationpaper.dk/download.asp]("http://plasticanimationpaper.dk/download.asp")

I got the tarball extracted, but I don't know where to go from there. After extraction, I just have this folder "pap4_0" on my desktop with files in it. I've been trying to find out how to run the papconfigure.run in it, but I can't come up with anything that works.

Also, the Read Me says to have the pap4_0 file where I want the directory to be "installed" where should I put this? I don't really want to just leave it on my desktop? With windows everything went to user/programfiles, I don't really know where they go here. 

Also, how would I get it to appear in the Applications tab? I got chrome installed and that went where it was supposed to go I guess, but that was a .deb file, so it was quick.

Any help would be appreciated.

---

### Post by Merk42 on 2010-05-12
try going to a terminal  navigating to the folder and typing sudo sh papconfigure.run

That configure file MAY put a launcher in your applications menu

If it doesn't you can go to System > Preferences > Main Menu and put in a shortcut to it manually

---

### Post by Metalclay on 2010-05-12
> **Merk42 said:**
> try going to a terminal  navigating to the folder and typing sudo sh papconfigure.run

That configure file MAY put a launcher in your applications menu

If it doesn't you can go to System > Preferences > Main Menu and put in a shortcut to it manually

Hm, well I just noticed something...it appears at the bottom it says i386, I'm running x64. That's probably why it's not running, yes? Or should it still run either way?

---

### Post by pytheas22 on 2010-05-13
I just installed this on a 64-bit Ubuntu 10.04 system.  There are a few things you need to do to make it work.

First, you need to install the 32-bit version of libstdc++5.  To do that, run these commands (got these from [here]("http://ubuntuforums.org/showthread.php?t=1243005")):

```
cd ~/Desktop
wget http://frozenfox.freehostia.com/cappy/getlibs-all.deb
wget http://nl.archive.ubuntu.com/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-17ubuntu1_i386.deb
sudo dpkg -i getlibs-all.deb
getlibs -i libstdc++5_3.3.6-17ubuntu1_i386.d
```

Then you need to cd to the location of your pap4_0 folder.  If it's on your desktop, this command should do it:

```
cd ~/Desktop/pap4_0
```

From there, run:
```

./papconfigure.run
```

and it should open.

If this works, you should be able to add a menu entry for the application by going to System>Preferences>Main Menu and creating a new item with the command:
```

/home/YOUR-USERNAME/Desktop/pap4_0/papconfigure.run
```

---

### Post by Metalclay on 2010-05-14
jl

---

### Post by Metalclay on 2010-05-14
Thanks! Got it working.

---

