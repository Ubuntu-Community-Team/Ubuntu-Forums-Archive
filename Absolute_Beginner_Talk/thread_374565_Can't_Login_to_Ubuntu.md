---
title: "Can't Login to Ubuntu"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by Freddy Isnot on 2007-03-02
Hi,

A little background info first.

I had Ubuntu 6.10 installed on my computer, it worked fine.  I decided to install Windows XP and try that dual boot thing.  I created a new NTFS partition and installed XP to it. That worked fine.  I even went back with GParted and created a third partition to share data between Ubuntu and Windows.

Except...

I could no longer boot Ubuntu.  So I put in my liveCD and used that to put GRUB back on the MBR.  I was able to get back to Ubuntu.  

Except...

Now I get to the Ubuntu login screen.  I type in my user name and password.  It makes like it is loading, then jumps back to the login screen.  No error message, no "wrong user name or password" message.  I can't get past the login screen.

So I ask the friendly folks here on the Ubuntu Forums, what's up with that?  Any suggestions for a confused user?

---

### Post by taurus on 2007-03-02
Press <Ctrl><Alt>F2 to get to another console.  Log in with your name and password.  Then, post the output of this command here?

```
df  -h
```

---

### Post by Freddy Isnot on 2007-03-02
Ah ha, I think I see what may be causing a problem. 

Here is what I get:
Filesystem    Size    Used   Avail   Use%   Mounted on
/def/hda1     33G      32G       0   100%   /
varrun         363M   128K  363M      1%   /var/run
varlock        363M        0  363M      0%   /var/lock
procbususb    10M   116K   9.9M      2%   /proc/bus/usb
udev             10M   116K   9.9M     2%    /dev
devshm        363M       0   363M     0%    /dev/shm
lrm              363M    18M   346M    5%    /lib/modules/2.6.17-10-generic/volatile

I thought I'd left a couple free gigs on dha1.  I must have not been paying attention when I messed with GParted.  I try resizing the partition and see if that does anything.  

Thanks for telling me about that <ctr><alt>F2 thing.  Now I know.

---

### Post by taurus on 2007-03-02
Try something like this to gain some space for now.

```
sudo aptitude clean
df -h
```

---

### Post by Freddy Isnot on 2007-03-02
I was already in GParted when I read the next post.  I've resized my partitions and now Ubuntu logs me in.  

Thanks for the help!

---

