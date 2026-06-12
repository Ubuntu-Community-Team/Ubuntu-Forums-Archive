---
title: "sychronize files between usb and hard drive"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by da Wookiee on 2008-04-07
I currently have mp3 and gnucash files on a usb drive to make them portable between my windows and linux boxes.  This worked until I unmounted and remounted the usb drive.  Now rhythmbox's and gnucash's mapping to the files is all messed up and prompts me to go hunting for the files each time.  No big problem, but it is a hassle.  

What I'm looking for is synchronization options that will allow me to keep the files on my hard drive, but when the usb is plugged in will check to make sure they are backed up on the usb in case anything goes wrong.  

The computer is turned off when not in use.

---

### Post by njparton on 2008-04-08
rsync is the best (quickest) way to synchronise files between 2 locations.
 
To get you started, install it:
 
```
sudo apt-get install rsync
```
 
then get the daemon running:
 
```
sudo /etc/init.d/rsyncd start
```
 
then from the command line it's easy to sync 2 directories:
 
```
rsync /source_dir /dev/destination
```
 
there are lots of other options that go with it and/or to set up an rsync server, there's loads of information out there if you're prepared to do some searching and reading :)

---

### Post by da Wookiee on 2008-04-08
When I tried to start the daemon, (even tried cutting and pasting) I got the following error.

```

sudo: /etc/init.d/rsyncd: command not found

```

What now?

---

### Post by Cadmus on 2008-04-08
> **da Wookiee said:**
> When I tried to start the daemon, (even tried cutting and pasting) I got the following error.

```

sudo: /etc/init.d/rsyncd: command not found

```

What now?

For basic synchronisation you don't need the demon, so you can go read up about it before trying to use it. Using rsync straight from the command line will do you for now I'd say.

The documentation I've found for rsync is a little thorny, but the basic mode of operaton that's worked for me is:

```
rsync -avP /path/to/source /path/to/destination
```

Which translates like this
```
-a, --archive               archive mode, equivalent to -rlptgoD
-v, --verbose               increase verbosity
-P                          equivalent to --partial --progress

```

'-a' Expands to:
```

-r, --recursive             recurse into directories
-l, --links                 copy symlinks as symlinks
-p, --perms                 preserve permissions
-t, --times                 preserve times
-g, --group                 preserve group
-o, --owner                 preserve owner (root only)
-D, --devices               preserve devices (root only)

```

and '-P' Expands to:
```
--partial               keep partially transferred files
--progress              show progress during transfer

```

**WHICH TRANSLATES TO:**
It does the whole directory and everything below it, keeps all the permissions and modification times on the files, gives you lots of feedback (including how far it is on a given file) and it's quicker to restart it if it gets interrupted.

As I said, not a very simple program, but very powerful.

---

### Post by njparton on 2008-04-08
It is very simple when used from the command line but not necessarily when using the daemon/setting up a server. I gave up on that and now I just have a bash script containing several lines of rsync commands. It backs up 4 email accounts across my home network and executes in < 2 secs usually.
 
Great program in my book :)

---

