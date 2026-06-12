---
title: "Getting wireless to work"
date: 2009-06-29
forum: Apple Hardware Users
---

### Post by PerilousPete on 2009-06-29
I have a MacBook 3,1 and I am trying to get my wireless connected.

If I call  rmmod wl ssb; sudo modprobe wl

Then the wireless conection works fine. But after a reboot it's broken again. I have tried blacklisting the file by placing it in /etc/modprobe.d/blacklist.conf as well as blacklist-wl.conf (as I had found after Googling for others with my problem). Neither works (I added a line to each file: blacklist ssb)

I would like to prevent ssb from starting, but if that's not possible then a bit of help getting a bash script to run the above at login would be settled for :)

Thanks

---

### Post by hajk on 2009-07-02
Well, that blacklisting of the ssb module is the right thing to do (you need to do it only once, either in blacklist.conf or in any of the other .conf files in /etc/modprobe.d/). Why then doesn't it work after a reboot? Because your kernel uses initramfs, which speeds up the boot process, but doesn't know about changes to /etc/modprobe.d unless you also run the command```

$ sudo update-initramfs -u
```
Try it, and you'll find that the changes now stick at the next reboot.

Have fun!

---

