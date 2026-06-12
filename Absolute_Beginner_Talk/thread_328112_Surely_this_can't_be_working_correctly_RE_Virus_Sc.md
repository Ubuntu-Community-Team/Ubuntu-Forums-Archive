---
title: "Surely this can't be working correctly? RE: Virus Scan"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by linuxbun on 2006-12-30
I've just installed gnome security suite from automatix...

First of all I did:

gksudo clamtk

and updated the signatures (which were up to date). Started it as user again and it said the signatures weren't up to date (whatever I thought). So I selected it to scan my home directory, it pretty much took less than a second and said "scanning complete, xxxxxx signatures scanned" but it didn't scan any files and it says at the bottom "0 files scanned".

What am I doing wrong? :confused: :confused: :confused: 

Only reason i'm scanning is i've received a file from a windows system. Want to make sure it's alright.

---

### Post by taurus on 2006-12-30
Even if the file from Windows contains a virus, it can't do anything since it can't run in Linux unless you use wine or some other Windows emulator to run it!!!

---

### Post by macogw on 2006-12-30
My question being added to this:
how do I run ClamAV?  I sudo aptitude install'd it, but it doesn't show up in the Gnome menus and typing "clam" "clamav" and "clamAV" (ditto to up there's "clamtk" dunno where tk comes from) do nothing.

EDIT:  Wine Is Not an Emulator.  And it can't run Windows viruses.  Some will run inside the terminal and spit out crap.  Then you hit ctrl + c and it stops.  Most can't intall.  If it was an emulator, they'd run just fine.

taurus, the worry can be about passing on the virus, though.  What if the OP opens the file and goes "oh so-and-so might like this!" and passes it on to a bunch of friends, and it turns out to be a virus?  OP will have spread a virus to bunch of Windows users unknowingly.  That's not very nice.  Just because the virus doesn't affect you doesn't mean others are safe from your passing it on.

---

### Post by diepruis on 2006-12-30
Try scanning your home directory with
```

cd
clamscan -r

```
That will make it scan subdirectories as well.

---

### Post by linuxbun on 2006-12-30
> **diepruis said:**
> Try scanning your home directory with
```

cd
clamscan -r

```
That will make it scan subdirectories as well.


That's done the trick, ta :D

---

### Post by arnieboy on 2006-12-30
There is a bug in the menu item that Automatix installs for ClamAV antivirus that is preventing it from showing up in Gnome menu.
This will be fixed in the next release. In the meanwhile, users can do the following:
Open up the following file:
```
sudo gedit /usr/share/applications/antivirus.desktop
```
and change the last line from
> Categories=System;Settings;
to
> Categories=Application;System;
and save and close the file. 
Now a new item will show up in Applications --> System Tools which will run clamtk as root.
-Arnie

---

