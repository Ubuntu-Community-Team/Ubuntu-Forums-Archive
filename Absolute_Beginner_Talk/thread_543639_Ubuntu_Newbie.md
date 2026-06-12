---
title: "Ubuntu Newbie"
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by Adam_clmns on 2007-09-05
I installed Ubuntu 5.1 lastnight from a disk my Computer teacher gave me. i have my hard disk partitioned with Windows XP running on one and Ubuntu on the other. on Ubuntu i can't figure our how to configure the network to put in my IP and all that please help me.

---

### Post by Hobo Joe on 2007-09-05
You should install Feisty, if I'm not much mistaken, That version is no longer supported.

---

### Post by Adam_clmns on 2007-09-05
i got 5.1 with the hope that i could just update it as soon as i got the internet runnign on the Ubuntu partition. if i could do that i could get fiesty, (which i'm not familiaer with)

---

### Post by Dr Small on 2007-09-05
You can download Feisty Fawn (The current version of Ubuntu) from the Ubuntu Website, here:
[http://ubuntu.com](http://ubuntu.com)

Or, have the latest version shipped to you for free, from here:
[http://shipit.ubuntu.com](http://shipit.ubuntu.com)

Dr Small

---

### Post by mali2297 on 2007-09-05
The best idea is to get the latest version of Ubuntu.

I guess you have Ubuntu 5.10 (Breezy Badger). You can get some information here:
[http://ubuntuguide.org/wiki/Ubuntu](http://ubuntuguide.org/wiki/Ubuntu)

But, as has been mentioned, that version is no longer supported.

---

### Post by Nythain on 2007-09-05
and to answer your actuall question there should be a file in
/etc/network
thats called interfaces.
open it like so
```

gksudo gedit /etc/network/interfaces

```
and you can make all your edits there (i would highly suggest googling how to manually set ip in linux, to find out exactly what you want to change and how to change it in that file)
then a simple
```

sudo /etc/init.d/networking restart

```
will restart the network with the changes made... that is presuming 5.1 isnt so old that it does things differently, if so, i dont know how things worked back then, and would suggest, like the others, downloading feisty, or having it shipped to you.

---

### Post by oldos2er on 2007-09-05
It's not possible to do a direct update from Breezy to Feisty. As others have said, download Feisty, and create a LiveCD. You can boot from the LiveCD and "play" in Ubuntu Feisty (it won't touch your hard drive, unless you tell it to) until you're comfortable with it.

---

### Post by Adam_clmns on 2007-09-05
well, thanx to you all, i'm gonna try to download fiesty, i think i'll just install it right away, i have a separate partition already set up so i can have windows alongside linux. again, thanx


adam_clmns

---

### Post by Adam_clmns on 2007-09-05
well, thanx to you all, i'm gonna try to download fiesty, i think i'll just install it right away, i have a separate partition already set up so i can have windows alongside linux. again, thanx


adam_clmns

---

