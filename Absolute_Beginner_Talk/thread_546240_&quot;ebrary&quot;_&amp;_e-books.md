---
title: "&quot;ebrary&quot; &amp; e-books"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by the badger on 2007-09-08
i've just started college (again) and while browsing the school's library came across an e-book i've been wanting: ubuntu linux for non-geeks. i was delighted until i realised that the software used to view these resources is aparently incompatible with ubuntu (oh, the irony!).
i've found some instructions on [installing IE for linux]("http://www.rubyrailways.com/install-internet-explorer-on-ubuntu-dapper-in-3-easy-steps/"), but i'm curios if anyone else has run into the same issue and found any alternate solutions?
the website in question is [http://www.ucfv.ca/library.htm]("http://www.ucfv.ca/library.htm"). any feedback is great!

---

### Post by oilchangeguy on 2007-09-08
the website loads fine with ff. but of course i don't have an id. so i can't get into the ebooks.

---

### Post by bodhi.zazen on 2007-09-08
What kind of file are you trying to open ? is it a .chm ?

If so you need a .chm viewer, I line xchm

sudo apt-get install xchm

---

### Post by the badger on 2007-09-08
> **bodhi.zazen said:**
> What kind of file are you trying to open ? is it a .chm ?

If so you need a .chm viewer, I line xchm

sudo apt-get install xchm

i don't know what type of file it is. it's not a help file, and wikipedia is telling me .chm is for ms helpfiles.

when i've logged in and try to view the contents of the book that i'm told i'm missing a plugin which, upon search, is "unknown plugin (application/x-edf)". from what i understand the plugin is the [ebrary brand "reader"]("http://site.ebrary.com/lib/anysite/support/2_support01.jsp#005"), which is apparently only available for windows and (sometimes) mac. 
just wondering if anyone else has run into this?

---

### Post by SpiritIsReality on 2007-09-08
howdy
could try a different route
[http://ubuntuforums.org/showthread.php?t=484846](http://ubuntuforums.org/showthread.php?t=484846)
free linux books online

trails

---

### Post by randcoop on 2007-09-09
The ebrary plugin is for Windows at the moment (Ebrary says that it will have a plugin for Linux later this year).  But it works quite well using wine.

If you know how to use wine, you can just install ebrary that way.  If you don't know what I'm talking about, you may want to look at Crossover, a commercial software that makes wine very easy to use.  Look at [http://www.codeweavers.com]("http://www.codeweavers.com").  Crossover includes the ebrary reader as one of the programs that are covered by default.

---

