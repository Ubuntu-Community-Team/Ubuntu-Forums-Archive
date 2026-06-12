---
title: "Alcohol 120% equivilent in Linux?"
date: 2005-08-27
forum: Absolute Beginner Talk
---

### Post by StephanW on 2005-08-27
Is there a program for linux like the windows program Alcohol 120%?

I'm downloading a ripped DVD file and I want to mount it onto a virtual dvd/cd drive so that I can play it.  I don't want to burn it, just play it.

Thanks.

---

### Post by ow50 on 2005-08-27
You'll want to use the "mount" command. I dont' know the exact options you'd use, but read the (long) man pages or search on google.

---

### Post by StephanW on 2005-08-27
Ok thanks, I'll look around for that.

In the mean time, can anyone elaborate more on how to use the mount command?

---

### Post by xmastree on 2005-08-27
Try [**this.**](http://www.ubuntuguide.org/#mountunmountisofileswithoutburning)

---

### Post by jprophet420 on 2008-03-13
> **StephanW said:**
> Ok thanks, I'll look around for that.

In the mean time, can anyone elaborate more on how to use the mount command?

sure. in a nushell, youre just telling the os to mount an image manually without the gui. here is how i mounted my hard drive:

first make a directory to mount it to, ie the mount point:

```
$mkdir /home/youraccount/hdd1
```

then mount,

```
$sudo mount -t ntfs /dev/sda1 /home/youraccount/hdd1
```

its not much different for iso files:

```
$sudo mount -o loop /path/to/file.iso /path/to/mount/point
```

just make sure you have the mount point already created or it wont work.

---

### Post by billgoldberg on 2008-03-13
You can play a .iso dvd file with vlc media player. (I use it to play my ripped dvd's all the time)

No need to mount it.

It seems to be allot of trouble to go to if you can just play it with a video player.

Or am I missing something?

---

### Post by Richieeeeeee on 2008-07-10
There is a tool like Alcohol 120% on windows:

[http://www.acetoneiso.netsons.org/](http://www.acetoneiso.netsons.org/)

---

