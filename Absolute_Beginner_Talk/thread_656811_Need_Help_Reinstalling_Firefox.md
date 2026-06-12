---
title: "Need Help Reinstalling Firefox"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by theburchclan on 2008-01-02
Firefox recently stopped working.  When I clicked on the icon is would respond "Firefox is already running, end that session or restart your computer".  No matter how many times I did this, it never changed.  As a result with all my screwing around I ended up removing Firefox via the terminal. Now I cannot get is reinstalled.  Of course this removal no longer makes it available on the Package Manager either.

I have tried to reinstall the entire Xubuntu package with the CD I used to load it originally but this starts the load process and then going starts scrolling down a lot of stuff I don't understand (like I/O errors...)  I have also downloaded Firefox to a thumb drive and copied it to my Xubuntu desktop but I can't figure out how to install it this way either.

As a side note the rest of Xubuntu loads and works fine.

Any help would be greatly appreciated.

---

### Post by ~LoKe on 2008-01-02
Try this in the terminal...
```
sudo dpkg-reconfigure firefox
```
If that doesn't work...try...
```
sudo aptitude install firefox
```

---

### Post by theburchclan on 2008-01-02
On the reconfigure command it returns - firefox is broken or not fully installed

on the install command it returns - could not get lock /var/lib/dpkg/lock - open (11 resource temporarily unavailble

Dan

---

### Post by ~LoKe on 2008-01-02
> **theburchclan said:**
> on the install command it returns - could not get lock /var/lib/dpkg/lock - open (11 resource temporarily unavailble

Close Synaptic first.  Then:
```
sudo aptitude -f install firefox
```

---

### Post by GuitarRocker2562 on 2008-01-03
or in synaptic, install firefox-3.0 not quite the same, and a few bugs, but i like better, lol

---

### Post by ~LoKe on 2008-01-03
> **GuitarRocker2562 said:**
> or in synaptic, install firefox-3.0 not quite the same, and a few bugs, but i like better, lol

Gnome integration, ftw.  I love having my themes consistent.

---

### Post by theburchclan on 2008-01-03
here is the result -

theburchclan@theburchclan-laptop:~$ sudo aptitude -f install firefox
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)</p>
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by ~LoKe on 2008-01-03
You still have synaptic open.  Close it.  If you can't manually, try this (as long as nothing is currently being downloaded/installed):
```
sudo killall synaptic
```

---

### Post by theburchclan on 2008-01-03
I did tried the synaptic route also.

It says "Package firefox has no available version, but exists in the database

---

### Post by theburchclan on 2008-01-03
sudo killall synaptic run.

---

### Post by theburchclan on 2008-01-03
Any other recommendations?  Is there a way to reload it from the CD?

---

### Post by theburchclan on 2008-01-03
I ended up downloading and installing swiftweasel from a different computer.  It loaded right up an I have internet on my laptop again.

Thanks for everyones help.

---

