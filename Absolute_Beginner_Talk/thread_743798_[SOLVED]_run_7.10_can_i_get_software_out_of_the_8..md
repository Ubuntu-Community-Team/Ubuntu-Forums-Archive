---
title: "[SOLVED] run 7.10 can i get software out of the 8.04 repositors"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by &lt;&lt;joe&gt;&gt; on 2008-04-03
I would like to get a newer version of rhythmbox
so can i get it out of 8.04 's repositorys

hers why 
i have a creative zen
pain in the beeper sorry it's a nice player but pain when not sapported
it uses mtp not fully supported by the current 7.10
tried to build from sorce got mtp to compile 
and got rhythmbox to compile but it cant find librhythmbox-core <-- or something like that
when i try to run it 
so that dosent work

---

### Post by zvacet on 2008-04-03
You can download it from [here](http://packages.ubuntu.com/search?keywords=rhythmbox&searchon=names&suite=hardy&section=all),but check dependencies(marked with red ball)first.If any of them is higher version then in Gutsy you can expect problems.

---

### Post by kesman on 2008-04-03
[http://packages.ubuntu.com/hardy/](http://packages.ubuntu.com/hardy/)

You could try searching for it there, but I think it depends on some packages that are different version in 8.04 than 7.10, and those packages depend on other packages that depend on other packages that depend... and so on, so I wouldn't recommend installing anything from a repository that isn't meant for your distribution. You could try to ask for that missing stuff for compiling from rhytmbox's site or somewhere, it should be compileable.

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-04-03
no its there it is just file is there in the source i just dont know how to get it all working
i followed the instructions on this page 
[http://live.gnome.org/Rhythmbox/FAQ](http://live.gnome.org/Rhythmbox/FAQ)

work well exept when i go to run it lol
:(

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-04-03
i should not have a problem with the dependaces becuses it only had a few runtime dependances 
i think :/

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-04-03
> **zvacet said:**
> You can download it from [here](http://packages.ubuntu.com/search?keywords=rhythmbox&searchon=names&suite=hardy&section=all),but check dependencies(marked with red ball)first.If any of them is higher version then in Gutsy you can expect problems.

i found it there but how do i download it

---

### Post by kesman on 2008-04-03
[http://getdeb.net/search.php?keywords=Rhythmbox](http://getdeb.net/search.php?keywords=Rhythmbox)
is this the newest version?

---

### Post by SunnyRabbiera on 2008-04-03
You can get hardy packages yes but its at your own risk, if you break your system it is out of our hands.

---

### Post by kesman on 2008-04-03
Get it from GetDeb, it works 100%

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-04-03
ooo 
could i some how use chroot
and run both 7.10 and parts of 8,04 at the same time
or have a directory were rhythmbox has all it's dependanceys that are over 7.10 and then it could just use the stuff from 7.10 to get the rest done


Oh i am running 64 bit as well

---

### Post by kesman on 2008-04-03
[http://getdeb.net/app/Rhythmbox](http://getdeb.net/app/Rhythmbox)

Get it here ffs

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-04-03
> **kesman said:**
> [http://getdeb.net/app/Rhythmbox](http://getdeb.net/app/Rhythmbox)

Get it here ffs

that was not build with libmtp7 and that means that my music player will not work with it

so i think i am just going to bata test

:) lol

---

### Post by &lt;&lt;joe&gt;&gt; on 2008-04-03
8.04 rocks :) works well
creative zen i purchased about 3 months ago is fully sapported by rhythmbox in 8.04 just go to edit plugins then check mtp sapport

---

