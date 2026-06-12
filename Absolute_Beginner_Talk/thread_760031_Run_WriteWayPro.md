---
title: "Run WriteWayPro?"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by kshsj777 on 2008-04-19
I installed Ubuntu a few weeks ago and am trying to get a novelist software, WriteWayPro to run on it.  I've already installed WINE, and the program, but when I try to run it, I get an error saying that it needs Microsoft XML Core Services.

I don't know if that's something that has to be built into WINE, or it's something I can download, install and use on Ubuntu.  If so, where would I have to put the file so that WINE will run WriteWayPro?

I've tried yWriter, but I can't get yWriter 4 to work.  When I try to run it, I get "Error 13 in Form_Load Type Mismatch"  though I can get yWriter 3 to work.  However, I don't like the interface very much, and I much prefer WriteWayPro.

If you have any idea how to get WriteWayPro to work, I would very much appreciate it.  If there isn't any way to get it work, any suggestions for a similar software to WriteWayPro would be very much appreciated too.

---

### Post by Oldsoldier2003 on 2008-04-19
> **kshsj777 said:**
> I installed Ubuntu a few weeks ago and am trying to get a novelist software, WriteWayPro to run on it.  I've already installed WINE, and the program, but when I try to run it, I get an error saying that it needs Microsoft XML Core Services.

I don't know if that's something that has to be built into WINE, or it's something I can download, install and use on Ubuntu.  If so, where would I have to put the file so that WINE will run WriteWayPro?

I've tried yWriter, but I can't get yWriter 4 to work.  When I try to run it, I get "Error 13 in Form_Load Type Mismatch"  though I can get yWriter 3 to work.  However, I don't like the interface very much, and I much prefer WriteWayPro.

If you have any idea how to get WriteWayPro to work, I would very much appreciate it.  If there isn't any way to get it work, any suggestions for a similar software to WriteWayPro would be very much appreciated too.

I have no experience with the program, but since its an editor you might consider running it in a Windows VM such as VirtualBox. (Thats assuming you have a windows installation CD, Vbox won't let you install from a recovery cd)

You might be able to get more info on your application by checking out the app database over at winehq.org

---

### Post by kshsj777 on 2008-04-19
Thanks, but I couldn't find it listed in the app database in WINE.  Unfortunately, I don't have either a windows installation CD or recovery CD.  Windows came with the computer when I got it three years ago.

Any idea about what Microsoft XML Core Services even is?

---

### Post by kshsj777 on 2008-04-19
I was able to find out from the WriteWayPro website the exact name of the file I needed to download.  It's called msml4.cab, and I installed it in a bunch of folders, since I didn't know where it should go.  However, I keep getting the error message that the program needs Microsoft XML Core services.  Is there a particular folder I should put this in?

---

### Post by ramjet_1953 on 2008-04-19
Unfortunately, I'm not familiar with that package, but you may want to have a look at these:

1. Celtx  (Free)
[http://www.celtx.com/](http://www.celtx.com/)

2. yWriter4 (Works well under WINE) (Free)
[http://www.spacejock.com/yWriter4.html](http://www.spacejock.com/yWriter4.html)

3. Writer's Cafe (Linux Version) (Commercial but worth it)
[http://www.writerscafe.co.uk/](http://www.writerscafe.co.uk/)

Regards,
Roger :cool:

---

### Post by kshsj777 on 2008-04-20
Thanks for the suggestions!

1) Celtx is mostly good for screenplays and I already have that.  It's awesome!

2) I am unable to get yWriter 4 to work on WINE.  I get the following error when I try to run it: Error 13 in Form_Load Type Mismatch.  Any ideas?  P.S. yWriter 3 works.

3)  I tried a free download, but doesn't seem to have the chapter-scene format that I need.

---

### Post by tajmox on 2008-05-12
Wine AppDb says to add richtxt.dlls and richtxt.ocx from an XP install.

---

### Post by kshsj777 on 2008-05-27
Where do I put them?

---

