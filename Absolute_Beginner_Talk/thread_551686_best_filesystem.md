---
title: "best filesystem"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by KCormier on 2007-09-15
Howdy.  So for all my installs so far I just use ext3 but I'm working on a new project and I want the best efficiency from my hard drive that I can get!  I am building a server to hold all my movies/music to play on my tv.  I may also stream some over my network to my laptop and such.  I'm using a 500gb hard drive just for videos.  Then I have a second 160 gb drive for linux and music.  I'm gonna make an 60gb ext3 partition for linux and programs.  Then I'm going to have a 100 gb partition for music and a 500gb partition videos.  I was wondering what format to use for the music and video partitions.  I'm more worried about speed than data security.  I know journaling filesystems keep a record of the changes they make so that those changes can be undone in case of a major problem.  I can only imagine this log takes up room and hard disk bandwidth.  (I may be at most trying to read two dvds (one desktop, one laptop) and write one to disk at the same time.  That's the heaviest access it'll see.  Do you think I can set it up to handle that?  ATA133 drive.  Thanks!!

Kevin

---

### Post by logos34 on 2007-09-15
I'd look into XFS.

[http://www.debian-administration.org/articles/388](http://www.debian-administration.org/articles/388)
[http://oss.sgi.com/projects/xfs/](http://oss.sgi.com/projects/xfs/)
[http://en.wikipedia.org/wik](http://en.wikipedia.org/wik)

---

### Post by rsambuca on 2007-09-15
Here is a site with a lot of benchmarks.

[http://linuxgazette.net/122/TWDT.html#piszcz](http://linuxgazette.net/122/TWDT.html#piszcz)

Which ever system you chose, I would consider adding the 'noatime' option to your fstab, which will make it much quicker for your purposes.

---

### Post by KCormier on 2007-09-15
awesome!  There's no major pitfalls in setting noatime?  can i do that through gparted setting flags?

Kevin

---

### Post by logos34 on 2007-09-15
> **rsambuca said:**
> I would consider adding the 'noatime' option to your fstab, which will make it much quicker for your purposes.

If you decide to stick with ext3 you could also add **data=writeback** option right after noatime.  (although in my personal experience the performance gains are negligible).  

 rsambuca: that's a great benchmark link.  i'm bookmarking it.

---

### Post by Rasitiln on 2007-09-15
XFS gets fragmented last I remember. 

I use Reiserfs for my ubuntu install, and ext3 on my storage HD, just so I can access it in a windows environment if I ever need to for some odd reason.

---

### Post by SunnyRabbiera on 2007-09-15
well even though I can answer that on a personal note I think that all linux file systems have their ups and downs.
I have tried Reiser, EXT 2 and 3 and XFS and at this point I would  gladly recommend XFS or Ext3
Reiser is fair but I would stay away from it as i think its gonna die soon as Hans Reiser its creator is being charged in murder.
i would reccomend ext3 though if you are still dual booting windows as this make better compatibility for moving files.

---

### Post by logos34 on 2007-09-15
> Hans Reiser its creator is being charged in murder

no ***?

edit: OMG! he was just arraigned and is being held in a Bay area jail...wow

---

### Post by SunnyRabbiera on 2007-09-15
uh huh, its true.
its actually kind old news but you can look it up easy

---

### Post by KCormier on 2007-09-16
So i've got gparted installed but it doesn't seem to support xfs.  Is there something I'm doing wrong?

Kevin

---

### Post by logos34 on 2007-09-16
Menu>Partition>Format to>XFS (bottom)

Anything?

Make sure the partition is unmounted, otherwise it will be grayed out.

Maybe you've got the older version. I know 0.3.3 supports it.

---

### Post by KCormier on 2007-09-16
i do have the old version :-/  How can i get the latest version of gparted?  apt-get and synaptic and everything say i have the latest version :(

Kevin

---

### Post by logos34 on 2007-09-16
> **KCormier said:**
> i do have the old version :-/  How can i get the latest version of gparted?  apt-get and synaptic and everything say i have the latest version :(

Kevin

it would probably be easier to use the commandline:
[B]
man mkfs.xfs[/B]

gparted  0.3.3 .deb pkg:
[http://ubuntuforums.org/showthread.php?t=465272](http://ubuntuforums.org/showthread.php?t=465272)
[http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fg%2Fgparted%2Fgparted_0.3.3-2ubuntu4_i386.deb&md5sum=e62b63fd1e7d91f44053cee5a1dc7b23&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fg%2Fgparted%2Fgparted_0.3.3-2ubuntu4_i386.deb&md5sum=e62b63fd1e7d91f44053cee5a1dc7b23&arch=i386&type=main)

---

### Post by newman on 2007-09-16
I believe NTFS is the best file system for most applications.

---

### Post by K.Mandla on 2007-09-16
I use straight ext2 everywhere, with noatime set. I haven't seen anything faster yet.

---

### Post by jordanmthomas on 2007-09-16
> **newman said:**
> I believe NTFS is the best file system for most applications.

Why is that?

---

### Post by logos34 on 2007-09-16
> **newman said:**
> I believe NTFS is the best file system for most applications.

You're just asking to get flamed.

But how can you say that, ntfs fragments much more than ext2/3, and is not nearly as forgiving after a power loss (ext3 isn't failsafe but dam near). 

[QUOTE=K.Mandla]I use straight ext2 everywhere, with noatime set. I haven't seen anything faster yet.[/QUOTE]

I didn't see any performance gains when I tried it my edgy install (along with other tweaks like prelinking, data writeback, etc).  Must've misconfigured it.

---

### Post by newman on 2007-09-16
> **jordanmthomas said:**
> Why is that?

On every system I've tried it seems faster and more responsive - I know it's not an exact comparison because of the different OS's in use, but I've tried a few file transfer tests, and NTFS was faster than ext3 and reiser. I have had power outages and even shutdown the PC abruptly with no data loss in NTFS. ext3 for some reason screwed up all my file access time stamps.  Also my hard drive seems to be constantly making activity noise with ext3, where as in windows with NTFS it wasn't. As far as fragmenting goes, I always run O&O defrag on NTFS so that is no issue - I find it hard to believe that ext3 doesn't require defrag.

---

### Post by qamelian on 2007-09-16
> **newman said:**
> On every system I've tried it seems faster and more responsive - I know it's not an exact comparison because of the different OS's in use, but I've tried a few file transfer tests, and NTFS was faster than ext3 and reiser. I have had power outages and even shutdown the PC abruptly with no data loss in NTFS. ext3 for some reason screwed up all my file access time stamps.  Also my hard drive seems to be constantly making activity noise with ext3, where as in windows with NTFS it wasn't. As far as fragmenting goes, I always run O&O defrag on NTFS so that is no issue - I find it hard to believe that ext3 doesn't require defrag.

NTFS is not that great. When I still used XP for video work, converting my drive from FAT32 to NTFS rendered the drive unusable for video capture from my camera. I had to replace the 5400 RPM drives with 7200 RPM drives to get the same performance I previously got under FAT32.

Also, your free to believe what you like, but in 9 years of running Linux, I have never had to defrag an ext2/3 filesystem.

---

### Post by KCormier on 2007-09-16
ok.  So i got ubuntu set up with the 3 partitions and everythings mounting automatically.  I have samba set up, vnc set up, it's hooked up to my tv, i can play videos just fine with vlc media player.  yay.  One last task.  I have a remote.  I've gone into keyboard shortcuts and bound the specific buttons with their actions but vlc doesn't seem to use these bindings.  Anyone know how to get vlc to work with my remote?  I'm using vlc so i can take the dvd's as isos and keep the menu structure and everything else like that!  Any ideas?

Kevin

---

