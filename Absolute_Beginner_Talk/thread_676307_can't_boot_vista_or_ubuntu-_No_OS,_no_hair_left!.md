---
title: "can't boot vista or ubuntu- No OS, no hair left!"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by cadaly on 2008-01-23
I'm new to linux, installed edubuntu onto a dead laptop for the kids a few weeks ago, liked the look of it and tried to load ubuntu onto my desktop as a dual boot.

Dell Dimension E521
AMD athlon 64xDual Core  2GB memory

Ubuntu wouldn't open from live CD, so I installed from alternate.

Now when I try to boot, I get a choice of Ubunbtu 7.10, or windows Vista, but Ubuntu stops half way though boot, (can't display in this mode) and 
 Vista says:
'windows didn't start, reccommend starting repair,, btu it won't start it. Tried starting normally, and it stops at 
autocheck fail, skip autocheck, then tries to re-boot

I don't know a huge amount about computers, so be gentle...
I've searched forums and tried running ubuntu in safe mode, tried inserting noapic/ nolapic, removing nosplash....etc
can't get a terminal because I can't open ubuntu.
Can't reload vista from recovery disk because it doesn't recognise the partitions?


heeeelp.....

---

### Post by lninjo on 2008-01-23
have you tried system repair with the vista disk. Sounds like your missing your mbr. Did ubuntu ever boot on your computer?
I had the same problem, I have 3 partitions, vista, xp, ubuntu. I had a problem with vista not booting so i had to use the system repair to repair the mbr. what kind of errors do you recieve and did you install vista first or ubuntu first?

---

### Post by lninjo on 2008-01-23
also are you using 64 bit or 32 bit install for your computer?

---

### Post by nikoPSK on 2008-01-23
you might have overwritten it, try testdisk. :)

---

### Post by y-lee on 2008-01-23
[SystemRescueCd]("http://www.sysresccd.org/Main_Page") has toolsthat might help. It boots into a command line but startx starts a GUI. Also maybe helpful is [Super Grub Disk]("http://www.linux.com/feature/57240"). I keep both around as well as Knoppix just in case.

---

### Post by cadaly on 2008-01-23
Thanks for such speedy replies...my faith in linux recovering....

The vista disk offers repair, but won't run it, will only run full install, but then stops when it gets to the partitioning bit.

Vista was pre-installed, and I let the ubuntu installer do the guided partition thing.

No, Ubuntu has never booted on the Dell, only on this laptop. (sorry, this is edubuntu, but edubuntu live disk won't boot on dell either)

I used standard (32 bit?) installer, I think.

Not sure what to do with a command line if I get one...
How can I get any of those disks? This laptop is so old htere's no cd writer and the floppy is knackered. (and I don't have a floppy drive on the dell anyway)

---

### Post by bwtranch on 2008-01-23
To tell you the truth, sounds like too many eggs in one basket. Maybe try to lighten the load a bit. (Microsoft means very, very, tiny software that takes up a lot of room)

---

### Post by y-lee on 2008-01-23
> How can I get any of those disks? This laptop is so old there's no cd writer and the floppy is knackered. (and I don't have a floppy drive on the dell anyway)

Do you have any friends that can download and burn them for you?

Are you sure the HD is not trashed?

I always keep rescue disks and floppies around because I'm paranoid. (even an old copy of MS-DOS, lol)

I honestly don't know what is wrong. :confused:

---

