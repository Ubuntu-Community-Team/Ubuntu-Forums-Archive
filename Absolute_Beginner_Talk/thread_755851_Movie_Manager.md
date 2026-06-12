---
title: "Movie Manager"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by abhiroopb on 2008-04-15
I recently ripped my entire movie collection onto my hard drive (about 100 titles). Now I would like something similar to amarok to manage all these.

I came across this: [http://www.gcstar.org/](http://www.gcstar.org/), but it seems I have to add each one by hand.

Basically I want something that scans my external hard drive, sees that I have movie X, movie Y, movie Z. Looks up the information for it on IMDB (or wherever) and displays it nicely. So, that when I click on it, it automatically launches vlc/smplayer so  that I can comfortably watch it.

I don't REALLY need this, so that is why I am not going to waste my time adding all the information by hand.

---

### Post by philinux on 2008-04-15
[http://linux.softpedia.com/get/Multimedia/Video/MeD-s-Movie-Manager-6486.shtml](http://linux.softpedia.com/get/Multimedia/Video/MeD-s-Movie-Manager-6486.shtml)

---

### Post by abhiroopb on 2008-04-15
I installed it and ran it using the java jar option. Now I have to create a mysql database. I have NO idea how to do this. Please help!

---

### Post by aeiah on 2008-04-15
you dont need a mysql database unless you're going to be accessing it over your network. their website suggests using HSQLDB for beginners.

[http://xmm.sourceforge.net/](http://xmm.sourceforge.net/)

---

### Post by abhiroopb on 2008-04-15
thanks was perfect! How do I get it to play a movie in either smplayer or vlc?

---

### Post by zombiepig on 2008-04-18
> **abhiroopb said:**
> 
Basically I want something that scans my external hard drive, sees that I have movie X, movie Y, movie Z. Looks up the information for it on IMDB (or wherever) and displays it nicely. So, that when I click on it, it automatically launches vlc/smplayer so  that I can comfortably watch it.


The next version of gcstar has this feature, but you'd need to wait for a release (probably a few weeks off), or run a daily snapshot. Lemme know if you want to try it and I'll give you instructions :)

---

### Post by abhiroopb on 2008-04-18
I am using Med's Movie Manager. And honestly this app does everything and more. It can even generate very nice looking lists. Not much more I could really ask for. Quite satisfied with it. A couple of isses with it.

1. If I change the file name it doesn't change in the database. So if I have move XYZ.avi on the database and on the database it is called ABC, and then I change XYZ.avi to ABC.avi, I will have to relink the file (this is only really so that the movie plays correctly).

2. I should be able to choose different players for different movies (as smplayer doesn't work for all movies).

3. Like Amarok it should constantly keep scaning the directory. I scanned it the first time, but now if I scan it again ALL the files get added again, which is really annoying. So after the first scan I have to add each one individually. Which is fine really, but an update of this would be nice.

4. When the IMDB info is retrieved a preview of that information would be nice (before selecting the file). As there are often remakes of a film, and its sometimes difficult to remember.

5. Support for more formats (specifically: mkv)

6.. Lastly its a java app so ts a bit weird and laggy, but I guess it works cross platform (would it  be really hard to write an ubuntu program for this? I have NO knowledge whatsoever in this department!)



I don't know about gcstar (as it didn't scan the folder) so I took a look at it, and it looks like it does the same thing. So Med's is great. Many thanks tot he creator!

---

