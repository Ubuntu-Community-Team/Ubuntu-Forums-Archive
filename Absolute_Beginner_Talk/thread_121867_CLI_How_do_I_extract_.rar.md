---
title: "CLI: How do I extract *.rar?"
date: 2006-01-26
forum: Absolute Beginner Talk
---

### Post by tux101 on 2006-01-26
Can extracting rar be done with tar?  If so, how?

---

### Post by kabus on 2006-01-26
No, it can't.
You'll have to install the rar package first (it's in multiverse, I think), then type

rar e *yourfile.rar*

to extract the archive.

---

### Post by asimon on 2006-01-26
[QUOTE=tux101]Can extracting rar be done with tar?  If so, how?[/QUOTE]
No, tar can't extract rar archives. You need 'rar' or 'unrar' for that.

So first install the package 'rar'. Note that you have to enable the multiverse repository for that.

Then you can extract rar archives from the command line with something like
```

rar x foobar.rar

```

If you have rar installed, the graphical archive programs like 'ark' for KDE or file-roller for GNOME should be able to handle rar archives too, but I have never tried them.

BTW: rar is non-free software. There is also a package called 'unrar-free' which is free software. It's able to unpack rar archives but I think it can't handle archives in RAR 3.0 format or later. If you want to use this package use 'unrar' instead of 'rar' above.

---

### Post by tseliot on 2006-01-26
Use Automatix, it will set it up for you.

---

### Post by endokrin on 2006-01-26
Hi,

I tried to install rar but it asks me to insert Ubuntu 5.10 CD into the drive!!??

```

sudo apt-get install rar..............................

Media change: please insert the disc labeled
 'Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)'
in the drive '/cdrom/' and press enter

```

---

### Post by Perfect Storm on 2006-01-26
Then insert thet CD-rom ;) 
There's properly some libs or that it need to use.

Or you can remove the CD-rom disk from the sourcelist if you want it to get it from the internet.

---

### Post by endokrin on 2006-02-01
Lol.. what an idiot (me)

I haven't even SEEN the CD since I installed Ubuntu.. I thought I could get everything I needed from those repository thingies.


I'll try this and hope it works.  If I find the CD...

---

### Post by endokrin on 2006-02-01
Well whatdya know!?!

It works..

If I have a folder that contains about 50 .rar files, how do I extract them all?

When I used to have windows, I could click on one part and it would extract all of them.

When I did this in Ubuntu, it only extracted the files in the first part.rar

(This is a big music collection, and only a couple songs extracted)

---

### Post by Delkster on 2006-02-01
[QUOTE=endokrin]I thought I could get everything I needed from those repository thingies.[/QUOTE]
Everything that is on the CD is in the repositories. However, if you have the Ubuntu CD/DVD enabled as an installation source for apt (check out Settings -> Repositories in Synaptic, for example) and there's no newer version available in the online repositories than on the CD, I guess apt will prefer the CD as a source and ask you to insert it.

If you disable the CD-ROM as an installation source, apt won't ask for it.

---

### Post by Sutekh on 2006-02-01
[QUOTE=endokrin]When I used to have windows, I could click on one part and it would extract all of them.

When I did this in Ubuntu, it only extracted the files in the first part.rar

(This is a big music collection, and only a couple songs extracted)[/QUOTE]
It should have done this correctly.  Did you choose the first archive file to extract from?

Edit: Oh yes you did.

---

