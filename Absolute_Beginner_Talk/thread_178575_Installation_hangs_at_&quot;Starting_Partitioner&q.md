---
title: "Installation hangs at &quot;Starting Partitioner&quot;"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by stevenash on 2006-05-17
Here's a history of what's happened:

I have 1.8GHz processor, 512MB RAM.  I have 2 hard drives: The first is a 40GB drive that has Windows on it.  The second is a brand new 250GB drive with nothing on it.

I started the installation and when I reached the "Starting Partitioner" stage, it loaded to 100% and then the screen went blank.  When I hit Ctrl+C, it restarted the Partitioner, and hangs at 52% every time.

It's not a problem with the speed I burned the ISO at.  Everything checked out fine.

I decided to unplug my first hard drive to see if it would work.  It did.  The partitioner loaded, but I stopped the installation to see if I could get it working with both drives plugged in.  So if no solution is found, I can always do that.

However, does anyone have any ideas as to why this is happening?  All opinions are welcome.  Thanks for your help.

---

### Post by aysiu on 2006-05-17
[QUOTE=stevenash]
It's not a problem with the speed I burned the ISO at.  Everything checked out fine.[/QUOTE] What speed *did* you burn it at? Some people think, for example, that 48x is a slow speed. I would recommend 4x or even 2x.

Also, did you do a checksum on the ISO image *before* you burned it?

See the first half of this page for more details:
[http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)

---

### Post by stevenash on 2006-05-18
I can't remember the exact speed, but I believe it was around 4X...definitely not 48X.  I did not check the md5.  However, when I unplug my 1st hard drive, the partitioner loads and everything is fine.  Don't you think that indicates that there's nothing wrong with the CD?

---

### Post by aysiu on 2006-05-18
[QUOTE=stevenash]I can't remember the exact speed, but I believe it was around 4X...definitely not 48X.  I did not check the md5.  However, when I unplug my 1st hard drive, the partitioner loads and everything is fine.  Don't you think that indicates that there's nothing wrong with the CD?[/QUOTE] You never know.

This may seem unrelated, but the principle is similar. If I get a Netflix DVD in the mail, it'll work on both my wife's laptop/ my desktop *and* our regular DVD players

If we check a DVD out of the library (one that's usually all scuffed up and scratched), it'll work on our computers but *not* our regular DVD players.

Clearly something is wrong with the DVD, even though you could argue that the DVD players are not as good at playing scratched DVDs as the computer DVD-ROM drives are.

So while your hard drive may have something to do with it, that doesn't exclude the possibility that it may work fine if the disk is properly checked. Does that make sense?

---

### Post by stevenash on 2006-05-18
Yes, that makes sense.  I have checked the md5, and it's fine.  I will try burning at a slower speed.

Does anyone else have any suggestions on how to fix the problem if this doesn't work?

---

### Post by Mustard on 2006-05-18
[QUOTE=stevenash]Yes, that makes sense.  I have checked the md5, and it's fine.  I will try burning at a slower speed.

Does anyone else have any suggestions on how to fix the problem if this doesn't work?[/QUOTE]

I'd only be guessing here, as I haven't seen symptoms like this described before, but I wonder whether the jumpers on the back of the drive are set up correctly for 'master' and 'slave', or whether they are using 'cable select'.

I really don't know whether this would affect partitioning, but its just a stab in the dark at what could be wrong on the hardware side of things.

---

### Post by stevenash on 2006-05-18
[QUOTE=Mustard]I'd only be guessing here, as I haven't seen symptoms like this described before, but I wonder whether the jumpers on the back of the drive are set up correctly for 'master' and 'slave', or whether they are using 'cable select'.

I really don't know whether this would affect partitioning, but its just a stab in the dark at what could be wrong on the hardware side of things.[/QUOTE]
Good thought.  On my older 40GB drive, the jumpers are labeled with an M and an S for master and slave.  On my new 250GB drive, however, they are not.  So I just used the same format that was on my old one for my new drive.  However, that doesn't mean that the jumpers are the same for both...but I would assume they are.  Do you know if it changes from drive to drive?

Also, is there any way to check it?

---

### Post by Mustard on 2006-05-18
Normally there is a sticker or illustration of some kind, just above the pins that shows where the jumper needs to be set.  That's the only way I know how to set them myself.  I don't know how standardised these settings are from drive to drive.  I suppose if this sticker is not visible, then you could try the manufacturers website to see what documentation might exist.

-edit-

Just a thought, it should show up in BIOS what the drives are being seen as (assuming you are using 'Auto' for detection), and there should even be some output on the screen regarding the drives during bootup.

---

### Post by desicrew on 2006-05-19
same thing happens to me...however mine gets to the 52% point automatically no need to push Ctrl+C.....


I even removed my slave drive (i have two...one 200gb and one 80gb) and tried it again.....and it ends up at the same place...so I don't know what the heck is going on!!!  ](*,)

---

