---
title: "[SOLVED] /home partition setup for save future upgrades"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by perixx on 2007-10-14
Howdy!


I've read, that it is a clever way to set up a separate /home partition in order to have  no problems whatsoever with major future OS upgrades, as all personal data and settings remain persistent...

So I'm curious how to:

1) do this on a fresh install 

2) if it's possible to move the existing home directory to a newly set up partition after installing Xubuntu


Thanks for hints!

perixx

---

### Post by forestpixie on 2007-10-14
I tend to use [gparted]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828") livecd to sort partitions before I install but

if you want to do it during install use the manual partitioning method - 
create a partition for root, mount as /
create a partition for home, mount as /home
create a swap partition 

it is [possible]("http://www.psychocats.net/ubuntu/separatehome") to move existing to a new partition

---

### Post by benerivo on 2007-10-14
It's easy to do this on a fresh install. You just have to partition the drive using GParted from the live cd before you install, making a separate partition for /home. Then during the installation you can select this partition to hold /home.

Look at [this website]("http://www.psychocats.net/ubuntu/separatehome") for doing it on a current installation

---

### Post by Lord Illidan on 2007-10-14
Warning, it can get a bit hairy when you move your /home folder to a seperate partition, so I recommend taking backups of your most important files beforehand.

---

### Post by alienexplorers on 2007-10-14
I had no problems creating a new /home partition and moving my /home stuff into it.  In fact it is how I created the /home partition I am using with 7.10....

---

### Post by perixx on 2007-10-14
Hello and thank you for your plentiful replies... =D>

I'll try it out the other day or at least at my next Ubuntu-install!!

Very helpful---thanks to all!

perixx

---

### Post by gjtoth on 2007-10-24
> **alienexplorers said:**
> I had no problems creating a new /home partition and moving my /home stuff into it.  In fact it is how I created the /home partition I am using with 7.10....

Would it be possible to show your fstab?  I'm in the process of moving my /home to a separate partition but, all instructions/tutorials relate to an older version of Ubuntu.

Thanks in advance.

---

### Post by forestpixie on 2007-10-24
you can have mine if that's a help to you

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c2db5fad-2540-4c3a-ac21-bd124059a495 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=dabb09c2-964c-466d-a039-cde4c30d23f8 /home           ext3    defaults        0       2
# /dev/sdb1
UUID=eebef378-1b5c-4b93-8d8c-8fa430f2dc73 /media/sdb1     ext3    defaults        0       2
# /dev/sdb2
UUID=6cebc2cf-6ba9-4c38-bdd8-5abf91ebf7d3 /media/sdb2     ext3    defaults        0       2
# /dev/sda3
UUID=8150326b-3b03-4e2a-bc5b-e0335617f2cf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by perixx on 2007-10-24
Hi! Here's mine (Xubuntu 7.04):


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=120247a9-3e01-440c-b2cf-cb70e9321988 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=e37de1b8-9e7f-4e53-b8d7-40cd5bbe8da7 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


I had other problems to solve but than transferring the /home directory so far, so sorry for not being any help here; but I suppose the procedure should be the same in Gusty and Feisty - so just try the suggestion of the post above...

perixx

---

### Post by perixx on 2007-10-26
Thanks a lot, forestpixie and benerivo!

I successfully transferred my /home folder to another partition following the info on your links! I even managed it without CD :]


by the way, that's what my fstab looks like now, gjtoth:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=120247a9-3e01-440c-b2cf-cb70e9321988 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=e37de1b8-9e7f-4e53-b8d7-40cd5bbe8da7 none            swap    sw              0       0
/dev/hda6 /home ext3 nodev,nosuid 0 2
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0



where /dev/hda6 is my new /home partition...

Again, many thanks for the help!


perixx

---

### Post by perixx on 2007-11-04
>> I managed to work out an '*improved Quick'n'Dirty*'-procedure that combines quick-partitioning & transferring both the /home and the /opt folders to different partitions -- Step 1a) + Step 2) -- use it at your own risk, though, NOT RECOMMENDED!! 

>> The safest / simpler method (like at Psychocats) is Step 1b) + Step 2) -- RECOMMENDED!! I've decided to also post it here for the sake of completeness and for users that like to have several explanations to the same topic. :]

