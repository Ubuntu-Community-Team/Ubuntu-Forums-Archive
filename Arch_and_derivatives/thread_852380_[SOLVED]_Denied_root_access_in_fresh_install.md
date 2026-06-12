---
title: "[SOLVED] Denied root access in fresh install"
date: 2008-07-07
forum: Arch and derivatives
---

### Post by kvk on 2008-07-07
I'm new to Arch and that level of detail regarding the OS architecture. I've got a fresh BASE install, but when I go to configure the network and do some troubleshooting prior to using PACMAN, I am denied root access to the files (etc/rc.conf, etc.), even though I am logged in as root. Did I miss a step somewhere during installation?

THank you!

---

### Post by fwojciec on 2008-07-07
"etc/rc.conf" or "/etc/rc.conf"?  Maybe you're using a wrong path/filename?

---

### Post by kvk on 2008-07-07
Sorry- that was just my typo here; my bad. 

The filename and paths are correct, and I get a "permission denied" response, regardless of which specific file I try to access.

---

### Post by fwojciec on 2008-07-07
Another idea -- maybe the root device is being mounted as read-only?  See if you see any messages to that effect during boot...

---

### Post by Rumor on 2008-07-07
Yeah, what fwo said :)

The only thing I can think of that would cause that issue is not rebooting between completing your base install and trying to edit those files.

---

### Post by kvk on 2008-07-07
Well, I checked, or tried to check, during boot, but I can't read that fast!! :-p

I might try to install everything all over again and see if it still happens. It accepts my password to log in initially after boot as root, but doesn't allow me root access to those files afterwards.

I'll see what happens with installing again. Thanks!

---

### Post by kvk on 2008-07-07
So here's a really silly question- I'm doing a fresh install, and under the install screen where the package categories are selected (base, devel, lib, support), no categories are selected, and I'll be darned if I can figure out how to select anything!! None of the key combinations I've tried will mark the empty bracket spaces [ ] by each category.

---

### Post by wolfvorkian1 on 2008-07-08
> **kvk said:**
> So here's a really silly question- I'm doing a fresh install, and under the install screen where the package categories are selected (base, devel, lib, support), no categories are selected, and I'll be darned if I can figure out how to select anything!! None of the key combinations I've tried will mark the empty bracket spaces [ ] by each category.

Use the space key, hit it and move on. For instance when it ask you later to choose a mirror for pacman to download from, move to the site you want, hit the big space key at the bottom of your keyboard and then proceed. It won't leave a visible mark in the box but later if you take a look later at the file pacman uses to determine what site it goes to ( I forget the name of the file), you'll see the site you marked with your space key listed even though there is no indication that you marked it during the installation.

The ArchWiki  Beginners  Guide is really  an unusual  document.  It is actually written to get you up and going and done in layman's lingo. An excellent piece of information.

---

### Post by MisfitI38 on 2008-07-08
> **wolfvorkian1 said:**
> The ArchWiki  Beginners  Guide is really  an unusual  document.  It is actually written to get you up and going and done in layman's lingo. An excellent piece of information.

Thank you. :D

---

### Post by kvk on 2008-07-08
Thanks! I got them loaded, although I had already searched the Arch beginners wiki top to bottom and couldn't find reference to the space bar- I assume it was so basic as to be assumed known. 

But I am still being denied root access, which is odd. I think I may have missed something in the configuration files that's making this happen; time to wade through it again, a bit more slowly. :)

---

### Post by fwojciec on 2008-07-08
The partition would mount as read-only automatically if there is some sort of a problem detected during disk check -- so that's one thing to look out for.  Another thing -- what filesystem are you using for root?

---

### Post by MisfitI38 on 2008-07-08
> **kvk said:**
> Thanks! I got them loaded, although I had already searched the Arch beginners wiki top to bottom and couldn't find reference to the space bar- I assume it was so basic as to be assumed known. 
[http://wiki.archlinux.org/index.php/Beginners_Guide#Select_Packages](http://wiki.archlinux.org/index.php/Beginners_Guide#Select_Packages)

3rd sentence in. ;)

---

### Post by kvk on 2008-07-08
DOH!! I am SUCH a dork! :-p

:popcorn:

As for the file system, I set the root partition to JFS.

---

### Post by fwojciec on 2008-07-08
> **kvk said:**
> As for the file system, I set the root partition to JFS.

