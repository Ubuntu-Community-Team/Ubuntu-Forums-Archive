---
title: "Please explain the whole /home partition thing to me .."
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by Eggnog on 2007-06-30
... and why it's a good idea to do it.  I'm not sure I quite understand what this is about.

---

### Post by chamberlain2006 on 2007-06-30
Putting the /home directory on a separate partition is often a good idea, because if your install crashes and you have to reinstall, or you choose to reinstall, you can keep all your data in the same place.  You can just re-enable it.  Much simpler than having to back it up!

---

### Post by greg_g on 2007-06-30
To add more clarification.

When you do have to reinstall for some reason (whether it be a hosed system or you just feel like doing a "spring cleaning") all of your personal settings will stay in tact.  Things like your desktop configuration, you menus, things of that sort.

The way I usually go about it is a 10-20 gig / partition, a swap parition that is 1.5 times the RAM amount, and the rest /home.  To clarify the "10-20": I did a 10 gig / on a system that only had a 80 gig harddrive ("only") and a 20 gig  on a 250 gig harddrive.  The 20 is probably more than I will ever use, but, harddrive space is cheap and it is better to overestimate.

Hope that helps,

greg

---

### Post by Eggnog on 2007-06-30
Okay, that makes sense.  I guess I did it all wrong to begin with.  My Ubuntu install is on my second hard drive (120GB).  I made a big 79 gig /partition for the whole shebang in the beginning, with a 1GB /swap (I have 512MB RAM in this box), and the remaining 40GB in FAT32 for sharing with the Win XP dual boot on another drive.  Can I resize that big partition using the Gparted live CD and then use the extra for a /home?

My next question is this:  when the next Ubuntu upgrade comes out, and I have a separate /home partition, will the upgrade just overwrite the main /home directory residing in the main partition?  Do I have that right?

---

### Post by chamberlain2006 on 2007-06-30
No.  The next version of Ubuntu (Gutsy) will install the newest versions of the packages.  Your personal data in the /home partition will not be changed.

---

### Post by Eggnog on 2007-06-30
All right then.  I think I will resize my /partition down to around 20GB or so and use the rest for the /home partition.  I take it that it's also formatted as ext3.  Do I indicate that it's /home during the partitioning, like I indicated "/" for Unbuntu system to install in the main partition?  Also, how do I tell Ubuntu to point toward the /home partition rather than the /home folder within /partition?

Sorry for the silly questions.  I'm trying to learn all of this and set things up properly to avoid problems down the road.

---

### Post by dfreer on 2007-06-30
Basically, if you are used to windows, think of /home as your My Documents folder. It can store all of your personal files, and also all of the preferences for programs you use. The bookmarks you set in firefox are stored in your home folder, the image you saved to your desktop and then set as your background will be stored in your home folder.
If you reinstall, or even upgrade to the next Ubuntu, **as long as you do not reformat your /home**, all of your personal files will be saved. Futhermore, your background will be exactly the same, when you load firefox you'll notice your bookmarks already loaded and ready to use, etc etc. The only thing you will need to do is reinstall the programs that you installed yourself (reinstalling them won't wipe your preferences, dpkg is *smart* enough not to wipe them).
It isn't a **bad** idea to use just one partition, however it makes things a whole lot eaiser to make the /home partition. 

If you can, instead of resizing, simply move all of the data you want to keep into that 40 GB FAT32 partition. Then do a clean reinstall and specify a seperate partition for /home, and move your data back. Yes, you can resize it if you wish, however methods on doing so depends on the filesystem type you use (my reiserfs filesystem cannot be resized with gparted). That's why I suggest backing up data and doing a clean reinstall (even if you resize, backup the data anyways as it isn't always a smooth process, you could end up with corrupted files if you resize).