### Post by Smelly Avocado on 2008-01-23
did you install ubuntu right?
maybe just start again with vista and try reinstalling ubuntu using this guide
[http://www.acpmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first]("http://www.acpmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first")
It's a great guide, i used it to dualboot my laptop.
and despite how it says to use 7.04 it worked with 7.10
just remember to back up data. (if you have any)

---

### Post by cadaly on 2008-01-23
Ubuntu seems to be installed alright, but incompatible with my system, so it just keeps stopping.
My main problem right now is that I can't get back into vista, so I can't do very much, like nothing....

---

### Post by Dazed_75 on 2008-01-23
Vista is definitely a weird bird in how it boots.  MS designed a whole new methodology for it.  Be careful of web articles which might predate the actual production release of Vista.  The beta and RC versions of vista did not implement the new scheme so many articles were written which were just plain wrong.  Then too, I believe some hardware manufacturers did not implement the new scheme entirely but that is just informed speculation.

In any case, I ran across [http://www.vistabootpro.org/](http://www.vistabootpro.org/) today while researching another problem. I have not used this but saw a couple of glowing users.  At first glance, it looks like it might be useful in fixing your problem getting Vista fixed.  Once that is done, be sure you look only at new articles to fix the dual boot.

---

### Post by cadaly on 2008-01-25
Still working on this!!
Still can't get into either windows vista or ubuntu, so I can't get a terminal window to try some of the things in the threads.
Also when I try to re-load Vista from the Dell recovery disk, it won't load because 'it can't assign a number to partition' or something like that, and aborts re-install. Also aborts repair.
Think ubuntu problem may be the video card, but I can't load a new driver without being able to get into an operating system, unless there's some other way of doing it.
Not sure exactly what my card is, because I can't access system, but from what I remember it is definitely an nvidia one.
Any ideas? If i coudl even get into ububtu, I might be able to access all tthe files on my disk.

---

### Post by bollix47 on 2008-01-25
When GRUB shows you the choices at startup is there a recovery mode (probably the second choice)?

If so, choose it.  This will bring you to a command prompt.

At the command prompt type:

```
dpkg-reconfigure -phigh xserver-xorg

```

Choose vesa for video and the defaults should be good enough for any other questions it asks.

After that's done you can either type reboot or startx.

Post back with any error output.

Good Luck.

---

### Post by cadaly on 2008-01-25
ububntu still stopping half way through booting- I get the ubuntu loading bars, orange and black,but then still getting same message on screen- too fast to read- something about not supporting this this video mode, then figures in yellow underneath. This happens a few times, with script running (white on black) in between. Then blue screen with white box and text:

The  display server has shut down about 6 times in the last 90 secs. It is likely something bad is going on. Waiting for 2 minutes before trying on display :0.

Then it waits and reboots to same.

Any suggestions on how to get back into vista?

---

### Post by cadaly on 2008-02-13
ok, so here's where I am now...
I went back to ubuntu 6.1 live, which runs and installed fine.

I finally managed to get a new install of vista onto my second hard disk by swapping the two installed hard  disks (thank-you liveswap on supergrub) To think that I was a complete beginner a few weeks ago and didn't know what a partition was!!
So I have a kind of dual boot, except that the only way I can switch from one OS to the other is by using the supergrub disk, which is a bit of a  hassle...

But although I like the look and feel of ubuntu, I tend to work more in vista- partly  because of other programs I have installed, but mainly because everything is crystal clear on my screen in windows whereas in ubuntu. it's very slighty fuzzy. Is this to do with the video card incompatability that stopped 7.10 working?
(I also tried damn small linux live cd and system rescue ver 0.4, and neither seem to run with my video card.)

Vista no longer 'sees' the original harddisk on which it was installed (and is still installed by the looks of things, just in a partition not readable by either vista or ubuntu)
Ubuntu is installed in the original disk, and still running ok, and I can access my openoffice files from windows no problem, so I can work from both.
But no way on earth can I seem to be able to access that original windows partition which has my original windows install and all my old e-mails- is there anyway I can get into this? Anyone???

---

### Post by cadaly on 2008-02-13
OK, see post above on how I managed to get vista back up and running, and ubuntu installed and running. 

Just now I even managed to access my old windows e-mails off 'invisible' disk by opening ubuntu (which could see but not read the disk) then writing the folder which looked like it contained e-mails onto a cd. Then I re-booted into vista, opened a brand new windows mail account, and 'imported' the e-mails from the folder on the cd. It's done some funny things along the way, but most of my e-mails seem to be there. 
My e-mails were the only thing I had 'lost' as everything else was on my external backup.

Still booting ubuntu from supergrub... but nearly there (and I've learnt a hell  of alot along the way). 

Ubuntu screen not as crystal clear as windows, keeps making me think I need to clean my glasses. Is this the videao card problem?

---

