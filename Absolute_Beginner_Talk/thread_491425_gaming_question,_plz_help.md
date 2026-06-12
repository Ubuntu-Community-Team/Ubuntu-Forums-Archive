---
title: "gaming question, plz help"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by ITdrummer on 2007-07-03
I am trying to download and install some cool games i found online.  

One such game being: Nexuiz

The files i need to download for this game are : 
 nexuiz  (666.1 Kb)
nexuiz-data  (227.5 Mb)
 nexuiz-music  (52.4 Mb)

Once i download these to my desktop. what do i do from there?

Should it go something like this:

```
cd ~/Desktop
sudo apt-get install nexuiz nexuiz-data nexuiz-music
```

---

### Post by PartisanEntity on 2007-07-03
What kind of files are they? Do they end with .deb for example?

---

### Post by greg_g on 2007-07-03
For me, Nexuiz was just a zip file and I extracted it to a directory of my choice (~/apps) and then all I need to do is double click on "nexuiz-linux-glx.sh" and it runs.

Where did you download the files from?  I believe I did from the official site.

greg

PS: this is the file I downloaded:
[http://sourceforge.net/project/downloading.php?groupname=nexuiz&filename=nexuiz-23.zip](http://sourceforge.net/project/downloading.php?groupname=nexuiz&filename=nexuiz-23.zip)

---

### Post by rubikfreak on 2007-07-03
You don't need to go to your desktop.
From any directory, just do:
```
sudo apt-get install nexuiz nexuiz-data nexuiz-music
```
I also think that you might only need to do
```
sudo apt-get install nexuiz
```
because nexuiz-data and nexuiz-music would
probably be dependencies.

---

### Post by ITdrummer on 2007-07-03
Here is where i get my files.  It is a long  list of games.

[http://www.getdeb.net/category.php?id=3](http://www.getdeb.net/category.php?id=3)

---

### Post by greg_g on 2007-07-03
Just to make sure, where did you get those files?

Because from their official site their download page links to the one file I mentioned in my previous post.  Here is the download page:
[http://alientrap.org/nexuiz/index.php?module=downloads](http://alientrap.org/nexuiz/index.php?module=downloads)


Ok, we posted at the same time and you answered my question.

I would personally not use the debs because there is no reason to install it.  It runs fine without.  Download from the official site (my links).

I know we can probably trust getdeb.net but I like to get the official stuff from the official site just because we know it is the latest version etc.

---

### Post by ITdrummer on 2007-07-03
like the avatar btw

---

### Post by greg_g on 2007-07-03
:)

thanks

And yeah, if the debs work, use them.  Just be prepared to update when you remember.  No reason to re-download 230 megs.

---

