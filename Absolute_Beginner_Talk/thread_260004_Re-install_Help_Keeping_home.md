---
title: "Re-install Help Keeping /home"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by morequarky on 2006-09-18
I need to re-install my Ubuntu box.

Two partitions it seems have been wiped.  /var /usr /home are still there.

How do I re-install and keep those three partitions a part of the new install?

Thanks.

(this is not a thread posted twice in different forums.  My original question was about fixing a filesystem/master boot record issue.  Now re-installing seems to be the only solution given the latest information and I am asking about just that, installing.)

---

### Post by kidders on 2006-09-18
Hi there,

Keeping your original /home is trivial (ie just don't format it!), however using an old /usr can be a little tricky ... and keeping /var is not for the faint-hearted.

If you don't fully understand exactly what the various components of a /var directory do, then you *definitely* shouldn't attempt to hold on to it.

Since this is the "Absolute beginner talk" section, I'd suggest holding on to /home, but consigning the rest to the dustbin :-(

---

### Post by GrootBrak on 2006-09-18
I have similair issues in my own thread. I really need to get a lot of data back even in the root folders. There is a lot of previously installed programs and sweat to ignore my files in /var, /usr as well. 

Would appreciate further help. Else what was the point of setting those as separate mount points?

---

### Post by kidders on 2006-09-18
There are **lots** of reasons to use more than one partition for a Linux install, but blindly copying thousands of files between two versions of an OS is not a terribly good idea. Of course, if you find yourself needing to do that, it's highly likely you don't need to reinstall the thing to begin with!

I can see where you're coming from though, in that your MySQL database might be living in /var, for example ... and you'd **_hate_** to lose that, right?! Most of the stuff in /var is not intended to be useful to anything other than one copy of one operating system on one computer though, so duplicating it can have unpredictable results. If, like I mentioned, you're looking to save a MySQL database from annihilation, mysqldump-ing it is by far the safest solution.

If, during install, you organise your mountpoints specifically with a view to being able to rescue as much as possible in the event of a catastrophe, it can be pretty doable though :-)

May I ask why you both need to start again from scratch? Perhaps there is another way.

---

### Post by morequarky on 2006-09-18
"May I ask why you both need to start again from scratch? Perhaps there is another way."

Sure.  I have an XP64 partition.  My wife installed XP Home inside the XP64 partition in the process deleting the contents of two partitions and wiping my Master Boot Record.  I put the master boot record back because I still have '/'.  But when I try to load 'ubuntu' it crashes to a useless prompt AFTER IT LOADS THE KERNEL when it tries to find the files systems.  I have '/' '/home' '/var' and '/usr' along with two more partitions I don't remember what they were but they currently contain "lost+found" files.  Whatever the case the '/' partition is not loading the filesystems correctly. It is so messed up that Gparted on a live CD of ubuntu claims the whole drive is empty and free to use.  

SO... I reinstall trying to keep as much as I can

OR

I play with some other files to get ubuntu back up and running.

thanks for the help

---

### Post by mejy on 2006-09-18
If you try to reinstall while keeping these partitions, things can get very messy.  /usr/ should not be blindly coppied - for one thing, apt will become completely messed up with files and programs partly installed that it has no record of.  /var/ is also - as previously mentioned - install specific.  Perhaps you could list information about data you need to keep.

---

### Post by greyash99 on 2006-09-18
You could burn the contents of your /home folder to a cd/dvd

---

### Post by morequarky on 2006-09-18
When I boot to a live CD gparted doesn't see anything on the drive at all.  Though it boots windows just fine and it boots ubuntu's kernel up to a point without a hitch.  It is possible to fix a partition table somewhere and fix it that way.

I don't know.

I need a few pictures off /home/public-html
Most of the other stuff is locked up in /home/<username> so a liveCD can't access it.

I had a really hard time getting apache to work and I don't want to have to go through that for the third time.

I never got ftp working at all.

I can't burn anything off because as it is now I can't access anything without the liveCD.  I guess I would have to find some kind of ext3 partition reader for Windows, but I don't have any burning software on windows.

very frustrating.

---

### Post by kidders on 2006-09-18
> Most of the other stuff is locked up in /home/<username> so a liveCD can't access it.

Why can't you access your /home? Are you using some sort of odd filesystem?

One possible suggestion for rescuing useful data might be to copy /etc to a USB stick or your camera or something. It will help you preserve complicated app configurations that, like you mentioned, can be a real pain to get right.

