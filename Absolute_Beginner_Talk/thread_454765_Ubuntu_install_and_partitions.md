---
title: "Ubuntu install and partitions"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by tozza on 2007-05-25
Hi guys,

This is my first attempt to switch to a Linux only distribution.  I have used it before some years ago but never that much but I want to make the switch as much as I can now :)

I have just installed Ubuntu onto my SATA Hdd which is 120Gb.  I just did the default install so I think its just one big partition.

I want to run games and download .torrents.  So what Im looking for is some direction with partitioning.  For example, under windows I have a partition for my games / downloads / OS.

I would probably look to just put games and files on the one partition for now as this is the trial atm (still dual boot windows on a 200Gb) but 120GB should give me a pretty good play.

My main confusion is where stuff gets installed.  So usually I just install basic programs on my C: because they dont take huge amounts of space.  Games though I will install on my D: as they can grow quite big.

Ok this is geting to big now so Ill try to sum it up...
1- looking for some clarity to where stuff is installed and what all the files mean .... /etc /usr etc etc
2- some recommendations on spliiting up my drive
3- maybe some help with remapping some of the pre created directors like /home (which i think is one that needs to be on the new partition) and any others that could move.

Thanks heaps guys,

So far the posts Ive read have been very helpful !! :)

Tozza.

---

### Post by drowner on 2007-05-25
1. The Linux filesystem is different to the windows one. Better, IMO, it gives you a more natural feel to how your computer actually is laid out.

/ is the top, callled 'root' (not the be confused with /root, which is the home directory for the user called root)
[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/) has a good explanation of what all the folders are for.

2. Splitting your drive: [http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning) is the best tutorial. Basically you will need one windows, and one linux partition, and a 'swap' partition.

3. You do not NEED to have a seperate partition for /home. by default it will be located at /home, on the linux filesystem. Some people like to have a seperate partition, and mount, or 'map' it to /home. The advantage of this is that if you do a clean re-installation of linux, your files and settings in your home directory are not removed.

Hope this helps.

---

### Post by tozza on 2007-05-25
Thanks for the reply drowner,

I think I may be over-complicating the issue in my head.

So would the best approach for what Im looking for be say a 10Gb system partition with a 100Gb home and 2Gb swap?.

If I was to install a game do I just stick it in home or will it go into the other directories like /lib and /usr and those other unfamiliar ones?

I think I'm most confused about where programs are being installed to.

Cheers,

Tozza.

---

### Post by drowner on 2007-05-25
> **tozza said:**
> Thanks for the reply drowner,

I think I may be over-complicating the issue in my head.

So would the best approach for what Im looking for be say a 10Gb system partition with a 100Gb home and 2Gb swap?.

If I was to install a game do I just stick it in home or will it go into the other directories like /lib and /usr and those other unfamiliar ones?

I think I'm most confused about where programs are being installed to.

Cheers,

Tozza.

See the first guide ;)

It tells you where programs are installed.

when you install a program, it will not ask you where to install it. Linux installs it where it puts programs. If that makes any sense.

---

### Post by tozza on 2007-05-26
Cheers for the help.

Managed to create new home partition and that was working well.

One more question,

I fiddled with the power controls letting the computer hibernate after 1hr.  This didnt seem to work to well and it would power back up.  I reset it but when I booted up this time the sound was not working.  I checked inside the sound tools and I cant see any reason for it.

Its a bit off my original topic but if anyone has some ideas that would be great :)

Thanks

Tozza.

---

