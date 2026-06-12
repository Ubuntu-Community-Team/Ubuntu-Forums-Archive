---
title: "Nautilus file search not working"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by domtom on 2008-03-22
I recently did a clean install of Ubuntu 7.10 having failed to get Kubuntu to upgrade from 7.04 to 7.10. So far I like it a lot but I am having trouble with Nautilus file searches.

For example, in my home folder I have a folder of movies with .mpg extension. Yesterday I tried to search for mpg (or *.mpg) and it returned a few files that contained mpg and one file called mpg.dll but no files with an mpg extension. Today it has found some files with .mpg.png extension (image files associated with the movie files) but still no .mpg files.

If I double click on a file with mpg extension it first of all magically changes its
extension to 'TeX font metrics' (?) and then says it cannot be opened because no application is known for this kind of file!

Can anyone suggest what is going on.

Thanks.

---

### Post by (((X))) on 2008-03-22
What happens when you link this type of file to other application?

---

### Post by jan quark on 2008-03-22
taken from the manual
```

man trackerd
```

> Help Options:
  -?, --help                      Show help options

Application Options:
  -e, --exclude-dir=/PATH/DIR     Directory to exclude from indexing
  -i, --include-dir=/PATH/DIR     Directory to include in indexing
  -c, --crawl-dir=/PATH/DIR       Directory to crawl for indexing at start up only
  -n, --no-indexing               Disable any indexing or watching taking place
  -v, --verbosity=VALUE           Value that controls the level of logging. Valid values are 0 (displays/logs only errors), 1 (minimal), 2 (detailed), and 3 (debug)
  -t, --throttle=VALUE            Value to use for throttling indexing. Value must be in range 0-20 (default 0) with lower values increasing indexing speed
  -m, --low-memory                Minimizes the use of memory but may slow indexing down
  -s, --initial-sleep             Initial sleep time, just before indexing, in seconds
  -l, --language=LANG             Language to use for stemmer and stop words list (ISO 639-1 2 characters code)
  -R, --reindex                   Force a re-index of all content
  -f, --fatal-errors              Make tracker errors fatal

perhaps you have to include the home directory into the trackerd index with
```

sudo trackerd --include-dir=/home
```

---

### Post by domtom on 2008-03-22
> **(((X))) said:**
> What happens when you link this type of file to other application?

How do I do that? If I right click the file and say 'Open with "Movie Player" for example, it works fine.

I have also discovered that if I use* Places -> Search for files...* it works correctly. Its only Nautilus that seems to be giving odd results.

---

### Post by onuca on 2008-03-22
Hi!

Same problem in here! Nautilus file search completely doeasn't work unless I'll go to Places - search for files...

Very weird!

I did run sudo trackerd --include-dir=/home

and that is what I've ended up:


Tracker version 0.6.3 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at [http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Initialising tracker...
Throttle level is 0
ERROR: tracker_dbus_init() could not get the session bus
DBUS ERROR: org.freedesktop.DBus.Error.NoReply occurred with message Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
process 23279: arguments to dbus_connection_register_object_path() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 5280.
This is normally a bug in some application using the D-Bus library.

Any ideas?? It is driving me crazzzzzyyyyyy - HELP PLEEEEAAAASSSSEEEEE!!!!!!

---

### Post by domtom on 2008-03-22
Tracker seems to be the issue - I see a lot of problems from other users. Why something so flawed has got into version 7.10 (Seven!) I have no idea but it seems 

it can be disabled - go to *System->preferences->sessions* and un-tick tracker. 
In the meantime 'Search for files...' from the *Places* menu works fine.

While I am complaining, there are other things I don't like about Nautilus -

1) Its CD/DVD creator jumps in every time you insert a blank CD and stops other applications from seeing the blank media, plus it seems there are no controls to its CD/DVD burning, such as how do I create a multi-session disk?

2) It doesn't have tabs, which having come from konqueror is a downer.

My view is that Ubuntu owes itself a  better default file manager.

---

### Post by (((X))) on 2008-03-22
so you want to  have tabbed file manager?
[http://pcmanfm.sourceforge.net/](http://pcmanfm.sourceforge.net/)

---

### Post by (((X))) on 2008-03-22
k3b is a good burning program I prefer it anyway.

---

