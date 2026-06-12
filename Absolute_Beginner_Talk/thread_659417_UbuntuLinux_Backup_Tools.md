---
title: "Ubuntu/Linux Backup Tools?"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by Zimphin on 2008-01-05
I need to remotely back up linux files to a windows server, preferably using click and drag or a GUI tool or a simple command.  I've looked on google, and here but couldn't find an exact answer to what I need.

Are there any tutorials or tools which might help me do this?

Thanks in advance

---

### Post by wolfen69 on 2008-01-05
[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

---

### Post by FurryNemesis on 2008-01-05
rsync is also good - it's in the repos as a .deb

---

### Post by Zimphin on 2008-01-05
Thanks for the quick and helpful responses :)

Specifically, I need to back up files to a windows share folder using an easy tool or command..

I know how to use samba, but I'm writing a tutorial about backing up a few files to a windows shared folder.. If there are any good tools I should include, that woluld be good, the tutorial will first be used by a small company then discarded which is when I can freely post it online.

Any backup tools/tutorials would greatly help,

Thanks

---

### Post by Boelcke on 2008-01-05
This is an older one, and might be more simple than what you're looking for, but I found it helpful in developing my own backup strategy.

[http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087")

---

### Post by dburnett77 on 2008-01-05
I'd just set up a FTP server, and mark your folders on the remote machine to be pulled via archive mechanism you use.  So that, when the change, they are automatically transfered via ports 21-23 to your machine.

Don't forget security.

I believe apachie_lite has a utility built in for this.

---

### Post by Zimphin on 2008-01-05
Thank you all for the helpful replies.. This is excellent, and if there are any more tools/methods to be included in the manual please don't hesitate to add your thought.

Thanks again

---

### Post by Sidewinder1 on 2008-01-06
I'm currently looking into rsync and dd; they're both rather technical and I'm a total noob. I tried clonezilla and it scared the cr@p 'outta me. The last thing I wanna do is screw up my system, trying to back it up ;-)

---