Misfit can probably tell you more about JFS, or correct me if what I'm saying is inaccurate, but from what I've read this filesystem can behave in erratic ways if it is used as a single system partition (i.e. on a system without a separate, dedicated /boot partition that's not JFS).

---

### Post by kvk on 2008-07-08
Hmmm...well, you definitely know more than I do. From what I can tell from the set-up, I created three partitions: root, swap, and home, all of which are JFS. But when the GRUB boot loader was installed, it appeared as though the installer placed it on a separate partition: sda0. When I initially tried to install GRUB on the sda1 root partition, I got an error message that I remember seeing elsewhere on this Arch forum, so I went back and allowed the installer to place it where it wanted, which was the sda0. But I never formally defined a file system for that partition.

---

### Post by fwojciec on 2008-07-08
> **kvk said:**
> Hmmm...well, you definitely know more than I do. From what I can tell from the set-up, I created three partitions: root, swap, and home, all of which are JFS. But when the GRUB boot loader was installed, it appeared as though the installer placed it on a separate partition: sda0. When I initially tried to install GRUB on the sda1 root partition, I got an error message that I remember seeing elsewhere on this Arch forum, so I went back and allowed the installer to place it where it wanted, which was the sda0. But I never formally defined a file system for that partition.

This is from the Arch wiki article about JFS:

> Using JFS on a boot partition with the Grub boot loader can work, but can lead to problems. In particular, using JFS on a boot partition has a habit of corrupting the master boot recorder on a Grub update. This happens quite frequently and requires a full repartitioning+formating of the drive with the boot partition in order to remedy the situation.

A personal recommendation is to create a boot partition of 50-100MB with an ext2 file system (which works perfectly with grub and is extremely fast) and format the root partition with JFS. As the boot partition is rarely written to, it makes little sense to put a journaled file system on this.

It is unclear whether or not the same issue is present with using LILO and a JFS boot partition. 

More here: [http://wiki.archlinux.org/index.php/JFS]("http://wiki.archlinux.org/index.php/JFS")

If you still can't get it to work and you're thinking of installing again I'd suggest something like this as far as the partition layout is concerned:

1. /dev/sda1 -- /boot using ext2 (I usually do about 500MB, just to be on the safe side, in case I want to have multiple kernels installed in parallel.
2. /dev/sda2 -- swap (should be created as swap not JFS)
3. /dev/sda3 -- / using JFS (10-12GB should be plenty)
4. /dev/sda4 -- /home using JFS as well (the rest of the disk)

Grub should be installed to /dev/sda (the whole disk, not a particular partition on it).

I just noticed that one of the examples on that wiki page has the "rw" (read-write) argument specifically included in the mount options in /etc/fstab -- perhaps you need to add something like this to the fstab on your system?

---

### Post by kvk on 2008-07-08
Excellent!! Thanks much! I'll go back and walk through the whole thing more slowly. What is the primary difference between a home partition and a root partition if there is only one user on the system overall? Is it simply that the root contains the system files, and home contains the specific application files created by the user?

I like the ninja bears, BTW. There are several new sets of cubs running around the river this year- they look a lot like them!!

:popcorn:

---

### Post by fwojciec on 2008-07-08
I'm so jealous that you get to live in a place where you can see bear cubs running around by the river like that...  I'd love to live in Alaska (or a similar place) at some stage in my life.

As for your question -- having separate root and home partitions gives you more flexibility, somewhat.  You can have different filesystems on each, it is perhaps easier to backup data, migrate a system to new/different hardware, and if you want to install a different distro you can just change what's on the root partition and keep the /home, where all your settings and private files are stored, intact.  If you're the only person who uses the computer and if you're planning on using a single filesystem on all partitions then it probably doesn't make a whole lot of difference if they are separate or not.

---

### Post by MisfitI38 on 2008-07-09
> **fwojciec said:**
> Misfit can probably tell you more about JFS, or correct me if what I'm saying is inaccurate, but from what I've read this filesystem can behave in erratic ways if it is used as a single system partition (i.e. on a system without a separate, dedicated /boot partition that's not JFS).

I am flattered by your faith in my knowledge, fwojciec. ;)
Actually, I clicked on the link you cite, and in the first paragraph, I read an error which I corrected.
It stated that the current linux version of JFS was ported from OS/2, which is correct, but it also stated that the OS/2 version was ported from AIX, which is not really correct.

As for using JFS on /boot, I have read that it had issues in the past, but the paper trail on this seems to disappear. I personally have been using JFS for every partition for a long time, and never had an issue on any machine.

I am going to go over the rest of the wiki article to see if I can verify or disqualify the validity of its content. If i found an error in the first few sentences, chances are that the rest of it may contain some old information which may be out of date. :)

---

### Post by kvk on 2008-07-09
You folks rock. :-)

I did the reinstall, and followed the Beginner's Guide from the Arch wiki. Things went much better- I created three partitions, with the '/' and 'home' partitions using ext3, and modified the .conf files as per the instructions. Post-install boot-up was fine, with a number of difference in the start-up script indicating things were much healthier, including the presence of the Arch logo which had been missing before.

Efforts to set up the wireless connection were not productive, but all results returned were in keeping with the wiki data- I just need to work on it a bit more.

HOWEVER, if I log in as 'root', enter the root password such that the log-in prompt changes to [root@arctos~]#, and then enter /etc/rc.conf as a test, the return is still 'Permission denied'.

Dang!

Wait a sec...I just entered "halt" to shut things down, and as the shut-down scripts were flying by, I saw a line that said the root partition READ ONLY was dismounting. But during boot-up, everything came up clean when mounting. Dang^2! :)

