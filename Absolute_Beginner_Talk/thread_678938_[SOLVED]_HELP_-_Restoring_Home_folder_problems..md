---
title: "[SOLVED] HELP - Restoring Home folder problems."
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by Bruce M. on 2008-01-26
Hi Folks, 

I had to do a re-install and was working with this problem until 5:30 this morning.  Trying to get the answer before coming here, alas, here I am.

Some time ago I downloaded HUBackup and was making semi-regular backups of my /home folder.  I'd let it run over night because it takes a long time.

24 Jan - all night:
 I ran HUBackup and created: **/media/sdb1/backup/24Jan08/bruloo-master-archive.1.dar**

25 Jan:
 I moved my /home folder to it's own partition, I had a moment of panic, but it ended up working well.
 Then because of my clumsy fingers I made the *Greatest of Ubuntu Sins*; I deleted /home.
 (Please, Don't ask! It's a personal thing but I ***HAD*** to leave the computer in a rush, and inadvertently deleted it by accident!)  :(

 OK, no problem, I'll run HURestore ... the program doesn't even start! NOTHING!

 So all night, until 5:30 this morning, I've been searching and reading about HUBackup, a "lot" of horror stories out there.

 *This program should NOT be in Ubuntu's repositories, or a WARNING in the Beginner's Area.*

So here I am a, clean install, with my **/home** sitting here: **/media/sdb1/backup/24Jan08/bruloo-master-archive.1.dar**, and anything I create from this moment until I get that extracted will reside on: /media/sdb1/

In my search I found this:
> 
Restoring File Using HUBackup

After receiving quite some emails about folks bewildered by the crashing hurestore I think it's only fair to create a post about how to restore files from archives created using hubackup using the underlying archiver , DAR.

Usually after a typical run of hubackup you will have two resulting files:

.hubackup-data/paepp-master-archive.1.dar
.hubackup-data/paepp-master-catalog.1.dar

(Thanks goes to Peter Päppinghaus for sending me an email about this)

To restore , which actually usually means extract in DAR's language you need to do something like:

dar -x .hubackup-data/paepp-master-archive -R TARGET_DIR

If there is more then one slice DAR knows how to switch between them properly.

That should be enough for most of operations, for more detailed explanation of what dar can do in restoration (or backup for that matter) DAR's manual pages are quite good.


I also have the complete dar man page and dar -h page saved as text files.

   -x		extracts files from the archive
 YES, I want this
   -R <path>	filesystem root directory (current dir by default)
 YES, I want this, but not root dir, /home

So the time came:

First I used DAR with the -l option, it's there:
```

[Saved]       [     ]   -rw-r--r--   bruloo     bruloo  98      Fri Oct 12 16:33:46 2007        .gworldclock
[Saved]       [-----]   drwxr-xr-x   bruloo     bruloo  0       Thu Jan 24 19:58:06 2008        .conkyscripts
[Saved]       [  69%]   -rw-r--r--   bruloo     bruloo  5452    Thu Jan 24 19:58:06 2008        .conkyscripts/conkymain
[Saved]       [  66%]   -rw-r--r--   bruloo     bruloo  4937    Wed Jan 23 19:31:30 2008        .conkyscripts/conkytest
[Saved]       [  62%]   -rw-r--r--   bruloo     bruloo  3152    Wed Jan 23 20:20:45 2008        .conkyscripts/conky_top_left
bruloo@bruloo:~$
```
But I see:
```
[Saved]       [Worse]   -rw-r--r--   bruloo     bruloo
```
on some files.  What does "Worse" mean?

OK, time to do this:
```

bruloo@bruloo:~$ dar -x /media/sdb1/backup/24Jan08/bruloo-master-archive -R /home
File ownership will not be restored as dar is not run as root. to avoid this message use -O option [return = OK | Esc = cancel]
Escaping...
Aborting program. User refused to continue while asking: File ownership will not be restored as dar is not run as root. to avoid this message use -O option
bruloo@bruloo:~$

```
No good, I need the ownership permissions.
So I tried this:
```

bruloo@bruloo:~$ sudo dar -x /media/sdb1/backup/24Jan08/bruloo-master-archive -R /home
Password:
/home/.wesnoth/cache/game.cfg-cache-v1.2.3-MEDIUM-NORMAL.checksum is about to be overwritten, OK ? [return = OK | Esc = cancel]
Escaping...
/home/.wesnoth/cache/game.cfg-cache-v1.2.3-TUTORIAL.checksum is about to be overwritten, OK ? [return = OK | Esc = cancel]
Escaping...
/home/.wesnoth/cache/game.cfg-cache-v1.2.3-TUTORIAL is about to be overwritten, OK ? [return = OK | Esc = cancel]

```

I closed out Terminal at this point after hitting [Esc], don't want to have to do that a few thousands times.
Checking DAR Help:
```
   -w              don't warn before overwriting files
   -wa             don't warn before overwriting and removing files
```
OK, that takes care of having to hit [OK] a few thousand times, lets continue:

DAR MAN Page:
```
       -w, --no-warn       Do  not  warn  before  overwriting  file or slice. By default (no -n and no -w) overwriting is allowed but a warning is issued
                           before proceeding. This option may receive &#8217;a&#8217; as argument:

       -wa, --no-warn=all  This implies the -w option, and means that over avoiding warning for file overwriting, DAR also avoid signaling a  file  about
                           to  be  removed  when  its  type  is  not the expected one. File are removed when they have been recorded as deleted since the
                           archive of reference. At restoration of the differential archive, if a file of the given name exists, it is remove, but if the
                           type  does  not  match the file that was present at the time of the archive of reference (directory, plain file, fifo, socket,
                           char or block device, etc.), a warning is normally issued to prevent the accidental removal of data that was not saved in  the
                           backup of reference. (See also -k option)
```
So will:
```
sudo dar -x /media/sdb1/backup/24Jan08/bruloo-master-archive -R /home -wa
```
do the trick?

**Oopps!**
Something else I have to ask before I do this (because I just noticed):

Today I'm: bruloo@bruloo
Yesterday I was: bruloo@The Team

Will this make a difference?

If it does, I'll have to re-install again, if not I'll leave it. :)

