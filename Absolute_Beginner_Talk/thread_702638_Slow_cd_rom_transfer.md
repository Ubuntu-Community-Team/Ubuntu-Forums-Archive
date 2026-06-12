---
title: "Slow cd rom transfer"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2008-02-20
I was just transferring data from a cd to my hard drive it 8 minutes to transfer 700mb this is insanely slow and has never happened before. A task like this usually takes under 2 minutes. I checked the process table nothing  else was using processor time except the system monitor its self. Any Ideas?

---

### Post by wpshooter on 2008-02-20
Reboot the machine and see if it takes that long again.  If it does, then maybe you have a problem.

---

### Post by LeAstrale on 2008-02-20
is the cdrom drive more noisy than usual? because then it might be a bad disc (not even or completely circular)

worst case scenario would be that the drive is about to die.

/Astral-1

---

### Post by swoll1980 on 2008-02-20
the dvd rom is brand new only like 4 months old seems as quite as its ever been.  I've got devede converting a file for me right now when it finishes I'll try rebooting and using a different  cd  see if that helps. I never thought it might be the the disk it's self I got the disk at micro center 50 for five dollars  I had one explode on me a month or so ago so maybe they're cheap for a reason

---

### Post by Xyhthyx on 2008-02-20
Try transfering the files using rsync for a speed boost.
```
rsync -rzv <content> <location>
```
For example, to copy everything from cdrom0 to home:
```
rsync -rzv /media/cdrom0/* ~/
```

---

### Post by OffAxis on 2008-02-20
you could also try checking to see if dma is enabled

```
hdparm /dev/cdrom
```

---

### Post by wpshooter on 2008-02-20
> **bloor75 said:**
> the dvd rom is brand new only like 4 months old seems as quite as its ever been.  I've got devede converting a file for me right now when it finishes I'll try rebooting and using a different  cd  see if that helps. I never thought it might be the the disk it's self I got the disk at micro center 50 for five dollars  I had one explode on me a month or so ago so maybe they're cheap for a reason

What do you mean by "**exlode on me**" ?

---

### Post by swoll1980 on 2008-02-20
> **OffAxis said:**
> you could also try checking to see if dma is enabled

```
hdparm /dev/cdrom
```

hdparm /dev/cdrom:
 IO_support    =  0 (default 16-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

---

### Post by swoll1980 on 2008-02-20
> **wpshooter said:**
> What do you mean by "**exlode on me**" ?

It exploded and destroyed my cd rw drive

---

### Post by swoll1980 on 2008-02-20
tried to restart used different cd still slow

---

### Post by OffAxis on 2008-02-20
> IO_support = 0 (default 16-bit)

It's running in 16-bit mode for compatibility; it should be running in 32.
There should also be a dma_enabled flag which returns 0 for inactive and 1 for active.

Try looking up the drive in the BIOS and set the parameters there. (I believe this listing is derived from there).

If everything is okay in the BIOS, and it's still not performing as expected, then you can set a few of the parameters with the hdparm command.

you can enter hdparm (by itself at the command line for a brief help file) or you can check out the man page for a better overview.
```

sudo hdparm -d1 /dev/cdrom
sudo hdparm -c1 /dev/cdrom
```

The switch by itself will RETURN the current state, the switch with a value will SET the current state.
so 
hdparm -c /dev/cdrom
will show the value for the IO_support.

By the way, those are number ones after the letters in the code, not I or L.

---

### Post by swoll1980 on 2008-02-21
when I try turning on the dma I get this error Inappropriate ioctl for device
when I try switching to 32bit I get this error Invalid argument
dma is set to on in the bios

---

### Post by OffAxis on 2008-02-21
can you post the output of 

```
sudo hdparm -I /dev/cdrom
```

and a sub question relating to the output of that command; Does it properly identify your drive?

---

### Post by swoll1980 on 2008-02-21
> **OffAxis said:**
> can you post the output of 

```
sudo hdparm -I /dev/cdrom
```

and a sub question relating to the output of that command; Does it properly identify your drive?

 HDIO_DRIVE_CMD(identify) failed: Input/output error

---