---

### Post by fwojciec on 2008-07-09
Try booting with the install disk and chek the root partition with fsck.

Can you edit files on your home partition?

---

### Post by kvk on 2008-07-09
Results from fsck -arctos /dev/sda1: [root directory]

/dev/sda1: 31448/1098880 files (0.1% non-contiguous), 203925/2196880 blocks

Results from fsck -arctos /dev/sda3: [home directory]

/dev/sda3: 12/1219200 files (8.3% non-contiguous), 76342/2437863 blocks.


As for modifying the /home files, I haven't gotten that far yet- I wouldn't even know how to get into them!

---

### Post by fwojciec on 2008-07-10
Sorry, I'm out of ideas :(

---

### Post by MisfitI38 on 2008-07-10
> **fwojciec said:**
> Another idea -- maybe the root device is being mounted as read-only?  See if you see any messages to that effect during boot...

Maybe try ```
mount -no remount,rw /
``` or edit /boot/grub/menu.lst and remove the ro from the kernel just to see if it helps :confused: ?

---

### Post by kvk on 2008-07-11
Thanks for all the suggestions- I really appreciate them.

Misfit, I tried running the 'edit' command and it returned 'no such file or directory'. 

I tried the following with the attendant results:

hdparm /dev/sda1

IO support = 0
readonly = 0 (off)
readahead = 256 (on)
geometry = 2432/255/63, sectors = 17575047, start =63

So I know the root partition isn't set as read-only. I'll keep digging around and see what I can find, and if I get it fixed, I'll post it.

Thanks so much!

---

### Post by Barrucadu on 2008-07-11
Are you just typing the file path? Unless the file is executable you'll get a permission error.

---

### Post by Rumor on 2008-07-11
When you are logged in as root, what is the error you get when you type ```
vi /etc/rc.conf
```

---

### Post by kvk on 2008-07-11
DOH!!  #-o:oops:

You are perfectly correct, both Barrucado and Rumor- I was not providing a text editor command, just the path name. I was able to open (as a test) both /etc/rc.conf and /etc/fstab and return to root with no problem.

I did notice on boot the line:

kinit: mount root (ext3 filesystem) readonly

but perhaps that's a general procedure that's ignored when logged on as root.

And thanks so much to everyone else who was spending their time helping me chase ghosts in the...well, not the machine, but in my own mind. :-P

---

### Post by MisfitI38 on 2008-07-11
> **kvk said:**
> DOH!!  #-o:oops:
I was not providing a text editor command, just the path name. 
Now that's just downright silly! We both deserve a good smack to the head. I was totally misunderstanding the nature of your problem.

---

### Post by kvk on 2008-07-11
We'll see what other issues I run into in this experiment! I'm playing with an old laptop I got from State surplus, with the goal of loading Arch, Emacs, Bluefish, a browser, Mutt, a text editor or two, and some science/math applications and encryption stuff, just for the ugly fun of it. Although I guess Emacs alone could pretty much do all of that!

Thanks again!

---

