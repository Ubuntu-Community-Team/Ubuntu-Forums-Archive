---
title: "[SOLVED] Add/Remove Applications"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by geonerd on 2007-12-27
I am running 7.10 (just installed it yesterday) on my Toshiba Satellite U205-5057 laptop. 

I would like to add a few programs via Applications -> Add/Remove; however, when I attempt to do so i get the following error:

"<Application> cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type."

How do i get these programs to install (i'm starting with InkScape and Xchat).

Here are the specs for the laptop:
[http://reviews.cnet.com/laptops/toshiba-satellite-u205-s5057/4507-3121_7-32327351.html](http://reviews.cnet.com/laptops/toshiba-satellite-u205-s5057/4507-3121_7-32327351.html)

Thanks for your help

---

### Post by mtaylor314 on 2007-12-27
I would try to alternative to add/remove programs.  Go to System --> Administration --> Synaptic Package Manager.  Under Tools --> Repositories, go through and make sure you have some to search, and then search for xchat or whatever it is.  Hopefully, that´ll work for you.  If not, go to a terminal and type sudo apt-get install xchat

---

### Post by iris-n on 2007-12-27
There are in fact a few programs that aren't supported by the i386 architecture.
You should look for an alternative, through Synaptic or apt-cache search.

Now, if this happens in every program you try to install, you do have a problem.

In my machine (i386 as well), XChat installed without problems.

---

### Post by mikewhatever on 2007-12-27
That error message usually shows up when a repository you try to download from is unavailable. Check your Software Sources and make sure Universe and Multiverse are chosen. If it still does not work, post you sources list.
 <sudo cat /etc/apt/sources.list>

---

### Post by as0l0 on 2007-12-27
take a look at this thread where it's a known issue with a quick fix.

[http://ubuntuforums.org/showthread.php?t=648728](http://ubuntuforums.org/showthread.php?t=648728)

---

### Post by geonerd on 2007-12-28
Got everything working now... just had to select multi/universe as mikewhatever suggested.  It was indeed a quick fix.

Thanks for helping a noob chick out (:

---

### Post by SOULRiDER on 2007-12-28
Thats what the people int he forums are for :)
Also, would you please markt he thread as solved under the Thread Tools menu? Thank you!

---

