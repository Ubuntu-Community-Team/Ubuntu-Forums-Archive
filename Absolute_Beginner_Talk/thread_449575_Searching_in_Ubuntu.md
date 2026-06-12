---
title: "Searching in Ubuntu"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by zhinker on 2007-05-20
What's the best program to search for files in Ubuntu?  The build in search function seems to reallysuck.

---

### Post by Kobalt on 2007-05-20
I like [Beagle]("https://help.ubuntu.com/community/Beagle"), but you can also try [Tracker]("https://help.ubuntu.com/community/MetaTracker").

---

### Post by taurus on 2007-05-20
What are you searching?  You can do it from a terminal with the find command.

```
sudo find / -name **filename** -print
```

---

### Post by earobinson on 2007-05-20
beagle is very popular [http://www.gnome.org/projects/beagle/](http://www.gnome.org/projects/beagle/)

---

### Post by empthollow on 2007-05-20
my personal favorite is the gnome search tool located in the places menu, it may take a little longer than beagle but it will find your file every time.

---

### Post by zhinker on 2007-05-20
do they also search for folders?  Because the lack of it has been my main complaint about the search programs I've found so far.

---

### Post by Kobalt on 2007-05-20
Beagle and Tracker will search into folders and even inside some type of documents.

---

### Post by zhinker on 2007-05-20
> **Kobalt said:**
> Beagle and Tracker will search into folders and even inside some type of documents.
But will they search for the folder name itself as well?  If I try to search for 'pictures' would a folder called 'pictures' be included in the results?

---

### Post by NT4usB on 2007-05-20
```
$ locate filename
```
will find all instances of a filename (folder or otherwise) and show the path to that filename.
wildcards will expand the search.
```
$ locate filen*
```
will find anything starting with filen

If you've just added stuff and want to search for it, run:
```
 $sudo updatedb
```
to update the database before you search so locate will find the new stuff.

---

### Post by Kuoi on 2007-05-30
> **empthollow said:**
> my personal favorite is the gnome search tool located in the places menu, it may take a little longer than beagle but it will find your file every time.

Well THIS was what I needed !!!

I've used Beagle , but that made my computer many times crashing, when it was indexing the files.
I've uninstalled it after about 5 times crashing.

I've installed Tracker now , but can't find much with it.

For example : I was searching "usplash" files today and didn't found anything with Tracker.
It is installed for many weeks now , so if it index anything , I can't see it.

I was looking for a good search tool because of the "usplash" problem today , and found your message.
I didn't even know I had this on my computer , ... not that it is hidden , but at "places" , I only look for places.

I've tried it  , and it found as much "usplash" files as there are on my computer . GREAT !

Many many thanks for this tip !!!!!!!

Kuoi

---

### Post by wyth on 2007-06-06
I've just ditched Beagle for Tracker, and am impressed. It's still under development, so to get some of the features you expect in Beagle it takes a wee bit of config file hacking, but nothing major. 

Kuoi: To make Tracker index/search more than your /home/*name* folder, you need to adjust the tracker.cfg file.  That's in /home/*name*/.Tracker/tracker.cfg.  Right near the top is the list of places you are indexing, and you can add to it.

Other features that are pretty keen: It's a lot lighter than Beagle, and in the above-mentioned config file (tracker.cfg), you can set Tracker to throttle its indexing at any desired speed.  There is also built-in nautilus support (need to get a deb for that), and a metadata tagging feature under development.  That's availabe at the command line, but I'm still working out how to get that graphically added into Nautilus (it's possible).  There's also deskbar integration.

Beagle drove my laptop into the ground.  The fan woke me up more than once at night when Beagle throttled its indexing whenever the machine was idle, and just kept at it for hours.  Tracker's much lighter on resources and indexes things lickety-split.

---

### Post by neorou on 2007-06-12
Is beagle included in server? I'm migrating over to ubuntu server from os x and openBSD, but came over with little expertise other than LAMP related stuff.

I'm trying to create a mechanism by which people can dump large number of PDF and Word files and have an automated system that indexes the file, much akin to what Beagle does on the desktop. OS X has spotlight plug-in for the server edition and it works fairly well. Unfortunately, I would have to continue using OS X.

I would like to get access to the beagle database list and integrate it with PHP and create query portals for users to find the literature in this 'digital library'.

Any advice?

---

### Post by wyth on 2007-06-12
Neither Beagle nor Tracker are automatically included, but they're both there in the repositories (and you could probably hook into either database).  It's just an apt-get away. 

I *think *[Tracker]("http://www.gnome.org/projects/tracker/index.html") will do what you're looking for.  At least the documentation there talks about its API and how developers can create tools using Tracker as the back end.  Might be worth a look.  I can't speak for Beagle, since I dumped it.

---

