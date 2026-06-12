---
title: "Source List - Possibly the stupidest Q"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by kristalsoldier on 2007-03-03
Hi...

I know this is probably the most stupid question...but here it goes...

Should there be only one source list (aside from a backup)  or can there be many?

I seem to have 4 source lists - all tagged by different days.

Should these multiple source lists be deleted and one source list maintained and updated?

I know i'll probably get flak for this...but its only been 8 days since i've met linux (edgy)!

(already ducking for cover!)

Thanks

---

### Post by taurus on 2007-03-03
The one that matters the most is /etc/apt/sources.list.  Others with date behind are backup copies and can be removed if you wish.

---

### Post by invalid on 2007-03-03
Typically the only sources list is /etc/apt/sources.list.

If there are multiple ones there, they are likely auto-created backups from using a program to update your repos. These are usually identified with a date they were created.

---

### Post by annda on 2007-03-03
what are the files named? as far as i can tell, only /etc/apt/sources.list is used. so ypu might as well delete the rest (except the backup files you need).

---

### Post by kristalsoldier on 2007-03-03
OK...but when I do gksudo gedit /etc/apt/sources.list in the terminal I get the following msg:

(gedit:7743): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

And then an empty editor opens up.

Why?

Thanks

---

### Post by taurus on 2007-03-03
Try

```
sudo nano -w /etc/apt/sources.list
```

---

### Post by invalid on 2007-03-03
ignore this reply, sorry

---

### Post by kristalsoldier on 2007-03-03
> **annda said:**
> what are the files named? as far as i can tell, only /etc/apt/sources.list is used. so ypu might as well delete the rest (except the backup files you need).

They are named as follows:

sources.list.save
sources.list.save1
sources.list.save 2
sources.list.save 3
sources.list ~
sources.list_backup

And there is a folder which is labeled: sources.list.d

---

### Post by kristalsoldier on 2007-03-03
> **taurus said:**
> Try

```
sudo nano -w /etc/apt/sources.list
```

When I do the above...I get the foll:

GNU nano 1.3.12          File: /etc/apt/sources.list 

The rest is blank!

---

### Post by taurus on 2007-03-03
What's the output of this command then?

```
ls -la /etc/apt
```

---

### Post by kristalsoldier on 2007-03-03
> **taurus said:**
> What's the output of this command then?

```
ls -la /etc/apt
```

total 56
drwxr-xr-x   4 root root 4096 2007-03-03 22:08 .
drwxr-xr-x 108 root root 4096 2007-03-03 21:32 ..
drwxr-xr-x   2 root root 4096 2007-02-28 16:00 apt.conf.d
-rw-------   1 root root    0 2006-10-25 14:27 secring.gpg
-rw-r--r--   1 root root 1878 2007-03-02 21:40 sources.list~
-rw-r--r--   1 root root 1967 2007-03-03 21:26 sources.list_backup
drwxr-xr-x   2 root root 4096 2006-09-28 00:44 sources.list.d
-rw-r--r--   1 root root 1878 2007-03-03 21:26 sources.list.save
-rw-------   1 root root 1579 2007-02-28 15:50 sources.list.save.1
-rw-------   1 root root 1577 2007-02-28 22:42 sources.list.save.2
-rw-------   1 root root 1577 2007-02-28 22:45 sources.list.save.3
-rw-------   1 root root 1704 2007-03-01 13:42 sources.list.save.4
-rw-------   1 root root 1200 2006-10-25 14:27 trustdb.gpg
-rw-r--r--   1 root root 2393 2006-10-25 14:27 trusted.gpg
-rw-r--r--   1 root root 2381 2006-10-25 14:27 trusted.gpg~

---

### Post by taurus on 2007-03-03
I guess "gksudo gedit /etc/apt/sources.list" somehow screwed up the name.

```
sudo cp /etc/apt/sources.list~  /etc/apt/sources.list
sudo nano -w /etc/apt/sources.list
```

---

### Post by kristalsoldier on 2007-03-03
> **taurus said:**
> I guess "gksudo gedit /etc/apt/sources.list" somehow screwed up the name.

```
sudo cp /etc/apt/sources.list~  /etc/apt/sources.list
sudo nano -w /etc/apt/sources.list
```

This is now what I get...

## Uncomment the following two lines to fetch updated software from the network
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restric$
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe
                               [ Read 38 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

---

### Post by taurus on 2007-03-03
Well, that's your /etc/apt/sources.list.  If you want to save and exit, do <Ctrl>o and <Ctrl>x.  And if you want to add more repos to it, then here is one.

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by kristalsoldier on 2007-03-03
Is this what it should look like? If I want to add other sources, is this where I should be doing this?

---

### Post by taurus on 2007-03-03
> **kristalsoldier said:**
> Is this what it should look like? If I want to add other sources, is this where I should be doing this?

If you want to add more repos, just add them to the end of the file so you can keep track of stuff you add in by hand.

---

### Post by kristalsoldier on 2007-03-03
Oops...seems like we were posting simultaneously!

OK...thanks. So, if I want to edit the source list for whatever reason, I use the command that you mentioned last. What then is the role/ function of the gedit command...the one that sends me to the blank text editor?

---

### Post by taurus on 2007-03-03
Gedit is a GUI text editor (just like Notepad in Windows if you want to think it that way) while nano is a terminal editor.

---

### Post by kristalsoldier on 2007-03-03
So...depending on one's preferences, one can use either? Net effect remains the same? Lastly, why then was I being moved to a blank text editor when using the gedit command given that there is a (what I presume to be) an operational sources list as I discovered using the nano command that you showed me?

Thanks

---

### Post by annda on 2007-03-03
you didn't have sources.list at all (it got lost somehow). you had a backup file named sources.list~

taurus helped you overwrite / create the file sources.list.

if you try to open/edit a file that does not exist (see the gedit case) the editor creates a blank file for you.

---

### Post by kristalsoldier on 2007-03-03
> **annda said:**
> you didn't have sources.list at all (it got lost somehow). you had a backup file named sources.list~

taurus helped you overwrite / create the file sources.list.

if you try to open/edit a file that does not exist (see the gedit case) the editor creates a blank file for you.

You know...I am a tubelight! Yes, of course...hit me right now!

Thanks folks...you've been a great help!

---

### Post by AndyCooll on 2007-03-03
And remember, after each modification of your sources.list to update the details by:
```
sudo aptitude update
```

:cool:

---

### Post by kristalsoldier on 2007-03-03
> **AndyCooll said:**
> And remember, after each modification of your sources.list to update the details by:
```
sudo aptitude update
```

:cool:

Yup...got that. Thanks!

---

