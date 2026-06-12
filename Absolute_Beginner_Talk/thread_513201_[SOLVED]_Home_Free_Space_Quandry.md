---
title: "[SOLVED] Home Free Space Quandry"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by stalker145 on 2007-07-30
I noticed recently that I am getting differing notices from the system as to free space in my /home directory. I've enclosed screen captures of Conky/Disk Usage Analyzer, GParted, and of the Gnome System Monitor applet as well as my Conky variables in the even that I did something wrong there.

I'd kinda like to have the 11 missing gigabytes of space if anyone may know how to recover it.

Thanks.

---

### Post by shearn89 on 2007-07-30
kinda weird - looks like its just the disk usage analyser that disagrees... Maybe its just acting up? Are there any other columns you can turn on that show other stuff?

---

### Post by stalker145 on 2007-07-30
> **shearn89 said:**
> kinda weird - looks like its just the disk usage analyser that disagrees... Maybe its just acting up? Are there any other columns you can turn on that show other stuff?

I couldn't find anywhere to enable any extra columns. I guess I could just copy a few gigs of *something* to my home directory and see if it chokes ;)

---

### Post by stalker145 on 2007-07-30
[SIZE="7"]**DUH!!**[/SIZE]

OK, now that I have that out of the way, let me explain. I decided I was going to back up the whole of my /home directory, blast the entire partition, and restore in the hopes of fixing the oddity that was noted. 

Well, as I was backing up, I started to see things like .Trash-root and it's subdirectories being backed up. I did the "I am god" thing, deleted all those files, and realized that THAT is where my space was being taken up - hence the very large and very bold statement above.](*,)

Let this be a lesson to all: Take out the trash or you'll end up running out of space. I'm sure that the files in question have been lurking for months through several installs, upgrades, and tinkerings. 

Thanks to everyone that poked in and thought about my problem and thanks to shearn89 for keeping this alive and not just me talking to myself ;)

---

### Post by shearn89 on 2007-07-31
> **stalker145 said:**
> [SIZE="7"]
OK, now that I have that out of the way, let me explain. I decided I was going to back up the whole of my /home directory, blast the entire partition, and restore in the hopes of fixing the oddity that was noted. 

Well, as I was backing up, I started to see things like .Trash-root and it's subdirectories being backed up. I did the "I am god" thing, deleted all those files, and realized that THAT is where my space was being taken up - hence the very large and very bold statement above.](*,)

Let this be a lesson to all: Take out the trash or you'll end up running out of space. I'm sure that the files in question have been lurking for months through several installs, upgrades, and tinkerings. 

Thanks to everyone that poked in and thought about my problem and thanks to shearn89 for keeping this alive and not just me talking to myself ;)

Haha... nice one. I totally didn't think about hidden files. Cheers for the mention!

---

### Post by Metallinut on 2007-11-03
I'm having a similar problem, but the trash does not seem to be part of it...

1st here's how my partitions look (according to Gparted)

[FONT="Courier New"]
Partition   Filesystem   Mountpoint   Size       Used
/dev/sda2   ext3         /            20.00 GiB  3.16 GiB
/dev/sda3   ext3         /home        26.16 GiB  21.88 GiB
[/FONT]

Now I know that /home shouldn't be using that much space...but here again, it's verified by df -kh:
```
root@lappy3000:/home# df -kh
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              20G  2.9G   16G  16% /
varrun                506M  100K  505M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   84K  506M   1% /dev
devshm                506M   36K  506M   1% /dev/shm
lrm                   506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/sda3              26G   22G  3.0G  88% /home
/dev/scd0             7.6G  7.6G     0 100% /media/cdrom0

```

But if I run Disk Analyzer or du -sh on /home I get this:
```
root@lappy3000:/# du -sh /home
7.9G    /home

```

Now that's a pretty big difference... about 13.98 GB that I cannot account for ANYWHERE.  Where are these files that are taking up so much space?!?  What's going on?

Oh and by the way, this is on a fresh install of Gutsy...

---

