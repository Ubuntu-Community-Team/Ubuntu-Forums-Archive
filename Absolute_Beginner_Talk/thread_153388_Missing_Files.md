---
title: "Missing Files??"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by etherealbeats on 2006-03-31
Whenever I open a package editor like Synaptic I get this error message:

The following problems were found on your system:

W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)


I have tried doing an apt-get update but to no avail. Any one else know what the problem could be.

Thanks for your help.

---

### Post by trent dillman on 2006-03-31
looks like some sources are messed up in your sources.list...comment out the cdrom entries...

---

### Post by professor_chaos on 2006-03-31
You have the cdrom listed, but you don't have the cd in the drive. I think this is a flaw in the design. It should check the drive and if not available, just move on.

open source.list file ```
sudo gedit /etc/apt/source.list
```
and put a # in front of the cdrom lines.

then apt-get update.

---

### Post by professor_chaos on 2006-03-31
I just have to post this so that I can have the same post count as dillman. Oohh yeah, tied with the dillman. Bring it on.

Sorry for my abuse of this thread, but I couldn't help myself. Peace.

---

### Post by trent dillman on 2006-03-31
Hehe so it's a competition?

I had no idea.

Oh well, you can win if you want. :-P

---

### Post by etherealbeats on 2006-04-01
Thanks, but when i go into that file, there doesnt appear to be any text there, just a blank window?

Thanks for the help guys.

---

### Post by trent dillman on 2006-04-01
sudo gedit /etc/apt/sources.list

typo :-/

---

### Post by professor_chaos on 2006-04-01
oops, sorry about that. "source.list" is when you only have one source. :) :-D Just kidding...of course.

"sources.list" is what you want. Dillman's got my back.

---

### Post by etherealbeats on 2006-04-01
hehe, thanks for the help, worked a treat

---

