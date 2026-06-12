---
title: "Server to Desktop by CD"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by theoldman on 2008-02-09
I would like to include the desktop interface in the server edition of 7.10. on my 2nd machine

I've done it by running the install desktop command, but I've got 7.10 desktop on CD, and I dont really fancy downloading it all again.

Is it possible for the server edition to 'load' the desktop files from the CD instead of from the net?

If so, how?

I'm using CLI on the server edtiion at the moment.

Thanks in advance.

---

### Post by Rocket2DMn on 2008-02-09
Put your desktop cd in the drive, then add the cd to the repos, and install :)
```
sudo apt-cdrom add
sudo apt-get install ubuntu-desktop
```

---

### Post by theoldman on 2008-02-09
Unfortunatly it's still trying to download the information from [http://gb.archive](http://gb.archive).. 

4hr38m

:confused:

---

### Post by Rocket2DMn on 2008-02-09
My bad! I forgot to tell you to run update
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ubuntu-desktop
```
Sorry!

---

### Post by az on 2008-02-09
If you mean the desktop cd, then that won't work.  Yo would need the alternate cd to install packages from.  There are only a few packages on the Desktop cd - the desktop itself is a "live" filesystem which you cannot install using the package manager.

---

### Post by theoldman on 2008-02-09
It mounts, then unmounts the cdrom drive once its read it

when I type sudo apt-get install ubuntu-desktop, it asks to have the server disk put in. then starts downloading from the net again.

Is there a way to get it to not connect to the gb.archives? or should I just pull the network cable out?

To add some more info:

I have downloaded the desktop install to CD (i've used this to install the OS before, so I know that disk works as a desktop install)
I have downloaded the Server install to CD and have also used it to install the server OS, so I know that CD works.

Can I get the desktop GUI from the desktop CD to be installed straight onto the server OS from the CD rather than having to download the ubuntu-desktop package?

---

### Post by Rocket2DMn on 2008-02-09
Why don't you mount it manually, try:
```
sudo mount /dev/cdrom
```
Then try to update/install.  Otherwise you will have to comment out the web sources in your sources.list file:
```
sudo nano /etc/apt/sources.list
```
Placing a # in front of every line except the cdrom.  Then update/install (don't forget update first!).

---

### Post by Ptero-4 on 2008-02-09
Unfortunatelly. You'll need to either download the alternate CD and add it to your sources.list or download the GUI off the net, this is because the desktop CD doesn't contain packages, it's a disk image that gets mounted by the liveCD and used to install, and the server CD doesn't contain the X11 packages (the CD itself is a deb source like the alternate CD, but the X11 stuff isn't included).

---

### Post by Rocket2DMn on 2008-02-09
He said he has the desktop cd, are you sure he can't use that as a repository?  I was certain you could...
In any case, in the time it's taking us to sort this out, you could probably just download it, theoldman.

---

### Post by JoshuaRL on 2008-02-09
You could always try APTonCD from a Linux computer connected to the web.  And the correct command is:
```

sudo aptitude install ubuntu-desktop

```
That's because it's a metapackage and if you ever decide to delete it then apt-get won't allow you.

---

### Post by theoldman on 2008-02-09
> **Rocket2DMn said:**
> In any case, in the time it's taking us to sort this out, you could probably just download it, theoldman.

I just wanted to do a quick install as I wanted to use the system, but instead I will set the download going overnight.

Thank You for trying anyway.

---

