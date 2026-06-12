---
title: "Filesystem Problems"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by apokkalyps on 2008-04-10
Periodically, my main hard drive seemingly at random after being booted up and running, will "become" read-only.  All my file attributes are the same,  So I think its on the device level.  Nothing will run after this happens and things will slowly start to fail.  All I can do is reboot and then it seems to work fine.  It's happened at least 3 or 4 times  Any Idea what could cause this or how to fix it?

Also, I just noticed on accident, and this could be very closely related: when I do

> tail -f /var/log/messages

I continually (like every two seconds) get read/write out-of-bounds errors.

> Apr 10 17:03:15 barrett-desktop kernel: [44835.720200] sda1: rw=0, want=14954908416, limit=755424432
Apr 10 17:03:17 barrett-desktop kernel: [44837.627438] attempt to access beyond end of device
Apr 10 17:03:17 barrett-desktop kernel: [44837.628036] sda1: rw=0, want=14954908416, limit=755424432
Apr 10 17:03:17 barrett-desktop kernel: [44838.052037] attempt to access beyond end of device
Apr 10 17:03:17 barrett-desktop kernel: [44838.052446] sda1: rw=0, want=14954908416, limit=755424432
Apr 10 17:03:17 barrett-desktop kernel: [44838.477566] attempt to access beyond end of device
Apr 10 17:03:17 barrett-desktop kernel: [44838.477908] sda1: rw=0, want=14954908416, limit=755424432
Apr 10 17:03:18 barrett-desktop kernel: [44838.914468] attempt to access beyond end of device
Apr 10 17:03:18 barrett-desktop kernel: [44838.914710] sda1: rw=0, want=14954908416, limit=755424432
Apr 10 17:03:18 barrett-desktop kernel: [44839.421830] attempt to access beyond end of device
Apr 10 17:03:18 barrett-desktop kernel: [44839.422242] sda1: rw=0, want=14954908416, limit=755424432
Apr 10 17:03:20 barrett-desktop kernel: [44841.380187] attempt to access beyond end of device
Apr 10 17:03:20 barrett-desktop kernel: [44841.380502] sda1: rw=0, want=14954908416, limit=755424432
Apr 10 17:03:21 barrett-desktop kernel: [44841.939170] attempt to access beyond end of device
Apr 10 17:03:21 barrett-desktop kernel: [44841.939655] sda1: rw=0, want=14954908416, limit=755424432
Apr 10 17:03:22 barrett-desktop kernel: [44842.529441] attempt to access beyond end of device
Apr 10 17:03:22 barrett-desktop kernel: [44842.529744] sda1: rw=0, want=14954908416, limit=755424432
Apr 10 17:03:23 barrett-desktop kernel: [44843.788661] attempt to access beyond end of device
Apr 10 17:03:23 barrett-desktop kernel: [44843.788912] sda1: rw=0, want=14954908416, limit=755424432
Apr 10 17:03:25 barrett-desktop kernel: [44846.400113] attempt to access beyond end of device
Apr 10 17:03:25 barrett-desktop kernel: [44846.400462] sda1: rw=0, want=14954908416, limit=755424432


I would have never noticed this if I wasn't trying to figure out why ubuntu isn't detecting my Nomad Mp3 player.

Is there any way to find out what program is causing this message?

---

### Post by herbster on 2008-04-10
Run

```
fsck -fvn /dev/sda1
```

And paste output back here when done.

---

### Post by apokkalyps on 2008-04-11
It happened again.  I rebooted it and it halted bootup and made me run fsck manually because something failed.   Unfortunatly I couldn't capture the output of the first fsck I did, but It fixed a crapload of orphaned inodes.  Or at least it said it fixed them.  Then I rebooted back into gnome and ran at a terminal:


> barrett@barrett-desktop:~/.evolution/mail/local$ fsck -fvn /dev/sda1
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
Warning!  /dev/sda1 is mounted.
fsck.ext3: Permission denied while trying to open /dev/sda1
You must have r/o access to the filesystem or be root
[email]barrett@barrett-desktop:~/.evol[/email]ution/mail/local$ sudo !!
sudo fsck -fvn /dev/sda1
[sudo] password for barrett:
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
Warning!  /dev/sda1 is mounted.
Warning: skipping journal recovery because doing a read-only filesystem check.
Pass 1: Checking inodes, blocks, and sizes
Deleted inode 1261572 has zero dtime.  Fix? no

Inodes that were part of a corrupted orphan linked list found.  Fix? no

Inode 1261573 was part of the orphaned inode list.  IGNORED.
Inode 1261574 was part of the orphaned inode list.  IGNORED.
Inode 1261575 was part of the orphaned inode list.  IGNORED.
Inode 1261576 was part of the orphaned inode list.  IGNORED.
Inode 18956710 was part of the orphaned inode list.  IGNORED.
Inode 37191689 was part of the orphaned inode list.  IGNORED.
Inode 40306034 was part of the orphaned inode list.  IGNORED.
Inode 40306119 was part of the orphaned inode list.  IGNORED.
Inode 40306317 was part of the orphaned inode list.  IGNORED.
Inode 40878993 was part of the orphaned inode list.  IGNORED.
Inode 40878995 was part of the orphaned inode list.  IGNORED.
Inode 42681544, i_size is 151022, should be 159744.  Fix? no

