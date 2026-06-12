---
title: "Windows to Linux, and planning for catastrophic reloading of OS"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by emarkay on 2006-10-17
I have been a Window$ user for over a decade, and like clockwork, about every 9 months (strange...) I have some catastrophic situation  that requires a complete "Reinstall Window$".  Occasionally just a "Setup" overwrite that saves the registry and all the configurations, but mostly a "Format C:" (for assurance of 'virginity') and a reinstall of Window$, and a reinstallation of all my programs.  

Luckily I have multiple volumes so all my data and batch files and other editable configs are stored elsewhere, but it's still a many hour task (and I have a 3 page document that describes procedure in depth so it's just a "point, click, wait, next!" sort of thing.)

I know Linux doesn't have a BSOD nor uses a registry, and [apparently] never crashes or gets corrupted or gags on a poorly written program, but what if it DOES?

***1a. ***  What files and directories should I copy to a "SAFETY" volume that I can just copy back (overwrite) to restore my customizations and configurations if the need arises?

***1b. *** Generally where are my user created data files found, and does Ubuntu place and user created data in any hidden files? 
 
***1c. ***Of course I can just overwrite or copy my backup user created data files  back to their original locations anytime, correct?

***2. ***  Does Ubuntu "overwrite" on reinstallation and save user customizations OR does it reset back to default everything?

***3. ***  What indications are there that something "bad" is happening to Ubuntu; is there a BSOD equivalent?  When will I know things are getting fuzzy?

***4a. ***   There is no (and evidently no need for) a "Norton Utilities"-like set of software and hardware diagnostic tools in Linux, correct?  

***4b. ***There is no need to defrag, clean the registry, scan disks for errors, scan for Ubuntu software errors, make a copy of the FAT, optimise file loading times, make backup copies of the registry, etc... so what sort of ways CAN I look "behind the Gooey" to see how firm, stable and correct things are?

[B]
Thank you![/B]

---

### Post by bulldog on 2006-10-17
Well go out and read some stuff. :D 

