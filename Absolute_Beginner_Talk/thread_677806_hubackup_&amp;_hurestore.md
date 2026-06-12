---
title: "hubackup &amp; hurestore"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by snakra on 2008-01-25
Hello,

A funny one! Help

I've just upgraded from 7.04 to 7.10.

I've used hubackup to backup onto an external hard disk and this was fine.

I then tried to restore usung hurestore just to see that all was well - but when I started - or rather, tried to start hurestore nothing happens at all.

Any ideas?

Thanks

SN

---

### Post by Bruce M. on 2008-01-27
> **snakra said:**
> Hello,

A funny one! Help

I've just upgraded from 7.04 to 7.10.

I've used hubackup to backup onto an external hard disk and this was fine.

I then tried to restore usung hurestore just to see that all was well - but when I started - or rather, tried to start hurestore nothing happens at all.

Any ideas?

Thanks

SN

I posted a Tips & Tutorials page today, not yet authorized, so I'll post it here for you in it's entirety:

HowTo: Restore HUBackups when HURestore doesn't!


I used HUBackup for months.

One thing is didn't allow it to do was created the backups in the /home folder. Which to me makes sense, because if you loose the /home folder, you loose the backups too.

HUBackup uses by default; ~/.hubackup-data/
~ = /home
/.hubackup-data = hidden folder ( the . )

So I put my backups on my second drive (another partition would be good) like this:

 /backups/23Nov2007/ <<-- deleted when I created  /04Jan2008/
bruloo-master-archive.1.dar
bruloo-master-catalog.1.dar

 /backups/07Dec2007/ <<-- deleted when I created  /18Jan2008/
bruloo-master-archive.1.dar
bruloo-master-catalog.1.dar

 /backups/21Dec2007/ <<-- deleted when I created  /24Jan2008/
bruloo-master-archive.1.dar
bruloo-master-catalog.1.dar

 /backups/04Jan2008/
bruloo-master-archive.1.dar
bruloo-master-catalog.1.dar

 /backups/18Jan2008/
bruloo-master-archive.1.dar
bruloo-master-catalog.1.dar

 /backups/24Jan2008/
bruloo-master-archive.1.dar
bruloo-master-catalog.1.dar

keeping three just to be sure.  I don't trust incremental backups because of bad experiences with them in the past.

On 25 Jan 2008 I moved my /home to it's own partition and was going to make a new backup when of all things, **I** inadvertantly deleted my new /home and had to reinstall.

OK time to runs HURestore (after getting HUBackup again), HURestore does NOT even open!
I was up all night searching for an answer, when I found this:

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


Then I got the DAR Man Page and the DAR Help page and saved to a file.

So after a lot of researching, asking questions and trial and error I found that this restored my /home (somewhat - some things are missing, easy to fix)

**NOTE:** DAR is used in Terminal ( > Applications > Accessories > Terminal )

Lets check the archive first:
```
bruloo@bruloo:~$ dar -l /media/sdb1/backup/24Jan08/bruloo-master-archive

```
Ok, page after page scrolled by ending with:
```
[Saved]       [  69%]   -rw-r--r--   bruloo     bruloo  5452    Thu Jan 24 19:58:06 2008        .conkyscripts/conkymain
[Saved]       [  66%]   -rw-r--r--   bruloo     bruloo  4937    Wed Jan 23 19:31:30 2008        .conkyscripts/conkytest
[Saved]       [  62%]   -rw-r--r--   bruloo     bruloo  3152    Wed Jan 23 20:20:45 2008        .conkyscripts/conky_top_left
bruloo@bruloo:~$
```
Good the files are there, now to get them.
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
/home/.wesnoth/cache/game.cfg-cache-v1.2.3-TUTORIAL.checksum is about to be overwritten, OK ? [return = OK | Esc = cancel]
Escaping...
/home/.wesnoth/cache/game.cfg-cache-v1.2.3-TUTORIAL is about to be overwritten, OK ? [return = OK | Esc = cancel]

```

I closed out Terminal at this point after hitting [Esc], [Esc], [Esc], don't want to have to do that a few thousands times hitting [Return].

DAR Help:
 -x = extract
 -R = <path> filesystem root directory (current dir by default)
 -wa = don't warn before overwriting and removing files
 -v = verbose (you'll see it working)

So here's the code that worked for me in Terminal:
```
bruloo@bruloo:~$ sudo dar -x /media/sdb1/backup/24Jan08/bruloo-master-archive -R /home/bruloo -wa -v
```

Good luck with this!
Bruce

---

### Post by Christopherius on 2008-04-30
I have the same problem too.

When i used those commands i got the following message:

```
/media/Media/backup/chris-master-archive.1.dar is required for further operation, please provide the file. [return = OK | Esc = cancel]
```

not quite sure what to do here?

EDIT:

Nevermind it turns out since I installed 8.04 my disk was not mounted as "Media" anymore it was called "disk".

---

