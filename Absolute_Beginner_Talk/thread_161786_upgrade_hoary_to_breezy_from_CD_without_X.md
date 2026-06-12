---
title: "upgrade hoary to breezy from CD without X"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by garner_nc on 2006-04-17
I fried my sons system so X does not start. Now would be a good time for an upgrade to breezy from hoary. This machine is not networked. Without X and Gnome and  Synaptic it seems there is no way to just upgrade from the breezy CD, or is there? Does apt-get run from a terminal somehow?

All the Best,
Doug White

---

### Post by macdo on 2006-04-17
Assuming you've got an official CD and not a Mac or a AMD64 system, insert this line into your /etc/apt/sources.list:
```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
```and comment out all the other lines. (Make sure they all start with a hash #)
To edit your /etc/apt/sources.list, type ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
```to back it up, then ```
sudo nano /etc/apt/sources.list
``` to edit it. Nano is a terminal text editor, not very pretty, but it does get the job done. A help file to use it can be found at [http://www.die.net/doc/linux/man/man1/nano.1.html](http://www.die.net/doc/linux/man/man1/nano.1.html)

Then go to a command line and type ```
sudo apt-get update
sudo apt-get dist-upgrade
```Shut down all programs and reboot.
Et voilà!

Remember, it's always a good idea to back up before major changes...

---

### Post by garner_nc on 2006-04-17
Macdo,

    This seems to be working. I'm having to run it from recovery mode. I'll post the end result when finished.

Thanks for the help.

Doug and Aleksandr White
Garner, NC USA

---

### Post by garner_nc on 2006-04-17
This worked GREAT. Thanks again.

All the Best,
Doug White

---

### Post by macdo on 2006-04-18
Just happy to have been able to help!
Have fun.

---

### Post by Charax on 2006-04-18
*Shudder* I wish I'd known about that before I tried to upgrade using the old "Stick the new CD in and hope for the best" method. made an interesting mess of my Hard Disk Partitions though - thanks for the info.

Is there any similar method for "Downgrading" ubuntu? I'm using Hoary but I'm thinking of upgrading to the Dapper beta (I assume it's the same process for the beta as you posted above) - if that messes up (in that charming way Betas do) how would I go back to Hoary without installing from scratch?

---

### Post by macdo on 2006-04-18
Well, I don't know if there's any way to downgrade - you'd need to read the [Apt Howto]("http://www.debian.org/doc/manuals/apt-howto/index.en.html") for that. I would suggest first upgrading to Breezy, though...

From reading the Apt Howto, I **think** that you'd need to create or modify (if it already exists) a file /etc/apt/preferences with this text:
```
Package: *
Pin: release v=5.10,a=breezy,c=main restricted universe multiverse,o=Ubuntu,l=Ubuntu
Pin-Priority: 1001
```
If you *do* try this, please make sure you back up first!

---

### Post by Charax on 2006-04-18
Breezy. Damn, that's what I have. I get confused with the release names. At the mo I'm on 5.10, and that's what I'm going to call it from now on ](*,) 

Looks like an interesting idea, but as I'm on a fairly clean install (hard to do anything when you've spent the last two days on Freeciv) there won't be much to back up.

Well, as I have both the 5.04 and the 5.10 CDs, I'll see if downgrading works, thanks.

---

### Post by macdo on 2006-04-18
Let me know how you get on :-)

---