>> PLEASE NOTE FIRST, that you can damage your OS to beyond recoverability WITH BOTH methods, also with that on 'psychocats' (though it's not as likely if you use 'psychocats' or Step 1b+ 2). Anyway, if your not a little adventurous or don't like the idea of maybe trashing your system and/or losing personal data (that's why you back it up first ;]), best keep away from all of those procedures(!) 


**Solution:**

Similar to this Howto here: - [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
- only a bit faster and more compressed (IMHO) - is my little solution 1b)+2b), where I moved & mounted /opt to /dev/hda7 and
moved & mounted /home to /dev/hda6 -- [at the same time I moved OpenOffice (in /hda1/opt/) to /hda7/]. 

>> You should know how to use Gparted, the Terminal and have a Live-CD at hand.
>> If you've already got a suitable partition for your /home folder, you can skip step 1a) / 1b), of course.

******************************************************************************************************
**[COLOR="Blue"]PARTITIONING:[/COLOR]**

[B]1a) Quick'n'dirty re-sizing the partition /hda1 of a  running Linux -- RISKY & NOT RECOMMENDED AT ALL, ONLY 'FOR THE BRAVE'!!!

:!: WARNING: working on an unmounted running system might screw up things, so in case you're unsure or if you have more than just a single primary partition and /swap, PLAEASE USE the LIVE-CD and/or refer to step 1b) for your own good!![/B]

OK, RISKY, but it worked **without Live-CD(!)** - but ONLY if there's just a single (primary) partition on the HDD (you'll have to unswap and maybe delete /swap first)! 
It should also work fine, if you're adding a partition in the free space after all others (or resizing a non-mounted partition of another system), at the very end of the HDD. 

**>> AT FIRST --  close all unnecessary apps and kill network; OPEN a Terminal, run 'gksudo mousepad /etc/fstab' (or accordingly for your desktop-version, see below) AND DO NOT  CLOSE THEM before you're fully finished with step 2 for safety!!!**
> 1) start Gparted
2) **[umount]** /hda1 (currently running Ubuntu system) 
- use 'sudo umount ext3 /dev/hda1' in Terminal, if Gparted complains (replace 'ext3' with any other filesystem, if any)
- unswap your /swap-partition and delete it, if Gparted complains
3) re-size /hda1 down to, say, 15GB 
4) create extended partition in free space (/hda2)
5) create 3 extended partitions within the new partition:
- a] e.g. /hda5 /swap partition, if deleted (e.g. 3-4GB at 2GB ram)
- b] e.g. /hda6 100GB ext3 partition for /home
- c] e.g. /hda7 40GB ext3 partition for /opt
6) commence changes and set up partitions (if it won't work, create each partition in a single step)
7) re-mount /hda1 (don't forget to set the boot-flag, if missing!)
8] mount partitions and do 'swapon' to /swap 
9) leave Gparted



**1b) re-sizing/creating /home-partition from Live-CD (example):**

Scenario:
/hda1 primary NTFS (XP, 50GB)
/hda2 primary FAT32 (storage, 10GB)
/hda3 extended
/hda5 -extended EXT3 (Xubuntu Feisty, 20 GB)
/hda6 -extended EXT2 (crap, 15 GB)
/hda7 -extended EXT2 (crap, 5 GB)
/hda8 -extended /swap (swap, 2 GB)

> 1) start Gparted
2) unmount (if they are not already) the partition(s) 
- you want to downsize/delete 
- 'below' the position from where you want to create your /home + /opt-partitons 
- also 'unswap' the /swap-partition, if needed.
2) re-size or delete (deletion="DATA LOST"!!) your target partitions
- e.g. re-size extended partition '/hda5 ext3 (Feisty-system)' down to 10GB, leaving 10GB free space
- delete extended partition '/hda6 + /hda7 ext2 (crap-partitions)', giving another 20GB free space.
3) create the new extended partitions /hda6 (type ext3) of 25GB size (/home) and /hda7 (type ext3) of 5GB size (/opt) in the free space between /hda5 and /hda8.
6) commence changes and set up partitions (if it won't work, do it in single steps).
7) mount your partitions again and do 'swapon' to /swap, if needed.
8] leave Gparted


>> DON'T FORGET TO ADAPT THE DESCRIPTIONS HERE TO YOUR PERSONAL NEEDS, should you have differently named partitions!

********************************************************************************

**[COLOR="Blue"]MOVING /HOME AND /OPT:[/COLOR]**

