---
title: "Can you improve the search tool, or if not, is there one that works?"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by PiggiePaul on 2008-02-22
I've noticed the Search Tool, under the PLACES menu, called SEARCH FOR FILES is actually rubbish.

I was browsing through folders, and could see some filenames in front of me.
I then get this search tool to find the file, (entire filesystem) but it can't find the files. :confused:

So, as it clearly (for whatever reason) does not find things.

Can you change it's settings to it really does find things?

Or if not, is there a proper search tool that will find anything (file) on your system, even if you type part of the search word?

Thanks.

---

### Post by spiderbatdad on 2008-02-22
You could try```
locate name
``` from the terminal.
Or open synaptic package manager and use the "search" tool near the top of the window...input "search files" and it will offer you a number of programs to browse...like doodle.

---

### Post by nick_h on 2008-02-22
The *locate* command and the search in the places menu relies on a database.  This can be updated with the *updatedb* command.

You could also try the *find* command which doesn't use a database.  Also have a look at *grep* if you are interested in the contents of files.

---

### Post by PeterJS on 2008-02-22
Point of interest, in light of this tread I went and ran a few experiments with locate, and it doesn't seem to want to index ntfs (it might just be a function of being in /media/, rather than FS), drives. Using:
```

sudo locate -U /media/sda1

```
I forced it to build a database of that drive, which worked well except it over wrote the database describing my root file system.
I tried:
```

sudo locate -U /media/sda1 -u

```
to try to get it to index both, it didn't work, I just got the ntfs drive. I'm going to try:
```

sudo locate -U /media/sda1 -U /

```
next and see if that produces a workable DB.
The search tool in the places menu is just a graphical front end to locate.

---

### Post by erginemr on 2008-02-22
You can give catfish a try, which has a nice GUI and acts as a frontend to find, locate and slocate:
[http://www.getdeb.net/app/catfish](http://www.getdeb.net/app/catfish)

---

### Post by PeterJS on 2008-02-22
No luck.
```

sudo locate -U /media/sda1 -U /

```
only indexed my root drive but not /media/sda1

---

### Post by PeterJS on 2008-02-22
Got it. In /etc/updatedb.conf one of the first configuration options is which portions of the FS should be pruned from the locate database, if there's anything in there you want search your should probably remove it from the exclusions list.

---

### Post by superprash2003 on 2008-02-22
Google Desktop is an awesome search tool... gives results very quickly!!

---

### Post by PiggiePaul on 2008-02-23
Just wanted to thanks to all of you for your suggestions to my SEARCH question.

I don't know why it's so hard by default as I've always been used to (in Windowz even from Windows 95, having a search tool that could could just type in some words (or wildcards) and it did a true search of the whole hard drive and showed you the results, which (although not pretty sometimes) did allow you to find the bits you wanted.)

I know Vista (sorry for saying that word) does index things, not quite sure how that works, apart from the fact it seems to want to kill your hard drive all the time.

I did not realize Ubuntu does some indexing too?

But anyway, I downloaded and installed "Catfish" (Thanks for the suggestion [COLOR="Blue"]erginemr[/COLOR]) and just gave it a quick try and it does indeed seem to find a LOT more.

So, will try using this in the future when I can't find something.

Thanks again for all your help and advice :)

---

### Post by SpiderGorilla on 2008-02-23
Make sure you're not using the Deskbar Applet, but you're using "Places" >> "Search for files"... because the Deskbar Applet is absolutely useless for searching the filesystem.

---

### Post by PiggiePaul on 2008-02-23
Yep and you can see the different, using the same search word:

Picture removed as I don't know  how to do thumnails view

Perhaps someone can tell me?

---

