---
title: "Resizing / Partition"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by Rush_898 on 2006-09-06
I have a problem.  When I installed in my newbness I did not understand that the / file system was going to hold so much stuff so now only a short while after install I have filled up all but about 400 megs of my original partition allocation.  My partitions are swap ext 3, /home 60 Gb ext3, / 5 Gb ext 3, and an extended partition of 60 Gb which I created trying to figure this whole thing out.  I also have 60 Gb of unallocated, unformatted space.  The tool I am trying to use is Gparted.  I tried it within the OS but no go, so I tried the live boot version and still the same problem.  It will not let me resize the root partition past it's already set size.  I created the previously mentioned extended partition just making sure that Gparted was working, which it was.  But I'm in a world of hurt if I can't expand my / partition.  Suggestions?

---

### Post by Iowan on 2006-09-06
Check the How-To's - seems like I saw one on just what you seek (moving / ).
I'll see if I can find it again.

[http://www.ubuntuforums.org/showthread.php?t=250104]("http://www.ubuntuforums.org/showthread.php?t=250104")
Not quite it - this is how-to move /Home.

---

### Post by Maxtorm on 2006-09-06
Have you tried Qtparted?  You can find this by searching for "partition" in Applications -> Add/Remove.  That said, if Gparted isn't working in either your installed or live CD environments, I don't see why Qtparted would.  If it's a case of Ubuntu locking the disks, perhaps you could try a bootable CD that is specific to the partitioning task?  For instance, [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) .  I believe you need the full (also referred to as the INSERT version) to get Qtparted.

---

### Post by Brownedwg89 on 2006-09-06
if im correct... the problem you're having is that you want to extend your / partition but you're trying to add space that is not contiguous with your current partition...

you can only make a partition bigger if there is unallocated space right next to it

---

### Post by msandersen on 2006-09-06
With Partition Magic, the original, when resizing the system partition it reboots and resizes before Windows restarts. I've never tried it with either QTParted or Gparted on the Linux root partition, but they probably don't have the capability. I would think it a case of the partition being locked when the system is running.
Since I've tried a few LiveCDs, I do have QTParted as part of, for example, Knoppix or PCLinuxOS, so if you have any of those or other KDE-based Live distros, you probably have QTParted on them. I think the Ubuntu LiveCD has Gparted, not sure. Gparted is currently not as complete as QTparted, for instance it can't yet move partitions.
I think that would be your best bet to resize the Root partition, short of having Partition Magic on a Windows install. I'm sure commandline hackers would be able to make a simple startup script to have parted do it on startup, tho that's of little help to you.

In the meantime, try clearing some space with **apt-get clean** in a terminal. That might clear few hindred Mb by clearing the Apt cache.

---

### Post by jISh on 2006-09-07
Why not nerf the 5GB ext3 you have there (assuming you are listing these in order), then merge the rest of the free space with your /home partition?

Your root partition shouldn't be increasing in size very often, as said above use the```

sudo apt-get clean && sudo apt-get autoclean
```
commands (you can put that in one line).

---

### Post by Rush_898 on 2006-09-07
Ok, I'm downloading the ultimate boot cd, and a live version of knoppix to try QTparted instead of just Gparted.  If that doesn't work I'm not sure. Is anyone sure that PM 8.0 would be able to do this?  Might be worth looking into just to have it. I appreciate the help.  I do think it is a problem of uncontiguous space I'm just not sure how to go about correcting that yet.

---

### Post by mitchtanz on 2006-09-07
Hi, NooB with same problem.

I've tried Gparted 0.1 and am still struggling to install Gparted 0.3. I read previously on these forums that Partition Magic 8.0 would do the job.

Now I have a problem with that. Everytime or with whatever choice I make in PM 8 I get Error 27-cannot unlock drive...ie some other program etc... is using the HDD hard disk. The only one that is obvious to me is GRUB. Does anyone have experience similar to this. Do I have to disable GRUB loader? Or do you think there is another problem?

Noob
Mitch

---

### Post by Boelcke on 2006-09-07
I just did a resizing of partitions on my second PC, as practice for doing it on my main PC (which has more partitions, and will be more complicated and critical).  I figured that would be a good start, since it's a much simpler job.

I used the Gparted live CD, which worked great for me.
[http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/")

What I learned leads me to believe that we can't really suggest a specific strategy unless we see exactly what the map of your drive is.  It seems to get complicated quick.  Let me briefly write what I did, and see if that leads you down a good pathway of thinking about this.

I have a 160gb drive, onto which I installed ubuntu 5.10 some time ago.  Not knowing how much space these things would take, I put my root first, at 55gb, followed by a partition for /home, also 55gb.  I left a bunch of unallocated space, and then put a gig of swap at the end of my drive.

[root=55gb----------][/home=55gb----------]----unallocated-----[swap]

Now, I wanted to shrink the root down to 15gb (only using 4gb right now, having run ubuntu on this machine for about 9 months).  Then, /home could drop down to something like 40gb, and I'd make a separate drive, something like 95gb, which I'm using to store a backup of stuff on another pc (pictures and videos).

Problem is, it seems like you can't move the start of a primary partition, only add to the end.  So I did it in multiple steps.  First, I shrunk my root down to 15gb.

[root=15gb]----------[/home=55gb----------]----unallocated-----[swap]

Then, I created a new, smaller home in the vacated space.

[root=15gb][/home=40][/home=55gb----------]----unallocated-----[swap]

Then, since the new home isn't really a home unless it has your stuff on it, I mounted it
```
sudo mount /dev/hda4 /mnt
```
and then copied everything over
```
sudo cp -a /home/* /mnt
```

Then, I expanded the old home, and call it backup.

[root=15gb][/home=40][/backup=95gb----------------------------][swap]

Naturally, I had to edit the /etc/fstab file to connect to these things in the new way.  I did have some sort of issue with the little volume adjuster in my taskbar (some folks have reported losing sound altogether).  I reinstalled gtk-register and libgstreamer0.8-0 in Synaptec, and everything is now good in my new home.

The only thing I haven't fixed is that the permissions aren't set correctly on the /backup partition, but I'll take care of that when I have a moment (before my next backup cycle).  It seems root is the owner, and I'd like my users to have permissions in there.

I've rambled enough -- hope this is helpful.

---

### Post by msandersen on 2006-09-07
> **mitchtanz said:**
> Hi, NooB with same problem.

I've tried Gparted 0.1 and am still struggling to install Gparted 0.3. I read previously on these forums that Partition Magic 8.0 would do the job.

Now I have a problem with that. Everytime or with whatever choice I make in PM 8 I get Error 27-cannot unlock drive...ie some other program etc... is using the HDD hard disk. The only one that is obvious to me is GRUB. Does anyone have experience similar to this. Do I have to disable GRUB loader? Or do you think there is another problem?

Noob
Mitch
Are you shutting Linux down properly, or just hibernating? If you're hibernating, maybe that's why it's locked.
GRUB only runs on Boot and doesn't lock any partitions.

---

### Post by mitchtanz on 2006-09-07
Hi

With my PM 8 I'm rebooting after using and getting Error27.

I think I'm properly closing Ubuntu by rebooting.

Now I may have complicated the problem in that I have the XP Partition reading and writing to the Ubuntu Partition and the Ubuntu Partition reading from the XP Partition.

[----Xp-14Gb-][Ubuntu-5.6GB-][Linux swap385Mb]

want to have

[----Xp-10Gb-][Ubuntu-rest9+GB-][Linux swap385Mb]

Thanks

If bushed, I'll re-do the whole Ubuntu install from LiveCD, but have updated etc...my DD.

A victim of initial caution, then excitement, at his Ubuntu install!

Best Wishes
Mitch

---

### Post by msandersen on 2006-09-07
> **Boelcke said:**
> I used the Gparted live CD, which worked great for me.
[http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/")
...
Now, I wanted to shrink the root down to 15gb (only using 4gb right now, having run ubuntu on this machine for about 9 months).  Then, /home could drop down to something like 40gb, and I'd make a separate drive, something like 95gb, which I'm using to store a backup of stuff on another pc (pictures and videos).

Problem is, it seems like you can't move the start of a primary partition, only add to the end.  So I did it in multiple steps.  First, I shrunk my root down to 15gb.

Seems they [released version 0.3 Sept 4-5](http://gparted.sourceforge.net/news.php), is that the version you used? The big news on that release is that it's now able to move partitions. There will be a lag before an Ubuntu package would become available in the Repositories, though. For resizing Root, a LiveCD would be best anyhow. I really don't know for sure, but I'd lean towards QTparted partly because they've been around longer. Since I have Windows as well, I've always used Partition Magic as I know I can trust it.
It's always a good idea to plan your partiton layout beforehand. You might want separate Data partitions like I did with a fairly modest Home partition.
Personally I set my Root to 5Gb, seems to be fine, I've got over a Gig left with all the tools I want. It's not quite so easy to install apps somewhere else in Linux unless you compile, though.
And of course, always back up what you can't afford to loose. Shit happens.

---

### Post by msandersen on 2006-09-07
> **mitchtanz said:**
> Hi

With my PM 8 I'm rebooting after using and getting Error27.

I think I'm properly closing Ubuntu by rebooting.

Now I may have complicated the problem in that I have the XP Partition reading and writing to the Ubuntu Partition and the Ubuntu Partition reading from the XP Partition.
So you're using the [ext2 IFS driver]("http://www.fs-driver.org/") for Windows? Maybe remove the Linux mounts while repartitioning and close Windows Explorer. The mounts are set in the IFS control panel.

---

### Post by mitchtanz on 2006-09-08
Thanks for your help. I had to accept defeat on resizing.

However I love Ubuntu sooo much... I deleted my original install and free-spaced 10GB and have just finished reinstalling fresh one.

Learning and persistence. Maybe a better install this time.

Best Wishes
Mitch

---

### Post by tvor on 2007-04-07
> **Brownedwg89 said:**
> 
you can only make a partition bigger if there is unallocated space right next to it
It that true? Does the unallocated space have to be right next (or under) the partition I would like to added to? [IMG]http://tvor.bloguje.cz//img/mmm.png[/IMG] I would like to add the free space to /hda6 (running live CD GParted 0.3.4.5)

---

### Post by Pisi-Deff on 2007-04-07
> **tvor said:**
>  I would like to add the free space to /hda6 (running live CD GParted 0.3.4.5)
First you have to move your swap and boot partition (between hda6 and the unallocated space) to the end of the unallocated space. Then you can resize hda6 to take the unallocated space too. :)

ps. I love the word 'unallocated'

---