[B]2) now, open a Terminal and proceed with the actual '/home'-moving-procedure:
NOTE:[/B] /home and /opt have to be mounted to /media/hda6 and /media/hda7 for this step!
(if they're not already mounted, use 'sudo mount -t ext3 /dev/hda6 /media/hda6'...+ same for /hda7)

> sudo rsync -au --append /home/ /media/hda6
(copies the content of /home to the new home-partition, keeping all permissions)

> sudo rsync -au --append /opt/ /media/hda7
(copies the content of /opt to the new opt-partition, keeping all permissions)


Renaming your old folders to '_backup' and creating new ones + mounting them:
**NOTE:** mountpoints for /dev/hda6 + /hda7 have to be changed to the new folders, so we need to unmount them first!
(You do that with 'sudo umount /dev/hda6'...+ same for /hda7)

> sudo mv /home/ /home_backup
sudo mv /opt/ /opt_backup
sudo mkdir /home
sudo mkdir /opt
sudo mount -t ext3 /dev/hda6 /home
sudo mount -t ext3 /dev/hda7 /opt

now add the mounting-commands for the new partitions to their folders in fstab + backing it up first:

> sudo cp /etc/fstab /etc/fstab_backup
gksudo mousepad /etc/fstab (if not already open)
=> this refers to Xubuntu users, use 'sudo gedit' for Gnome (don't know for KDE) or 'sudo nano', if you prefer the command line.

Edit the file and add these two lines under '# /dev/hda6' + '# /dev/hda7': 
(DON'T FORGET to comment out or erase other mount-commands for these partitions (e.g. UUID:e543fg...... /media/hda6....)!!!

> /dev/hda6 /home ext3 nodev,nosuid 0 2
/dev/hda7 /opt ext3 nodev,nosuid 0 2

Save & exit.


Allright, that should work now - restart Ubuntu - you now should have moved your complete /home folder to /hda6 and the contents of /opt to /hda7!

=> I actually also moved the SBackup-folder from /var/backup successfully to /opt/backup (hda7) in order to avoid messing up the system due to an overboarding system-partition - When I think of trying sth. similar with XP's user-folders *LOL*

If you find that everything works satisfactorily you can delete /*_backup folders you've created before.


**JUST REMEMBER** - this solution worked for me, it won't necessarily for you - so everything happens on your own risk!!! Please use all commands as stated (esp. '/' slashes and mounting!) - BUT don't forget to adjust the partition's values to your needs.


**I CAN'T ACCESS MY ACCOUNT AT BOOT ANYMORE - GETTING STRANGE ERRORS!!**  - well, this happened to me several times :) 
Just don't panik! You've probably just used a '/' too much/less in 'fstab' or you forgot to 'sudo mount' your partitions before re-booting... 

Anyway, to revert to your BACKUP's, do the following:
> 1) Reboot.
2) When getting a break at the bash and error (fsk.ext3 or similar) - most probably a mistake in fstab/mounting - just type 'exit'.
3) At the login, change to 'protected Terminal'-session and log in. Just acknowledge all with YES / OK - you'll get a white USER-terminal.
4) type: 'sudo umount /dev/hda6'...'sudo umount /dev/hda7'...'ls /home'+'ls /opt' (should be empty -- safety-unmount + verifying)
5) 'sudo rsync -au /home_backup /home' (will take a while) + 'sudo rsync -au /opt_backup /opt' (recovering /home + /opt)
6) 'sudo rm /etc/fstab'....'sudo cp /etc/fstab_backup /etc/fstab' (recovering fstab-file)
7) 'sudo chmod 775 /home'...'sudo chmod 755 /USER' (safety-permission reset. Should also help with 'HOME/.dmrc'-error! -- replace 'USER' by your username.)
8] Reboot.


**Supplemental info on re-using /home partitions with a new installation:**
[http://ubuntuforums.org/showthread.php?t=166626]("http://ubuntuforums.org/showthread.php?t=166626")

Best regards - sorry for the bugs in previous version -

perixx

---

### Post by hogwartsnigel on 2007-11-13
Hi,
Thanks for the post. I managed to reduce my boot partition to the desired 30Gb, set up a 10gb swap, 160gb ext3, and a 70gb ext 3

When I tried to follow your console entry for moving home to my hda4 (your hda6) I received the following

[COLOR="Navy"][I] sudo rsync -au /home/ /dev/hda4
ERROR: destination must be a directory when copying more than 1 file
rsync error: errors selecting input/output files, dirs (code 3) at main.c(494) [receiver=2.6.9]
rsync: connection unexpectedly closed (8 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(454) [sender=2.6.9][/I][/COLOR]
 
[COLOR="Black"]My system is working fine and much cleaner but  I would appreciate any help in moving over my home and opt files.

Ta

Nigel[/COLOR]

---

### Post by az on 2007-11-13
> **perixx said:**
> a separate /home partition in order to have  no problems whatsoever with major future OS upgrades, as all personal data and settings remain persistent...


No problems whatsoever?

That's simply not true.  It's a lot easier and safer to back things up to another disk.  I do not recommend using the same configuration files for different distros, or different versions of the same distro.

Creating new partitions limits your disk space.

If you want a separate partition for home, that's fine, but it is completely false to claim that it presents no problems whatsoever.

---

### Post by perixx on 2007-11-14
'ello hogwartsnigel!

> sudo rsync -au /home/ /dev/hda4
ERROR: destination must be a directory when copying more than 1 file

I'm not currently having the set up system at hand, so I can't doublecheck this; maybe I made a slight mistake here, for I would think that should copy everything into the root-directory root of hda4, not just onto the drive:

> sudo rsync -au /home/ /dev/hda4[COLOR="Magenta"]/[/COLOR]


@az:

My apologies, but you're referring to my first post in this thread, where I was still looking for a solution - thus my quoted sentence merely marks a question but a claim. 

Granted, I'm not expert enough to judge whether there are problems arising of this method and which those are. Of course I know that another partition for backing up things is only second-best as a solution. Another drive is much more secure. Actually I didn't intend to call this a real 'backup' method anyway - more like: 'making things a little easier in case of a system-crash by keeping them separated'. I'm still doing manual backups with SBackup...

You'll agree that it's better to have your personal settings all on a different partition in case your installation screws up - plus you can avoid fragmentation on your system's partition - provided that all new apps are installed in /hda4/opt/ (on 'backup'-partition), don't you? 

I wonder how to have all /home and /opt folders of different Linux distributions on one separate partition or folder...
Do you think it might work to mount the respective Distro-folders to 
> /dev/hda4/DISTROx1/home
/dev/hda4/DISTROx1/opt
/dev/hda4/DISTROx2/home
/dev/hda4/DISTROx2/opt
.
.
.


?

And do you think that it's possible to use one /opt folder for using a program with several similar distros, e.g. all built on Debian, at a time? Or will every distro try to write its own settings to /opt instead of only into /home/.APPLICATION?
 

perixx

---

### Post by az on 2007-11-14
> **perixx said:**
> 

You'll agree that it's better to have your personal settings all on a different partition in case your installation screws up - plus you can avoid fragmentation on your system's partition - provided that all new apps are installed in /hda4/opt/ (on 'backup'-partition), don't you? 

/opt is not a linux FHS-compliant place to install software and the Ubuntu package manager does not put packages there.

No, it's not better to put personal setting on a separate partition.  That's a false sense of security.  If you get hardware problems, it's unlikely that one partition gets spared over another.  If you cannot boot your OS but can still access the disk, it's irrelevant whether you are backing up from a home folder or partition.

As well, a lot of times you will "screw up your system" because of a misconfiguration - the solution to which is to create a new user (and jettison the borked configs).

A separate partition will create more fragmentation since fragmentation happens when the filesystem is full and each smaller filesystem will fill up faster than one big filesystem.


> **perixx said:**
> 

And do you think that it's possible to use one /opt folder for using a program with several similar distros, e.g. all built on Debian, at a time? Or will every distro try to write its own settings to /opt instead of only into /home/.APPLICATION?
 

Linux is not binary-compatible.  I would stick with my distro's package manager version of the application and keep up-to-date that way.

---

### Post by perixx on 2007-11-14
Hi az...

> /opt is not a linux FHS-compliant place to install software and the Ubuntu package manager does not put packages there.

Allright, I still have to figure out, WHERE Ubuntu-.deb-packages are installed to exactly. As I heard, compiled stuff goes into /opt, though (I want to learn how to compile more recent app-versions, so that's still interesting to me)... 
The official OpenOffice.org version (not the buggy Ubuntu version) went into /opt as well - I do not know how to influence such behaviour, though. I assume there's a switch for apt-get to specify installation paths, maybe?   

> As well, a lot of times you will "screw up your system" because of a misconfiguration - the solution to which is to create a new user (and jettison the borked configs).

That sounds reasonable to me, as long as I knew how to let 'rsync' automatically apply the respective user-dependent file permissions while transferring the account's data. 

Still, I'm not fully convinced by the futility of moving the /home folder.... If my OS really gets smoked (and not by hardware failure), there's always still the chance that all my personal desktop-settings are being instantly re-used after newly installing Ubuntu, I believe - and this could also apply to some /opt-installed programs... 

Perhaps I should try this out!

As I said, this is no replacement for a real backup, of course. But for a 'soft-borked' system simply recovering an auto-backup from the optional /home partition seems no bad idea to me.


perixx

---

### Post by hogwartsnigel on 2007-11-15
Hi guys,
you two..... now behave...I managed to move my home file to a seperate partition as intended  but via another thread and link [http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index)  great reference url.

I now have my partition system as I want but am looking through a decent graphic interface back up my partitions onto another hard drive...any suggestions on the best utility for this for a pleb like me?

Ta

Nigel

---

### Post by perixx on 2007-11-21
Hi howgwartsnigel,

I was pretty busy these days, sorry 

Currently, I've been using the 'rsync' CLI method (used together with a starter-button it's sort of a manual 'graphic backup utility').

I've also been using 'SBackup' which is seens powerfull - don't forget to adjust the backup folder away from your current Ubuntu-partition, though - you might otherwise render your system non-functional if using up all space on the partition.


Here you can find some further hints on backups I received:
> [http://ubuntuforums.org/showthread.php?t=602409](http://ubuntuforums.org/showthread.php?t=602409)
[http://ubuntuforums.org/showthread.php?t=592788](http://ubuntuforums.org/showthread.php?t=592788)

Another graphical backup utility would be 
'HomeUserBackup', but I haven't tried this one yet. It also can burn your backups onto media.


perixx

---

### Post by mike555 on 2007-11-21
I know a lot of people recommend setting up a /home , but in my experience it messes up upgrades , because it has some hidden config files .................. it might be better to make a separate   /backup   partition and just drag your doc's and stuff into it before upgrading , that way you can upgrade without the   /home interfering  with a setting ......

---

### Post by perixx on 2007-11-21
@mike555:

> in my experience it messes up upgrades , because [COLOR="Blue"]it[/COLOR] has some hidden config files 
What hidden files from what and where do you exactly mean?? I'm lost...


Simply dragging my documents to that /backup partition seems inferior a solution to me, compared to using a backup tool. Not only that you probably would lose file permissions, but you'd always would have to drag the whole /home folder in order not to leave out anything and to have your desktop settings with you - which is much more file copying work for the HDD, than just doing an incremental backup.


perixx

---

### Post by mike555 on 2007-11-22
[QUOTE=perixx;3812806]@mike555:


What hidden files from what and where do you exactly mean?? I'm lost...

   Your  /home  folder has hidden files in it  (you can see them by clicking view , hidden files) they are config files that tell the computer how you like your apps and desktop set up ........... but when you upgrade to a newer version sometimes it messes things up , especially if you go from KDE to gnome ....... I think it's better to have a  /backup  partition and just backup all your pictures and documents and bookmarks into it before upgrading  ............ just my opinion

---

### Post by perixx on 2007-11-24
Well mike555,

I was referring to a 'desktop-persistent' upgrade, of course! KDE and Gnome seem to be more advanced in terms of menus and looks. But they're much too bloated for my taste; apart from that, I assume that everybody stays with his favoured desktop once he found out what he likes best, thus not having to worry about the different desktop-system's setup. 

So, if you stick to a certain desktop-flavour (Ubuntu, Kubuntu or Xubuntu), I suppose you shouldn't have that much trouble using the method I was writing about here... 

When doing major release-upgrades, I would think it's a good idea to backup the /home folder of the fresh installation, before switching to the 'old' /home partition, though. You've got a point there!


perixx

---

### Post by perixx on 2008-01-09
Just for those who stumbled across my alternate /home+/opt HowTo of this thread, **I've updated** the backup-procedure it in the meantime and added a warning message as well...

perixx

---

