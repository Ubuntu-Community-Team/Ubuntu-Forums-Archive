---
title: "Usind dd to create iso from cd doesn't work"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by jelofson on 2008-04-06
I have used the the right-click "Copy Disk" method to create ISO copies of cds without much problem (the progress indicator doesn't really do anything until it's completed, so I didn't even know it was working at first). Now, I would like to try to use the ** dd** command line method to create an ISO of a cd or dvd. I have read in other posts that you can use :
```
dd if=/dev/cdrom of=/home/whatever.iso
```

However, this doesn't work for me. I get the following error:

```
dd: reading `/dev/cdrom': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.00509919 seconds, 0.0 kB/s

```

Is it a mount error? The CD icon shows up on the desktop fine. It's a laptop's internal CD drive.

I have also tried /dev/scd0 as that is the same drive as /dev/cdrom

It's not a huge issue, but I want to know why I can't seem to get this to work.

Thanks, 
Jon

---

### Post by Hospadar on 2008-04-06
you may need to unmount the cd before you can dd it.  I'm not actually sure about this, but you might want to give it a try.

you can do a "df" to see which devices are what if you think you may have the wrong one.  If you have more than one cdrom drive, it will probably be /dev/cdrom0 (assuming it's the zeroth drive.  If you don't think you see it in df, mount it, then df (look for a disk 750-800 Mb big for a cdrom, or 4/8 Gb for a dvd)

---

### Post by Duck2006 on 2008-04-06
Some reading on dd commands.

[http://www.brunolinux.com/02-The_Terminal/The_dd_command.html](http://www.brunolinux.com/02-The_Terminal/The_dd_command.html)

[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

---

### Post by Irihapeti on 2008-04-06
I've come across this issue myself. It seems that dd will copy a *data* CD no problem, but it quits with that error message mentioned earlier if you try to copy a *music* CD.

---

