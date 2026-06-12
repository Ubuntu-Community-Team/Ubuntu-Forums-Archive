---
title: "Tremulous"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by tdutta on 2007-04-05
Hi there,

Just found this link [http://www.madman2k.net/comments/46/](http://www.madman2k.net/comments/46/) and I'd like to install tremulous from this person's site. I've downloaded the two files to my desktop. What do I do now to install them?

thanks,
Tilak

---

### Post by ubuntu27 on 2007-04-05
IT isn't i the repositories isn't it? I am in another computer so I cannot check it.

enable all the repos like Multiverse, Universe, Restricted by
System/System (? don't remember)/SOftware Sources.
 
Then Open the terminal (Applications/Accesories/Terminal)

and type

```
sudo aptitude install tremulous
``` and hit enter. Type your password, and hit enter again.



That you do it.


If it wasn't in the repository.
Then, you can install the deb package by just double clicking it. ;)

---

### Post by deadgobby on 2007-04-05
So you DL the Deb pack too. Just right click on the mouse and have Gdebi install it. Or open up the  Terminal and 
cd Desktop
-l ( to show the list of stuff on your desk top and copy and past the deb file name after this command
sudo dpkg -i ( deb file name )

---

### Post by tdutta on 2007-04-05
Thanks for your help...

looks like there's something funny with the file tho...

I'll see if I can track down the game somewhere else i guess...

Thanks again!
-T

dpkg-deb: `tremulous_1.1.0-2dapper1_i386.deb' is not a debian format archive
dpkg: error processing tremulous_1.1.0-2dapper1_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 tremulous_1.1.0-2dapper1_i386.deb

---

### Post by Patrick K on 2007-04-05
It's in Add/Remove. I installed ii from there and had no problems.

---

### Post by ubuntu27 on 2007-06-19
> **tdutta said:**
> Hi there,

Just found this link [http://www.madman2k.net/comments/46/](http://www.madman2k.net/comments/46/) and I'd like to install tremulous from this person's site. I've downloaded the two files to my desktop. What do I do now to install them?

thanks,
Tilak

Hey!! Reviving this thread again.

How did the install go?

I just wanted to tell you that if you're running the latest Ubuntu 7.04 (Fesity Fawn), then Tremulous is in the repository, meaning you will be able to install it using Synaptic Package Manager or Add/Remove in Applications menu.

---