Inode 42681544, i_blocks is 304, should be 320.  Fix? no

Pass 2: Checking directory structure
Entry 'browse.dat' in /var/cache/samba (18956316) has deleted/unused inode 18956715.  Clear? no

Entry 'file-meta.db-journal' in /home/barrett/.cache/tracker (42680376) has deleted/unused inode 42680789.  Clear? no

Entry '%gconf.xml' in /home/barrett/.gconf/apps/gnome-screensaver (42680476) has deleted/unused inode 42680682.  Clear? no

Entry '.mcoprc' in /home/barrett (42680322) has deleted/unused inode 42680442.  Clear? no

Entry 'segments' in /home/barrett/.beagle/Indexes/FileSystemIndex/PrimaryIndex (42713644) has deleted/unused inode 42717225.  Clear? no

Entry 'deletable' in /home/barrett/.beagle/Indexes/FileSystemIndex/PrimaryIndex (42713644) has deleted/unused inode 42717210.  Clear? no

Entry '_1ss.del' in /home/barrett/.beagle/Indexes/FileSystemIndex/PrimaryIndex (42713644) has deleted/unused inode 42717204.  Clear? no

Entry '_1ss.del' in /home/barrett/.beagle/Indexes/FileSystemIndex/SecondaryIndex (42713645) has deleted/unused inode 42717202.  Clear? no

Entry 'uid-cache' in /home/barrett/.evolution/mail/pop/apokkalyps@mail.charter.net (42827874) has deleted/unused inode 37666827.  Clear? no

Entry 'knotifyrc' in /home/barrett/.kde/share/config (42845032) has deleted/unused inode 42846408.  Clear? no

Entry 'tpb.tracker.thepiratebay.org_announce_4969a6f3' in /var/tmp/kdecache-barrett/http/t (19054600) has deleted/unused inode 19056719.  Clear? no

Entry 'open.tracker.thepiratebay.org_announce_26377145' in /var/tmp/kdecache-barrett/http/o (19054768) has deleted/unused inode 19056729.  Clear? no

Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Unattached zero-length inode 18957416.  Clear? no

Unattached inode 18957416
Connect to /lost+found? no

Unattached zero-length inode 19055376.  Clear? no

Unattached inode 19055376
Connect to /lost+found? no

Unattached zero-length inode 41844883.  Clear? no

Unattached inode 41844883
Connect to /lost+found? no

Unattached zero-length inode 42680843.  Clear? no

Unattached inode 42680843
Connect to /lost+found? no

Unattached inode 42716513
Connect to /lost+found? no

Unattached zero-length inode 42717206.  Clear? no

Unattached inode 42717206
Connect to /lost+found? no

Unattached zero-length inode 42717209.  Clear? no

Unattached inode 42717209
Connect to /lost+found? no

Unattached zero-length inode 42717224.  Clear? no

Unattached inode 42717224
Connect to /lost+found? no

Unattached zero-length inode 42846379.  Clear? no

Unattached inode 42846379
Connect to /lost+found? no

Pass 5: Checking group summary information
Block bitmap differences:  -15016056 +28609683 -(28739936--28739968) -(28739975--28740101) +(28740103--28740134) -(28740135--28740136) +(28740137--28740341) -(28740344--28740382) +(28740383--28740389) -(28740390--28740444) -28771228 +37929623 -37929631 +40583697 +40583926 -(40585406--40585409) +41986982 -72878080 +72878081 -(74397697--74397701) -74407936 +75089924 -75089925 -(75358208--75358214) +83695623 -85361945 -(85364850--85364851) -85364860 -85364893 -85364898 -85365136 -85365142 -(85365144--85365146) -(85365148--85365151) -(85365215--85365216) -85368745 -85368748 -85368836 -(85377868--85377873) +(85381172--85381173) -(85381175--85381176) -85385481 -(85385560--85385582) -(85439962--85439965) +85440019 +85440022 +85440079 +(85440081--85440120) +85440122 +85440172 +(85440174--85440175) +85440177 +85446947 +85472251 -85472282 -85472303 -(85472411--85472419) -85472421 -85472424 +(85472904--85472907) +(85502365--85502366) +(85502368--85502369) +85502372 -(85502391--85502414) -85502751 -85502753 -(85502755--85502757) -(85502759--85502780) -(85502792--85502798) -85502800 +85502809 +85502813 -(85502815--85502816) +(85502817--85502819) +(85502830--85502831) +(85503605--85503607) +(85503776--85503786) +85503788 +(85503808--85503809) -85503899 -(85503901--85503906) -(85522287--85522297) -85522299 +(85522312--85522313) -(85522316--85522323) -85522325 -(85522327--85522328) -(85522330--85522333) -(85522336--85522440) -(85522452--85522465) -(85522468--85522489) -(85522492--85522493) -(85522496--85522562) -(85522607--85522614) +85695439 -85723713 -85731549 +87715874
Fix? no

