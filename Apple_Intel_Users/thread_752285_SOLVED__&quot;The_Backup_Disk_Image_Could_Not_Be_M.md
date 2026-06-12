---
title: "SOLVED:  &quot;The Backup Disk Image Could Not Be Mounted&quot; using Time Machine over AFP"
date: 2008-04-11
forum: Apple Intel Users
---

### Post by Fisslefink on 2008-04-11
[SIZE="3"]My setup:[/SIZE]

[I]I use Time Machine on Mac OS X Leopard 10.5.2 (with latest updates) to back up to an **hfsplus (non-journaled) **partition on my Ubuntu Feisty box, which I have shared over AFP ([[COLOR="DarkOrange"]here's how[/COLOR]]("http://www.macosxhints.com/article.php?story=20071110145136486")) using Netatalk and Avahi ([[COLOR="DarkOrange"]here's how[/COLOR]]("http://ubuntuforums.org/showthread.php?t=347019")).  
The sparsebundle destination is encrypted with AES-128 ([[COLOR="DarkOrange"]here's how[/COLOR]]("http://forums.macrumors.com/showthread.php?t=434960")), so my sensitive work data is encrypted via File Vault on my Mac, and it backs up to a secure destination, even while I'm logged in.  It's great![/I]

-----------------------

[SIZE="3"]The issue:[/SIZE]

Backups usually work marvelously, mounting the share automatically and performing the backup in the background while I am logged in.  It doesn't unmount it quite as gracefully (afpd on the Ubuntu box still sees a user logged in), but I can live with that.
[B]
This morning, I got a mysterious error from Time Machine:
 > Time Machine Error
The backup disk image could not be mounted
[/B]

Oh no, I thought... there go all of my backups!  Reading [[COLOR="DarkOrange"]this thread[/COLOR]]("http://discussions.apple.com/message.jspa?messageID=6032779") made me even more concerned.  

[SIZE="3"][COLOR="Blue"]However, there is a solution.  [/COLOR][/SIZE]
Taking a look in dmesg using "dmesg|grep hfs" on the Ubuntu box, I discovered this error:
"hfs: Filesystem was not cleanly unmounted, running fsck.hfsplus is recommended.  mounting read-only."

Curiously, running "mount" on the Ubuntu box reports that the hfsplus partition was mounted with the "rw" flag ... so it looks like it's read/write, but it's really not, for the safety of your data.  Just something to watch out for.

So I figured maybe if I repaired the filesystem and remounted it read/write again, it would get rid of the Time Machine error.  I'll cut to the punchline:  [COLOR="Blue"]Once the hfsplus filesystem was repaired, Time Machine backed up to it over AFP with no problems at all, just like it used to[/COLOR]

--------------------------

[SIZE="3"]Adventures in compiling fsck.hfsplus:[/SIZE]

This requires the program "fsck.hfsplus" which some people claim comes in the hfsutils and hfsprogs packages, but I haven't found that to be the case.  Indeed, I found a bug report that would suggest it really is missing. ([[COLOR="DarkOrange"]#135070[/COLOR]]("http://www.google.com/url?sa=t&ct=res&cd=1&url=https%3A%2F%2Flaunchpad.net%2Fbugs%2F135070&ei=moT_R-SJJYiYoQSSy4zhBw&usg=AFQjCNFYkkeA4GxT75JCQOS7K8Q-ZENlQg&sig2=LO0Qv0ODr9rJ9TwNMF_4ZQ"))

So I had to compile fsck.hfsplus myself.  

I found these two forum topics ([[COLOR="DarkOrange"]#1[/COLOR]]("http://ubuntuforums.org/showthread.php?t=392287"), [[COLOR="DarkOrange"]#2[/COLOR]]("http://ubuntuforums.org/showthread.php?t=392287")) very useful guides, except that the links for the source and the patch didn't work (see below):

Since the links for the source and the patch are broken now, I had to dig around to find links that work.  As of April 11, 2008, these links work:
[[COLOR="DarkOrange"]http://gentoo.osuosl.org/distfiles/diskdev_cmds-332.14.tar.gz[/COLOR]]([COLOR="DarkOrange"]http://gentoo.osuosl.org/distfiles/diskdev_cmds-332.14.tar.gz[/COLOR])
[[COLOR="DarkOrange"]ftp://ftp.fi.debian.org/pub/gentoo/distfiles/diskdev_cmds-332.14.patch.bz2[/COLOR]]([COLOR="DarkOrange"]ftp://ftp.fi.debian.org/pub/gentoo/distfiles/diskdev_cmds-332.14.patch.bz2[/COLOR])

With these links and the directions in the topics referenced above, I was able to build and compile fsck.hfsplus on Feisty Fawn on a 32-bit system, with no problems.  There is even a post later on in thread #1 that explains how to [[COLOR="DarkOrange"]build fsck.hfsplus on 64-bit systems[/COLOR]]("http://ubuntuforums.org/showpost.php?p=4591297&postcount=27").

Hopefully putting all this info in one place will make this task easier on the next guy.

---

### Post by cyberdork33 on 2008-04-11
you could also just run repair with Disk Utility on the Mac... the hfs tools on linux are not all that reliable. Either way, I don't know why you are using a HFS filesystem... the sparse bundle file can be created on any filesystem...  Maybe this is a requirement for netatalk or something?

---

### Post by Seamus on 2008-04-27
Hmm, I'm using ubuntu as well, but it's just an ext3 filesystem, and it worked fine until 10.5.2 was released and now I get the same issue - the disk image could not be mounted.

I've not found a solution for this yet :(

Any suggestions would be greatly appreciated!

---

### Post by Fisslefink on 2008-06-18
I just had the same problem.  That error can be caused when Time Machine is attempting to hard link to a previously corrupted backup.

Try this:
1) Connect to the shared drive from your Mac
2) Mount the .sparsebundle on your Mac
3) Inside the .sparsebundle, expand the folder "Backups.backupsdb"/<your_user_name>
4) Sort the contents by date
5) Delete the link "Latest" and also the most recent incremental backup folder (ie. "2008-06-18-075750")
6) Unmount the .sparsebundle
7) Go into Time Machine Preferences, choose "Change Disk..."
8) Select the shared drive (not the sparsebundle)
9) Click Start Backup.  After "Preparing" for a little while, it start backing up again.
10) Click Enter Time Machine when it's done backing up.  All of your old backups should be visible (whew!)

This solution was inspired by the discussion here: [http://discussions.apple.com/message.jspa?messageID=7133581](http://discussions.apple.com/message.jspa?messageID=7133581)

---