[http://learnlinux.tsf.org.za/](http://learnlinux.tsf.org.za/)

[https://help.ubuntu.com/6.06/](https://help.ubuntu.com/6.06/)

[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)

[http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page)

[http://help.ubuntu.com](http://help.ubuntu.com)

To start with but there are plenty more.

---

### Post by pbaehr on 2006-10-17
> **emarkay said:**
> I have been a Window$ user for over a decade, and like clockwork, about every 9 months (strange...) I have some catastrophic situation  that requires a complete "Reinstall Window$".  Occasionally just a "Setup" overwrite that saves the registry and all the configurations, but mostly a "Format C:" (for assurance of 'virginity') and a reinstall of Window$, and a reinstallation of all my programs.  

Luckily I have multiple volumes so all my data and batch files and other editable configs are stored elsewhere, but it's still a many hour task (and I have a 3 page document that describes procedure in depth so it's just a "point, click, wait, next!" sort of thing.)

I know Linux doesn't have a BSOD nor uses a registry, and [apparently] never crashes or gets corrupted or gags on a poorly written program, but what if it DOES?

No operating system is truly invulnerable to crashes. Linux can crash, but it's less frequent than Windows. Rarely does it crash to the point where the entire operating system locks up, but it DOES happen. Usually, though, if you kill the offending process you should be able to resume business as usual.

> ***1a. ***  What files and directories should I copy to a "SAFETY" volume that I can just copy back (overwrite) to restore my customizations and configurations if the need arises?

***1b. *** Generally where are my user created data files found, and does Ubuntu place and user created data in any hidden files?

The answer to both of these is the same. The /home directory contains all of your user files and user configuration details. Additional configuration is found in /etc. I do not back up my /etc directory, though. I find most of the things I've customized reside in /home.
 
> ***1c. ***Of course I can just overwrite or copy my backup user created data files  back to their original locations anytime, correct?
A preferable solution (for me, anyway) is to mount the /home directory as a separate partition. This way, regardless of what happens to the rest of the install (wipe/upgrade/etc...) my user configuration and personal files will be available, unchanged when the system is back.

> ***2. ***  Does Ubuntu "overwrite" on reinstallation and save user customizations OR does it reset back to default everything?

See above. It will overwrite your customizations unless you have mounted /home on it's own partition.

> ***3. ***  What indications are there that something "bad" is happening to Ubuntu; is there a BSOD equivalent?  When will I know things are getting fuzzy?

I guess if things are starting to work in a way you don't expect that would indicate a problem. Maybe someone else can cover this question more fully.

> ***4a. ***   There is no (and evidently no need for) a "Norton Utilities"-like set of software and hardware diagnostic tools in Linux, correct?

There are plenty of diagnostic tools available for Linux. Many are built in. When you develop a need for one, post a new thread and ask what to use.

> ***4b. ***There is no need to defrag, clean the registry, scan disks for errors, scan for Ubuntu software errors, make a copy of the FAT, optimise file loading times, make backup copies of the registry, etc... so what sort of ways CAN I look "behind the Gooey" to see how firm, stable and correct things are?

There is no need to defrag. The file system is much better at handling files than NTFS. There is no registry to scan. Your disk will be scanned automatically every 20th (I think) time it is mounted. As far as going behind the GUI, understand that the GUI is running on top of a command line (like Windows was until Win98) so you can drop to the command line at any time with relative ease.

> [B]
Thank you![/B]

You're welcome. ;)

---

### Post by Klaidas on 2006-10-17
> Linux can crash, but it's less frequent than Windows

Ok, let's put stereotypes aside
You can make Linux crash more, and vice versa.

---

### Post by podunk on 2006-10-17
I backed up my whole system by following the command in post 210 here:
[http://www.ubuntuforums.org/showthread.php?t=35087&page=21](http://www.ubuntuforums.org/showthread.php?t=35087&page=21)

I startedit expecting it take hours - it was done when I came back from supper. :-)

Restores perfectly also - you can extract single files or directoried or restore the whole kit and kabodle.

---

### Post by jordanmthomas on 2006-10-17
1.  Occasionally, you will have a kernel panic and a bunch of mess will be printed on screen.  This can be considered Linux's BSOD.

1a.  In order to make sure everything works afterwards, you'll pretty much need to back up everything.  Configuration files are found in /etc and user configuration files are found in your home directory as hidden files (they start with a . )

1b.  Hidden files start with a .  To see them in a terminal, use 
```
ls -a
``` or in nautilus, press Ctrl-H

1c.  You sure can, and it won't break your system (maybe your user account, but probably not)

2.  Ubuntu rewrites everything on installation if I'm not mistaken.  If you can find a way to make it not format your partition, it will probably leave old files around, but you'd have a mess.

3.  You know stuff is going wrong if you can't mount your hard drive.  Basically, if your Linux actually breaks, it will be an impressive event.  You may get several kernel panics or it will just break.  

4a.  I'm not too familiar with Norton's products, but you won't need much in the way of software diagnostics.  Hardware, on the other hand, you will need to keep an eye on.  Maybe someone else can answer this part better.

4b.  You may actually want to scan your discs for errors.  (nothing's perfect)  You can do this by typing this:
```
sudo touch /forcefsck
sudo reboot

```
As far as looking behind the GUI to see how things are going:  that is the bread and butter of Linux.  Try reading some books or websites on Linux administration.

**beaten like 20 times

---

### Post by Irony on 2006-10-17
One of the great things with Linux is that you can just copy the entire operating system to another volume in a similar manner to copying a folder, e.g.;

[PHP]sudo cp -ax /mnt/hda3_Ubuntu/. /mnt/hda6_Ubuntu/.[/PHP]

This makes for a simple way of backing up a system.

You can also copy sections such as the home directory to a separate volume to route, e.g.;

[PHP]sudo mkfs.ext3 /dev/hda7
sudo mkdir /mnt/hda7_Home
sudo mount /dev/hda7 /hda7_Home
sudo init 1 (wait, wait... until prompt root@ubuntu:~#)
cd /home
cp -ax * /hda7_Home
cd /
mv /home /home_old
mkdir /home
mount /dev/hda7 /home
init 2  (or Ctrl D)[/PHP]

No need for reinstalling to separate partitions.

---

### Post by emarkay on 2006-10-17
Cool, thanks (I am printing this thread now).

I am an avid reader (I do RTFMs) but there is just so much to cover - in a few days, I have like 15 Linux/Ubuntu bookmarks and as many posts linket to review.

I appreciate those links, and will get to them and I appreciate the responses  -like I said these are good questions that need to be answered in the transition that others like me may want to know.  

Maybe when I get confident and have all my apps  tested in Linux, I'll add to the WWW clutter with my own "How I transisioned from Windows to Linux" Web page, too!  :)

BTW, so far, this is my first day without ever booting into Windows!  So far so good!!! 8)

---

### Post by aysiu on 2006-10-17
You can try Ubuntu without installing it--see how you like it.

[Just download a CD image, burn it as a disk image](http://www.psychocats.net/ubuntu/iso), and make sure your BIOS is set to boot from CD before the hard drive.

Ubuntu will boot up fully functional and run from the CD and your computer's RAM. It will not affect your hard drive, but it will give you an idea of how Ubuntu works.

---

### Post by bdb on 2006-10-17
> **emarkay said:**
> BTW, so far, this is my first day without ever booting into Windows!  So far so good!!! 8)

One day I maybe able to say this.  Everyday at work I boot up a windows machine.

---

### Post by bdb on 2006-10-17
> **aysiu said:**
>  but it will give you an idea of how Ubuntu works.

Just remember that it will run slower off the CD than a harddrive install.  This has been my experience.

---

### Post by pbaehr on 2006-10-17
> **Klaidas said:**
> Ok, let's put stereotypes aside
You can make Linux crash more, and vice versa.

You're right, perhaps that was a bit of a fanatical statement. Though, I will add that in my personal experience it rings true. I have only had to do a hard reset on my Ubuntu box once in about a year. Even then, I probably could have connected via SSH and tried to recover. At a certain point it's just not worth the trouble, though. Bragging rights are only worth so much. ;)

---

### Post by emarkay on 2006-10-17
Remember you can't "install" thing like printers and such while running from the CD.

BTW, I spent a few hours a few weeks ago with that same CD and it convimced me that here is promise in Linux.  What a FANTASTIC "Try before you buy" feature! - and it's FREE, too!

Still in Ubuntu - almost 10 hours without going to Windows! :mrgreen:

---

### Post by podunk on 2006-10-17
I booted into windows for the first time in 3 weeks yesterday (I forgot to convert some data to something useable) and my goodness! It was *painfully* slow!

I really like this linux stuff.

---

### Post by bdb on 2006-10-17
> **emarkay said:**
> Remember you can't "install" thing like printers and such while running from the CD.

Really?  I was wondering why I could never get my printer working with the livecd but then with the real-deal it was easy.

---

### Post by seijuro on 2006-10-17
While it is true that no OS is crash proof if you try hard enough you can break any piece of software however I have been running Ubuntu since hoary which is a little over a year I'm guessing and have yet to have any crash what so ever. As opposed to the fresh windows install on the tower which had 2 crashes in the first day. I'm also quite happy that the download for nvidia drivers for linux is roughly about 1/4 the size of the windows download.

---