Free blocks count wrong for group #458 (2, counted=1).
Fix? no

Free blocks count wrong for group #873 (231, counted=4).
Fix? no

Free blocks count wrong for group #877 (30385, counted=30112).
Fix? no

Free blocks count wrong for group #878 (32249, counted=32242).
Fix? no

Free blocks count wrong for group #1160 (994, counted=993).
Fix? no

Free blocks count wrong for group #1238 (3326, counted=3324).
Fix? no

Free blocks count wrong for group #1281 (7343, counted=7344).
Fix? no

Free blocks count wrong for group #2270 (32214, counted=32208).
Fix? no

Free blocks count wrong for group #2299 (32111, counted=32104).
Fix? no

Free blocks count wrong for group #2462 (1841, counted=1896).
Fix? no

Free blocks count wrong for group #2495 (19643, counted=19673).
Fix? no

Free blocks count wrong for group #2554 (31274, counted=31275).
Fix? no

Free blocks count wrong for group #2605 (2431, counted=2291).
Fix? no

Free blocks count wrong for group #2607 (186, counted=380).
Fix? no

Free blocks count wrong for group #2608 (76, counted=81).
Fix? no

Free blocks count wrong for group #2609 (457, counted=217).
Fix? no

Free blocks count wrong for group #2614 (1, counted=2).
Fix? no

Free blocks count wrong for group #2615 (7, counted=9).
Fix? no

Free blocks count wrong for group #2616 (16, counted=7).
Fix? no

Free blocks count wrong for group #2676 (2, counted=3).
Fix? no

Free blocks count wrong (10768233, counted=10741722).
Fix? no

Inode bitmap differences:  -(1261572--1261576) -1261623 -18956715 +18957416 +19055376 -19056719 -19056729 -(37191688--37191690) -(37191692--37191697) -37666827 +41844883 -42680442 -42680682 -42680789 +42680843 +42716223 -42716254 +42716513 -42717202 +(42717208--42717209) -42717222 +42717224 +42846379 -42846408
Fix? no

Free inodes count wrong for group #77 (16308, counted=16307).
Fix? no

Free inodes count wrong for group #1163 (13166, counted=13165).
Fix? no

Free inodes count wrong for group #2270 (16377, counted=16368).
Fix? no

Free inodes count wrong for group #2299 (16374, counted=16373).
Fix? no

Free inodes count wrong for group #2460 (11163, counted=11166).
Fix? no

Free inodes count wrong for group #2495 (13533, counted=13535).
Fix? no

Free inodes count wrong for group #2554 (16236, counted=16237).
Fix? no

Free inodes count wrong for group #2605 (495, counted=493).
Fix? no

Free inodes count wrong for group #2607 (12246, counted=12266).
Fix? no

Free inodes count wrong for group #2614 (15965, counted=15966).
Fix? no

Free inodes count wrong (46744333, counted=46744745).
Fix? no


/dev/sda1: ********** WARNING: Filesystem still has errors **********


  474355 inodes used (1.00%)
   16583 non-contiguous inodes (3.5%)
         # of inodes with ind/dind/tind blocks: 72444/8659/0
83659821 blocks used (88.60%)
       0 bad blocks
       9 large files

  407454 regular files
   34342 directories
     132 character device files
      26 block device files
       3 fifos
     475 links
   31914 symbolic links (26045 fast symbolic links)
      47 sockets
--------
  474396 files


Also do you know whats up with the warning about fscking a mounted filesystem?  Is tha something to be concerned about?

---

### Post by herbster on 2008-04-12
You don't want to run a fsck on a mounted filesystem, that's why it gives you that, but I gave you a command that runs it as read-only, so as you can see it says "no" to every query of whether or not to fix errors.

Paste the output of

```
sudo fdisk -l
```

Do you know what is on /dev/sda1? Is it your root? Another drive of data or something?

---

### Post by apokkalyps on 2008-04-13
yeah /dev/sda1 is my root drive.  Which makes me more concerned about it failing.  
Is that an abnormal amount of errors?  I assume any errors is bad?

Although I just yesterday backed up my 400gig home folder to an external drive.


> barrett@barrett-desktop:~$ sudo fdisk -l
[sudo] password for barrett:

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbbc58b91

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       47023   377712216   83  Linux
/dev/sda2           47024       48641    12996585    5  Extended
/dev/sda5           47024       48641    12996553+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdd404b77

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdc: 507 MB, 507379712 bytes
16 heads, 63 sectors/track, 983 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         983      495313+   6  FAT16


---

### Post by herbster on 2008-04-14
You can reboot your computer so that it runs fsck on reboot:

```
sudo shutdown -F
```

Obviously, be sure you've closed your apps/saved your stuff you might be working on, that'll reboot your box and run the fsck on reboot.

---

