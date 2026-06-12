---
title: "edit partitions?"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by locke.dragon on 2007-04-06
SOLVED

i have a dual-boot machine between windows and ubuntu.  i'd like to make the ubuntu partition bigger, but can't.  ubuntu won't let me edit it's own partition while it's running and my live cd i installed from won't run any more (burned at 8x speed).  i've already shrunk the windows partition and now have an empty space in the middle of my drive.  is there a way to expand the ubuntu partition into this empty space from WITHIN ubuntu?

---

### Post by marko_4454 on 2007-04-06
have you tried qtparted??

meaning:

```

sudo qtparted 

```

---

### Post by locke.dragon on 2007-04-06
it said the command wasn't found.  did you mean gparted?  i've tried that.  it won't let me change a partition that's in use and i can't un-mount the ubuntu partition.

---

### Post by marko_4454 on 2007-04-06
well, I meant this one:
[http://qtparted.sourceforge.net/]("http://qtparted.sourceforge.net/")
Try installing it:
```
sudo apt-get install qtparted
```

You will not be able to unmount the ubuntu partition because its in use. 
Also, have you tried running the install CD? That should help more than running live CD. 
in the install CD there is a part for partitioning the HDD.
Maybe this is the only way to do it.

Sorry, but I am not in my linux box as of now, so I cant really try anything. :(

---

### Post by mdsmedia on 2007-04-06
neither gparted nor qtparted will allow you to change the partition while you're running Ubuntu.

The best option, AFAIK, would be to download the QTparted LiveCD from the sourceforge site given above, burn it to disk, and run that, so that you're not in the Ubuntu system when you're trying to change it.

---

### Post by marko_4454 on 2007-04-06
Thanks for helping me out here :)
I knew you had to use qtparted.

---

### Post by locke.dragon on 2007-04-06
ok.  thanks.  will do!

---

