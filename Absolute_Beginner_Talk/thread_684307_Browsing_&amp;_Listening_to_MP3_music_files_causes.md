---
title: "Browsing &amp; Listening to MP3 music files causes file directory errors"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Difranco1911 on 2008-01-31
After listening and browsing MP3 music files I get the following error when I try to browse the files.  This only occurs after about 30minutes or so and the only way to recover is reboot the system.  Mounting and unmounting the disk drive is of no use.

Please help.

Thanks in advance.


Excuse me while I go reboot now.

---

### Post by SunnyRabbiera on 2008-01-31
huh, this is odd...

---

### Post by Difranco1911 on 2008-02-01
Tell me about...... it's driving me crazy.  No burning mixes, creating ringtones, or general music fun.

---

### Post by tgalati4 on 2008-02-01
Log in from another machine using ssh.  You may need to install openssh first.  Run your music.  When the machine locks up, see if  you can run the following command from the remote terminal:

dmesg | tail

Look for hardware or disk read errors.  It could be that you have RAM that needs reseating.  Try cleaning out your computer while you are at it.  Run memtest overnight to get 30 passes.

Also realize that many computers share the sound hardware with the I/O hardware and network hardware on the same chip.  I've seen one eMachines with a fried Southbridge by streaming XM radio overnight from the web.  The chip developed a blister and let the magic smoke out.

---

### Post by Difranco1911 on 2008-02-01
Well it's happened again.  The system doesn't lock up so I ran the command you suggested and here are the results:
```


dmesg | tail
[ 2253.265193] attempt to access beyond end of device
[ 2253.265194] sdg: rw=0, want=933887, limit=933651
[ 2253.265257] attempt to access beyond end of device
[ 2253.265259] sdg: rw=0, want=933888, limit=933651
[ 2253.265457] attempt to access beyond end of device
[ 2253.265459] sdg: rw=0, want=933886, limit=933651
[ 2253.265521] attempt to access beyond end of device
[ 2253.265523] sdg: rw=0, want=933887, limit=933651
[ 2253.265585] attempt to access beyond end of device
[ 2253.265586] sdg: rw=0, want=933888, limit=933651


```

As for my system it is a an [ASUS P5-P5G33]("http://usa.asus.com/products.aspx?l1=1&l2=3&l3=409&l4=0&model=1798&modelmenu=1") with quality Corsair memory.  I will run the memtest tonight to see if I can get it to break.

It's also useful to note that I have been running this system since October 2007.  As long as I don't mess with music files I can run my system playing movies, tv shows, etc and not need to even reboot for 2 weeks straight.  I leave my computer on all the time.

Thanks for the useful suggestions and I will try them all.

---

### Post by Difranco1911 on 2008-02-01
memtest came back fine.    So what next?

---

### Post by tgalati4 on 2008-02-01
I have a Sony Ericsson phone with a 4 GB card.  I get similar errors at 4 GB when I connect my phone via USB and it automounts.  It could be an Gutsy bug.  To narrow the problem down, try moving a portion of your music to another drive (either internal or external, or another network machine) and try again and look at dmesg for errors.  Since your RAM is good, and dmesg is indicating a file system error, I would focus on that first.

I was going to reformat my phone memory to see if the error goes away, but I've been lazy, and haven't done it yet.

You can use dmesg | tail -50 to get the last 50 lines to see if anything else is happening.

---