Thanks for your input
Bruce

EDIT: Are there no DAR users out there that can help?

---

### Post by dstew on 2008-01-26
I am not a DAR user, but I read your post because I saw you had no replies. I think your proprosed command is correct. I don't think your new user name will matter. However, I am curious about the files in your /home that would be overwritten. Are those configuration files in your clean Feisty install? Or, did you install Gutsy? I have Feisty, and I don't see any .wesnoth directory in my home folder.

---

### Post by Bruce M. on 2008-01-26
> **dstew said:**
> I am not a DAR user, but I read your post because I saw you had no replies. I think your proprosed command is correct. I don't think your new user name will matter. However, I am curious about the files in your /home that would be overwritten. Are those configuration files in your clean Feisty install? Or, did you install Gutsy? I have Feisty, and I don't see any .wesnoth directory in my home folder.

I was/am using Feisty.  This is a clean install, well I added HUBackup so I could restore which didn't work, then I installed Thunar (like it better than Nautilus) so I could navigate to my second HD where I've put everything regarding DAR and my searching last night.

So I will want everything in this clean, bare bones Ubuntu  /home overwritten.

Wesnoth is a game I install, but haven't had time to play.  :(

OK, going to do that now. {taking a deep breath} ... if it dosen't work due to the name change, I'll have to re-install again.

Will respond when I'm done.
That's for the reply
Bruce.

---

### Post by Bruce M. on 2008-01-26
Today I'm: bruloo@bruloo
Yesterday I was: bruloo@The Team

It didn't work, files are "owned by:  bruloo (The Team)

Gotta try something else.  :(

---

### Post by Bruce M. on 2008-01-27
Solved, found my own answer, but it's late, been a very very long day and I need to sleep.

Will post results in about 10 hours.

Night all
Bruce

---