---

### Post by morequarky on 2006-09-18
/home/<username>/doc isn't open to the public like "public-html" is.  

/etc might be one of the partitions that got wipped.

grrr

---

### Post by GrootBrak on 2006-09-19
My case is bit different, because I was trying to move to a bigger hard drive. I made the mistake of using Qparted, and it messed up something so that at reboot,I was unable to. The plan is to cut away my two old HDD's since my PC have only one IDE port, but four SATA's.

Anyway, I have four users on my PC, and each had specific programs and access rights. It took me long to figure that out. 

Also under the /home/username there is a pile of hidden files, including .wine, .gimp and so on. I need those back (and working) as well, and at this stage I can get only my saved documents back.

Then of course, my email, Firefox etc. had specific set-ups that took me hours to get it right. Where can I get that?

I did manage to copy simple user settings (bluetooth, GPRS dail-up, sources.list,snapscan.conf) from the old etc, and its working! 

Coming back to my programs.... That is such a sorry mess. Do I need to re-install everything again? Then of course I need to add it to my and the other users menu's as well... Is'nt that what the back-up was for?

The of course the big question. After a couple of months I tend to collect quite a few apps. and settings. So I need a bigger hard disk. Is there a method of copying one disk to the other, swop disks and carry one where you left?

Apologies for the loooooong winded reply!

And

---

### Post by kidders on 2006-09-19
Hi guys,

Morequarky and GrootBrak seem to be having similar trouble with /home. There is no reason why you can't retain a /home partition for use on a reinstalled Ubuntu ... just don't let the installer format it! If you're only interested in parts of /home, you can copy the bits you want out of there as root, from a LiveCD version without, any difficulties.

There are several things to be aware of though. First, let's assume you both have seprate /home partitions and have already reinstalled Ubuntu. With luck, this won't be so generalised it won't help either of you!!

First, /home is a good example of something you *can* blindly copy from one Linux to the next, without having to worry too much about weird side-effects. One big issue is file ownership though. In filesystems such as ext3, the owner of a file is stored on disk as a number, which is mapped to a name by the operating system, for your convenience. On a reinstalled system (or a LiveCD version), those maps won't exist any more, so your files will appear to be owned by mysterious people called "1002", or "1003", or some such. Additionally, other Linuxes (ie things other than your originally installed Ubuntu) may have different user maps installed, so files in /home may suddenly find themselves owned by new people that just happen to map to the correct UID numbers. If (when) this happens to you, don't worry ... it's perfectly alright :-)

If you want to, you can deliberately try to create a new user set that maps correctly to the original UIDs on your old system. It's easy to do. If you make a mess, or simply can't be bothered, step two would simply be to **chown -R** each user's home directory, rewriting the ownership maps, so they look right. On /home, this is easy to do, because the "right" owner of each directory is obvious from its name.

Now, as most people know, all user-specific application settings are stored in **/home/<username>/.something** As you slowly re-install all the apps you had on your original system, these settings will begin to be used, as long as your users don't delete them. The fact that they may be hidden makes no difference to anything, really ... all that's important is that, by that stage, your users' /home directories are actually owned by them, according to your new UID maps.

Should you choose to copy /home directories around a bit, rather than leaving the whole partition intact, it is very important to do a "permissions preserving" copy. Ordinarily, when you copy something, the **cp** command automatically guesses the permissions you are most likely to want the destination copies to have. When archiving data belonging to other people, you won't want this to happen. Using **cp -dpR** takes care of this.

**At this point, let _me_ apologise for the long-winded reply!!**

The more "usual" thing to do when re-installing your OS is to install all your applications again from scratch. Most of the time, the only things that make one installation of, say, apache, different than another are:

[LIST=1]
[*]The global application settings in /etc
[*]The user-specific application settings in /home        [in this case, personal www trees]
[/LIST]

So, provided you can preserve /etc and /home, reinstalling your apps from scratch is (a) faster ... after all, using Ubuntu's package manager is a snap, and (b) safer ... because you can be sure things such as elaborate symlink relationships won't get messed up.

I hope some of this helps you guys out ... I should probably stop typing now!!

---

### Post by kidders on 2006-09-19
> **GrootBrak said:**
> So I need a bigger hard disk. Is there a method of copying one disk to the other, swap disks and carry one where you left?

Yep. One possibility is to use the **dd** (disk dump) utility, which can copy entire partition/filesystem structures around, byte for byte. Of course, if the whole point in making the move is so that you can have bigger partitions, this isn't exactly ... well ... useful!