Furthermore, although you can ignore this, I tend to make a /localhd partition and delete /home, then system link my /localhd/home/dfreer (which has all of my data) to /home/dfreer. Any other data that I don't want to lose during reinstall, like my custom /etc/X11/xorg.conf and my local game files (doom 3 and unreal tournament 2004 which take up several GB's of data in /usr/local/games/*), I keep in /localhd and use system links. So anytime I reinstall I just need to install a few common programs (codecs, mplayer, vlc, amarok, etc) and I'm running Unreal Tournament 2004 in a matter of minutes!

---

### Post by greg_g on 2007-06-30
> **Eggnog said:**
>  Do I indicate that it's /home during the partitioning, like I indicated "/" for Unbuntu system to install in the main partition?  Also, how do I tell Ubuntu to point toward the /home partition rather than the /home folder within /partition?

Sorry for the silly questions.  I'm trying to learn all of this and set things up properly to avoid problems down the road.

No silly questions.

Yes, when doing an install and partitioning you should set its "mount point" to be /home (there is a drop down list for it), just like you do for "/" (also in the drop down list).  And since you set that to be its mount point it will automatically point there.

Hope that makes sense, I can reword if you want.


greg

---

### Post by dfreer on 2007-06-30
> **Eggnog said:**
> All right then.  I think I will resize my /partition down to around 20GB or so and use the rest for the /home partition.  I take it that it's also formatted as ext3.  Do I indicate that it's /home during the partitioning, like I indicated "/" for Unbuntu system to install in the main partition?  Also, how do I tell Ubuntu to point toward the /home partition rather than the /home folder within /partition?

Sorry for the silly questions.  I'm trying to learn all of this and set things up properly to avoid problems down the road.

Yes, it's the same process as when you specify one partition to be /, you do the same thing with /home.

Think of it this way:
```

Normal one partition install:
/dev/hda1  ->  /
                  etc/
                  home/
                         dfreer/
                         user1/
                  usr/


New two partition install:
/dev/hda1 -> /
                  etc/
**                  home == /dev/hda2**
                                      dfreer/
                                      user1/
                  usr/

/dev/hda2 -> /home
                  dfreer/
                  user1/

```

---

### Post by Eggnog on 2007-06-30
Since I'm not too vested in this install, I think I will take the advice to backup my /home directory to the FAT32 partition and do a clean reinstall.  If I understand this correctly, here is what I think I should do:

1.  Backup /home data to the FAT32 partition.
2.  Make a new /partition around 20GB, /swap around 1GB or so, and /home with the remainder (around 59GB or so).
3.  Reinstall Ubuntu.
4.  Copy /home data from FAT32 to /home partition.

If this is correct, I have a few more quick questions then I am off to the races.

1.  After I wipe out my Ubuntu install, should I do a FIXMBR to put my boot record back to straight up Win XP before I reinstall Ubuntu?  I'm not sure where GRUB resides or what might happen if I damage or destroy it.

2.  When it comes time to upgrade to Gutsy, will my /home partition be protected automatically or will I have to do or not do something during the upgrade to make sure it's not overwritten?

3.  Is 20GB normally enough for the /partition?  I'm not sure how to judge that.

And thanks for all the help.  This /home partition makes perfect sense to do.

---

### Post by greg_g on 2007-06-30
Yep, you have the right idea, your process looks good.

And about your questions:
I can't help with #1, sorry.

#2: when the upgrade comes your /home partition shouldn't be effected.  The most that will happen is an individual program that is updated might update some config files in your user folder.  But that is ok and normal.  And, if you choose to Reinstall for somereason, you just tell it to format the / partition and leave /home alone.

#3: 20 gigs should be *plenty*  I mean, I have it at 20 because I have some room to spare.  I am only using about 4 gigs of it right now, and I probably won't ever go above 10, and that is if I try.  The / partition will only house your installed applications.  And some other stuff but that is a good way to think about it.  It is like your "Program FIles" and "Windows" directory all in one from WIndows.  And /home is like My Documents and, forgive the reference, a personal "registry" *shudders*

Get a cup of tea, install, and we'll see ya on the flip side.

Welcome aboard.

greg

---

### Post by dfreer on 2007-06-30
One thing to worry about. If you simply copy your current /home to a FAT32 partition, when you go to copy it back you will find out that your permissions may have not been copied over correctly, not just the ownership of the files but the actual permissions themselves (read, write, execute). Also, there are TONS of hidden folders in your home folder, most of which deal with your user preferences. They can be found in nautilus by hitting <Ctrl>+<h>, or by terminal with *ls -al*

(1). Don't worry about restoring the MBR of XP, unless for some reason you need to get to XP **after** you wipe ubuntu. The ubuntu reinstall should detect XP regardless of whether the MBR is broken or not, if it doesn't it is a relatively simple matter to add a few lines to boot XP again.

(2). Well, it depends on how you upgrade as well. Simply by changing your apt sources list, you will not need to worry about it wiping your /home, as all it does to upgrade between versions of ubuntu is install newer programs, and (most likely) add a new kernel. 
As for upgrading by using a Gutsy Live CD to reinstall (my preferred method), as long as you make sure it doesn't wipe your /home partition by reformating, and you tell it to mount it at /home, there won't be any problems.
If you don't mount it at /home by accident (for example, feisty will automatically mount any partition at /media/sda3 for example), it will create a default /home/$USER partition. You can safely delete that /home and either (a.) correctly mount your partition at /home or (b.) mount it somewhere else and systemlink the home folders.

(3). Agreed, 20 GB's is plenty. I tend to use anywhere from 3-5 GB's, even after installing a load of programs (most linux programs are pretty small). I've seen some / partitions get bigger, mainly when installing games (doom 3 and unreal tournament 2004 install in /usr/local/games/). You can always find out what is taking up all of the space, and move it onto the partition that has plenty of space, and system link it back to it's original location.
Also, /tmp sometimes gets full (I stream movies off the internet, which means mplayer caches them in /tmp while playing), with appropriate care you could even system link that to another partition, although you should know what you are doing if you do that.

Ok, that probably is a little confusing, so here's an example:
Greg has two partitions besides his swap, one located at /dev/hda1 called / and it is 5 GB's. another at /dev/hda2 called /localhd with 65 GB's. After installing his favorite game "Duck Hunter's Revenge 2" in /usr/local/games/, he finds he is out of disk space on /. He copies /usr/local/games/ to /localhd/games, deletes /usr/local/games, and then runs the following command:
```
sudo ln -s /localhd/games /usr/local/games
```
His game works great from that point on, and it "appears" like it is located at /usr/local/games although it is really at /localhd/games/

---

### Post by jc508 on 2007-06-30
I am trying this too seeing the box is at ground zero...
A couple of supplementary questions please.

1. How does the link think get setup? (ie home == /dev/hda2) or is it automatic because /home is some kind of magic?
2. My default single partion is listed as /media/hda  or similar not /  are these equivalent ?

---

### Post by Eggnog on 2007-06-30
Okay, I'm back and everything has gone well so far.  I have a 20GB / partition, a 1.5GB /swap partition, and around a 56-58GB /home partition.  I went ahead and repaired the MBR just to be safe even though I probably didn't need to.

I'm mindful of the warning about copying files directly from /home to the FAT32.  I noticed right away that it wouldn't copy everything over so I'm not going to rely on it.  I went ahead and exported my Firefox bookmarks before the reinstall and did a few other things but I think I'm going to just pretty much start from scratch after that.

I'm kind of glad to be starting almost from scratch, with the exception of the imported bookmarks and what not.  It won't take as long to get things back to normal again because I have a bit better idea of what I'm doing now.  This will probably be a lot cleaner installation that the previous one anyway.  Earlier I had kubuntu-desktop installed as well but wished I hadn't done that after a short while; I tried it and then decided not to use it.  I'll just use the various K apps I prefer instead.

Anyway, thanks to everyone for their help.  Now I'm not so worried if my Ubuntu breaks or fretting upgrade time.  I can reinstall without fear of losing my /home.  Thanks again.

---

### Post by dfreer on 2007-07-01
> **jc508 said:**
> I am trying this too seeing the box is at ground zero...
A couple of supplementary questions please.

1. How does the link think get setup? (ie home == /dev/hda2) or is it automatic because /home is some kind of magic?
2. My default single partion is listed as /media/hda  or similar not /  are these equivalent ?

(1). Well, think of windows, if you are familiar with it. Have you ever mounted a network share to a drive letter, like Z:/? Or plugged in a USB drive that gets mounted to E:\ or some letter? You can do the same with Hard drive partitions, and they will have their own drive letters. Not only that, but using XP disk management tool you can mount a partition as a folder instead, like C:\Second Hard Drive\
When you navigate to C:\Second Hard Drive, even though it looks like it is part of Drive C it is a seperate partition with it's own drive space.

Ok, well mounting any sort of drive in linux is similiar to that last XP example. When you tell the installer to mount the second partition at /home, it lets you access the second partition through a folder on the / drive, namely the folder called /home. 

If you want a simpler answer, Tux the Penguin is actually a WIZARD, and he casts his magic on your PC so you can access your files the way he wants you to. :popcorn:

(2). I'd have to see the output of 
```
sudo fdisk -l
```
because I don't think you can not have a / partition. You may have two partitions, or something else funky going on. In general, ubuntu likes to mount extra partitions as /media/hda1 or /media/sdb3, depending on several different factors (look into the linux partition naming convention if you want to know more about that), that's just the way the installer is set up.

EDIT: glad things are working out eggnog!

---

### Post by silverglade00 on 2007-07-01
Eggnog, If you want to keep your Firefox extensions, bookmarks, etc. next time, just copy the .mozilla folder in your home folder to another disk. After you reinstall and copy the .mozilla folder back to your home, you will find everything restored to Firefox. If it crashed right before this, it will even come back and ask if you want to restore the session! Cool stuff. You might also want to check out the Google Browser Sync extension on the Google website. It stores your cookies, history and bookmarks on their server (encryption is available) and you can load it on any computer with the extension and your password.

---

### Post by Eggnog on 2007-07-01
Thanks for the info, silverglade.  I'll definitely be looking into the Google extension.  There's been a lot of good info in this thread.  I hope others find it useful.  Because a /home partition makes so much sense, and seems to be a far better way of doing things, it ought to be part of the default guided install.  A user would determine the size of the / partition he or she wanted and the install would take care of the /swap like usual and use the rest for /home.  Having a separate /home partition just makes so much sense.

---

### Post by dfreer on 2007-07-01
> **Eggnog said:**
> Thanks for the info, silverglade.  I'll definitely be looking into the Google extension.  There's been a lot of good info in this thread.  I hope others find it useful.  Because a /home partition makes so much sense, and seems to be a far better way of doing things, it ought to be part of the default guided install.  A user would determine the size of the / partition he or she wanted and the install would take care of the /swap like usual and use the rest for /home.  Having a separate /home partition just makes so much sense.

This has been brought up before, I believe the general reasoning against this would be new users typically do not know what size the / partition should be, and if it were to get full they will most likely not know how to fix it. It is a good idea in **any** OS, for example in windows it is a relatively simple matter to map the "My Documents" folder to another partition, however most major PC manufacturer's opt for the "1 partition for the entire OS" scheme.

---

### Post by Eggnog on 2007-07-01
> **dfreer said:**
> This has been brought up before, I believe the general reasoning against this would be new users typically do not know what size the / partition should be, and if it were to get full they will most likely not know how to fix it. It is a good idea in **any** OS, for example in windows it is a relatively simple matter to map the "My Documents" folder to another partition, however most major PC manufacturer's opt for the "1 partition for the entire OS" scheme.

If not as part of the guided install, then perhaps as one of the options?  Not quite a guided install, but not as severe as a complete manual install, which would intimidate some new users.  It was just a thought.  :D

---

### Post by az on 2007-07-01
> **Eggnog said:**
> If not as part of the guided install, then perhaps as one of the options?  Not quite a guided install, but not as severe as a complete manual install, which would intimidate some new users.  It was just a thought.  :D

A seperate home partitoin as part of the regular install?  This has been discussed at length on the dev mailing lists.

Basically, there are a few reason to not do it.

1.  There is no guarantee that your configs from one version of an app will work with another version of the same app.  So using your home folder configs on different systems is not recommended.
2.  It complicates the installation process.  Linux competes with windows.  Windows is 99.99 percent of the time pre-installed.  Linux is not.  It is a specific goal to keep the installer to the smallest number of clicks possible,
3.  You don't need to have a seperate home on a desktop system.  It is a lot simpler to do backups the old-fashion way.  With hardware costs plummeting, it usually makes more sense to buy a new, bigger hard drive than to make your drives smaller.
4.  Most of the time, you will need to go back and change your partition sizes anyway.  The more you partition your drive for your linux system (Say, on a server where you have seperate /var /boot ...etc.), the greater the risk that you get it wrong and that you run out of space.  If you follow the default behavious - all on one partition - the whole drive is shared, so you avoid that problem.

So, there are not enough reasons to do it, and a lot of reasons to not do it.

---

