---
title: "How do I install Dvd-slideshow from the subversion repository"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by Grafster on 2007-03-08
Been working on my wedding slideshow and I'm almost done.

I've been working with [dvd-slideshow]("http://dvd-slideshow.sourceforge.net/wiki/Release_0.8.0") over the past few weeks. It's generally a great program.
Unfortunately there was a [bug]("http://sourceforge.net/tracker/index.php?func=detail&aid=1674572&group_id=100188&atid=626615"). :( 
But hardworking open source programmers fixed it. And posted a responce in the bug area telling me about it. :) 

But it's not in the normal download area, instead it's in a [subversion repository]("http://svn.sourceforge.net/viewvc/dvd-slideshow/") (or SVN code if they aren't the same)....
I've been trying for the past few days but I can't seem to figure out how to install.

(And I know that I'm not supposed to be posting plez-help-me-install in the bug tracking area for dvd-slideshow -- I assume they're doing whatever they do to try to make the code availible to everyone anyway).

So I come to the collective wisdom of the ubuntu forums for aid. (My wife will be really happy if I can get this fixed...)

---

### Post by o_fortuna on 2007-03-08
Open up a terminal (Applications--Accessories--Terminal) and paste in these commands:
```
sudo apt-get updtate
sudo apt-get install subversion
svn co https://svn.sourceforge.net/svnroot/dvd-slideshow dvd-slideshow-svn
```
That will download it to your home directory under dvd-slideshow-svn. Then just:
```
cd dvd-slideshow-svn/
./dvd-slideshow
```
To run it.

---

### Post by Grafster on 2007-03-10
This worked brilliantly. Thanks very much!
(the Subverision code fixed the problems too. Wife says "we're done")

Much obliged!

---