Here's an alternative:

[LIST=1]
[*]Shut down your X environment and all running apps & services, to reduce the probability of something being modified while you duplicate your filesystem structure.
[*]Check that **lsof** is a _very_ small list. Open files may get locked or modified during the copy.
[*]Copy your filesystem structure in small, manageable chunks, rather than all at once. Start with, say, **cp -dpR /etc /mnt/newdisk/etc**
[*]Tweak your new /etc/fstab to have the right things mounted in the right places.
[*]Install your bootloader (grub maybe?) on the new disk. Be careful with device numbering (see next step).
[*]Shut down and physically swap your hard disks around.
[*]Boot as normal into your new, bigger Ubuntu.
[/LIST]

If you're careful, and don't do anything hasty without thinking it through, this should work perfectly every time ... I think!!

---

### Post by GrootBrak on 2006-09-20
Thanx for that long winded reply, kidders. At least now it makes sense to me! The only problem I need is to find out what was the original user ID's agianst the username. Any idea how I can find those? If that is the case, then I'm halfway there.

Just a point to note why I want a bigger hard disk...
As mentioned, I made seperate partitions for a few things, basically a partition for each drop down in the installer. After a few months my /home and /usr was full. But /(root) /var was using less than a Gig! I previously used a third party app, Acronis to resize.

Getting back to my programs. I don't mind reinstalling them if I can get my original settings back as linked to my /home settings! But I do mind downloading them again. To gaurd agains that I kept every single file I downloaded in my apt/cache. Now with Synaptic I use that option "Install downloaded programs" (can't recall the exact name now..) It shows me a huge list of files (and a few broken ones) that will be installed. But after installation completes, I still don't see me programs. Some programs did appear, but they are not working at all. Among them is Gimp and Thunderbird. Most is completely missing.

Do you know how I can re-install my old programs in the cache without downloading the lot all over again?

---

### Post by kidders on 2006-09-20
> I need is to find out what was the original user ID's agianst the username. Any idea how I can find those?

It's not really worth bothering unless you more than a handful of users. Your original **/etc/passwd** will tell you what you need to know though. Each line goes a bit like this:

```

username:password:uid:primaryGroup:gecos:home:shell

```

> I made seperate partitions for a few things, basically a partition for each drop down in the installer.

Oh gosh... did you really *need* to do that?! If I were you, I'd undo some of that partitioning!! Holding onto your cached downloads is a smart idea though. By the way, are you sure gimp, etc. are actually missing? (What happens if your try **whereis gimp** or **ls -ld /usr/share/gimp** ?)

---

### Post by GrootBrak on 2006-09-22
Just as information, I thrashed the new install completely. Bought a SATA drive, a block of RAM and reinstalled first windows, and then Ubuntu. The only extra mount point I have is /home, and my old partitions sitting on my old IDE drive.

Now, before I stuff up badly, again... I made sure when I added the other used to set them to the original UID as you said. Now, should I copy all the /home/<user> to the new home first and then re-install my apps, or should it first be re-install the apps and then copy the old /home/<user> to the new /home?

Then of course the problem with my cache. Since I do have a cache, and prefer to use it in stead of re-downloading the whole shebang, how can I re-install my cache? 
sudo apt-get install <something> won't work and dpkg -i <something> won't add the dependencies. To add 200+ packages one by one is no fun either.

---

### Post by kidders on 2006-09-22
Hi again,

The order doesn't matter ... application installers don't generally touch peoples' home directories.

---

### Post by GrootBrak on 2006-09-24
Thanx man! Things are looking better. The only hassle I now have is to add my cache to Synaptic.
I've done the following in my /cache/archives directory:
sudo dpkg-scanpackages ./dev/null|gzip-9c>Packages.gz
Then nothing seems to happen. I cannot see the packages in Synaptic, and neither was it added to my apps. How can I install those packages? (Accept for dpkg -i...)
Regards

---

### Post by kidders on 2006-09-24
Yeah, I saw a line like that in another post :-) Unfortunately, my Linux experience doesn't come from Ubuntu (poor, poor me, eh?!) and this is something I haven't needed to try yet, so I know everything you do, I'm afraid!

Perhaps one of the other posters can lend a hand?

Anyhow, hopefully now that you've done all that donkey-work once, it'll be *waaaaay* faster for you the next time around.

---

