---
title: "[SOLVED] Copy the Ubuntu CD in Ubuntu?"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by Joe Dinmore on 2007-11-27
I'm on dial-up, so I get my Ubuntu via ship-it. 
What's the easiest way of making a copy of the Ubuntu CD to share with others?

---

### Post by siciliancasanova on 2007-11-27
I'm not sure of any quick commands.  I know you could put the disk in and use an iso extraction application to copy the image and then you can burn it again.

---

### Post by jordanmthomas on 2007-11-27
There's a program called k3b that does this well.  It is for KDE, which isn't included with Ubuntu so you'll have to install it
applications --> accessories --> terminal
```
sudo apt-get install k3b
```
(or if you don't want to go with a command line, go to system --> administration --> package manager and install it from there)

There *should* be a program in Gnome that will do this, but I'm not a Gnome user so I can't tell you what it is.

I'd do this on the command line myself.  Open a terminal
```
dd if=/dev/cdrom of=Ubunt.iso
```
this will copy the cd to an iso in your home folder.
Then, you can put in a blank cd and burn the iso onto it:
Then, you can use cdrecord to record it.

Or you can be lazy and just right click the file and go to "write to disk" to use nautilus's burner.
The file will be in your home folder, so just go to places --> home folder and right click Ubuntu.iso

---

### Post by Joe Dinmore on 2007-11-28
> **jordanmthomas said:**
> 

I'd do this on the command line myself.  Open a terminal
```
dd if=/dev/cdrom of=Ubunt.iso
```
this will copy the cd to an iso in your home folder.
Then, you can put in a blank cd and burn the iso onto it:
Then, you can use cdrecord to record it.

Or you can be lazy and just right click the file and go to "write to disk" to use nautilus's burner.
The file will be in your home folder, so just go to places --> home folder and right click Ubuntu.iso
cool. Thanks for that.

---

### Post by CatKiller on 2007-11-28
> **Joe Dinmore said:**
> What's the easiest way of making a copy of the Ubuntu CD to share with others?

1: Put the disk in

2: Right-click on the disk icon that's appeared on your desktop

3: Select "Copy Disc..."

That's it, pretty much.

---

### Post by Joe Dinmore on 2007-11-29
> **CatKiller said:**
> 
1: Put the disk in

2: Right-click on the disk icon that's appeared on your desktop

3: Select "Copy Disc..."

That's it, pretty much.
ummmm. Thanks. (slinks away, embarrassed).:oops:

---

### Post by CatKiller on 2007-11-30
> **Joe Dinmore said:**
> ummmm. Thanks. (slinks away, embarrassed).:oops:

No need for embarrassment :)

Unless you already know how powerful Linux is, or don't know about the limitations of other Operating Systems, there are things that it never occurs to you to try. It's one of the nice things about these forums - people share things that they've done, and it gives you inspiration to try something yourself.

---

