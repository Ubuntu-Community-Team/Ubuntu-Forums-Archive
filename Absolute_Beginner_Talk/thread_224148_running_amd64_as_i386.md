---
title: "running amd64 as i386?"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by bodhidharma on 2006-07-27
Friends,

Thanks the for the help a couple of days ago (I rolled back my
installation until the "mouse ignores clicks for many seconds"
problem went away...).

I'm having all sorts of weirdness with my new homebuilt machine
running Dapper ... well, not really weirdness, it just is hard
to get it working to my satisfaction.  One of the issue (the main
one) seems to be that software often is unhappy that my CPU is
an AMD64 and the available stuff is i386.  My question is: how
does one handle this?  In particular, might it make sense simply
to install the i386 kernel and everything as if it were a Pentium?
Then presumably I would never have this problem, but I would not
take advantage of the faster stuff associated with the 64 bits...
(but the machine is for my teenage son, who probably doesn't care).
Or can one simply install some i386 libraries and binaries and hope
that it will seamlessly go from the amd64 to the i386?  What are
my options?  Any suggestions or good or bad experiences to tell?

Thanks!

---

### Post by Perfect Storm on 2006-07-27
You can use an i386 installation of Ubuntu on an AMD64 computer without any problems. You might want to run:
```
sudo apt-get install linux-k7
```
Afterwards to get a kernel which fit closer to your machine then.
Or if you have multiply proccessor:
```
sudo apt-get install linux-k7-smp
```

---

### Post by The Noble on 2006-07-27
Supposedly, you may want to hold out on using the 64 bit software until edgy+2 or so, as this is when true multiarch will be completed. The next year, multiarch will get really bumpy due to work on it.

Note that this is just what I remember, so maybe someone else knows more exact scheduling.

---

