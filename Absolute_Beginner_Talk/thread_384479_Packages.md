---
title: "Packages?"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by stevenjt on 2007-03-14
I recently (two days ago), installed the "edgy" build on a machine at home.  This machine is *not* connected to the outside world, nor can/will it be.  I assumed there would be no problems getting software, as I noticed the "packages.ubuntulinux.org" sub-domain here.

Yesterday I attempted to download a few packages I was interested in, and to my dismay they both had a page worth of dependancies.  At first I thought, no problem...this is a "package" after all, they will be included by default.

Well, I guess I shouldn't have assumed that?  Do "packages" *not* include dependancies?  If not, why are they called "packages"?

To make matters worse, many dependancies have even more dependancies, making downloading them each, individualy, and absolute horror...

Is there not a location somewhere where I can download packages that are true "packages", dependancies included?

I can't believe this isnt the case, as it would seem common sense to do so?

---

### Post by christhemonkey on 2007-03-14
1) They are called packages as they contain all the individual files that make up that particular item.

2) The autopackage project tries to do just this.
     See here for some autopackages:
[http://autopackage.org/downloads.html?PHPSESSID=1caa059ef5c2a85b14a86a34af86365c](http://autopackage.org/downloads.html?PHPSESSID=1caa059ef5c2a85b14a86a34af86365c)

There used to be/still is a add on cd for ubuntu with popular softwares (+all neccesary dependencies) on it.
[http://mrbass.org/linux/ubuntu/](http://mrbass.org/linux/ubuntu/) (but its very outdated so dont actually use it)

---

### Post by 23meg on 2007-03-14
> Well, I guess I shouldn't have assumed that? Do "packages" *not* include dependancies?

They don't. They almost always depend on other packages.

> If not, why are they called "packages"?

Probably because they contain multiple files that are required for applications to run.

> Is there not a location somewhere where I can download packages that are true "packages", dependancies included?

To transfer a package *and* all its dependencies to a computer that's not connected to the net, you can use [APTonCD]("http://aptoncd.sourceforge.net/").

---

### Post by stevenjt on 2007-03-14
Thank you both for the responses...

> **christhemonkey said:**
> 1) They are called packages as they contain all the individual files that make up that particular item.

2) The autopackage project tries to do just this.
     See here for some autopackages:
[http://autopackage.org/downloads.html?PHPSESSID=1caa059ef5c2a85b14a86a34af86365c](http://autopackage.org/downloads.html?PHPSESSID=1caa059ef5c2a85b14a86a34af86365c)

There used to be/still is a add on cd for ubuntu with popular softwares (+all neccesary dependencies) on it.
[http://mrbass.org/linux/ubuntu/](http://mrbass.org/linux/ubuntu/) (but its very outdated so dont actually use it)

I looked at the Autopackage site, unfortunately the list of packages is rather small and doesn't include the items I was looking for.

> **23meg said:**
> They don't. They almost always depend on other packages.



Probably because they contain multiple files that are required for applications to run.



To transfer a package *and* all its dependencies to a computer that's not connected to the net, you can use [APTonCD]("http://aptoncd.sourceforge.net/").

APTonCD looked promising, there is no non-linux version though (only box connected to the outside is running win2k).

All in all, this has been more fustrating that it was suposed to be.  Though I appreciate the help, it looks as if I am better off going back to win2k on both boxes, as I have access to the apps I need under that OS.  This was half experiment (hoping the nature of Linux, in general, would provide me with a more diverse tool set), but in the end my computers need to work for me, not the other way around.

---

### Post by 23meg on 2007-03-14
A quick forum search revealed [this solution]("http://www.ubuntuforums.org/showpost.php?p=1010313&postcount=5") that will apparently let you grab a package *and* its dependencies in Windows. Do search the forums and elsewhere yourself as well; as I don't connect to the net with Windows as a matter of principle, there may be a more elaborate solution I don't know of.

Another possible (though limited) solution may be to download the DVD and use it as a repository.

Ubuntu is dependent on a fast internet connection to work as supposed, since it comes in one CD and you typically need to fetch things from the repositories quite often. If you don't have one, to be honest with you, using Ubuntu can be a painful experience. 

I hope you can find a solution that will make Ubuntu for you. If not, do look into other distributions.

---

### Post by stevenjt on 2007-03-14
> **23meg said:**
> A quick forum search revealed [this solution]("http://www.ubuntuforums.org/showpost.php?p=1010313&postcount=5") that will apparently let you grab a package *and* its dependencies in Windows. Do search the forums and elsewhere yourself as well; as I don't connect to the net with Windows as a matter of principle, there may be a more elaborate solution I don't know of.

Another possible (though limited) solution may be to download the DVD and use it as a repository.

Ubuntu is dependent on a fast internet connection to work as supposed, since it comes in one CD and you typically need to fetch things from the repositories quite often. If you don't have one, to be honest with you, using Ubuntu can be a painful experience. 

I hope you can find a solution that will make Ubuntu for you. If not, do look into other distributions.

Thanks :)

I should have tried searching first, my apologies for that (was getting frustrated...not an excuse I know...)

Just out of curiosity, is there a reason why dependencies aren't included with packages?  Or at least a single, archived, download that includes packages and dependencies?  I ask because to me, this is just a natural way to distribute something, rather than having to go through trees of downloads to ensure all dependencies are covered (which is how it seems to be now).  It just seemed overly complex to me.  Maybe complex isn't the correct word, as I had no problems understanding the system, I just got very fustrated, after I hit about three levels of dependencies deep trying to get a single application, and quit.

I understand that for computers that are wired in, this system works fine...am I just an anomaly (trying to do this on an isolated system)?

---

### Post by christhemonkey on 2007-03-14
I did what you are trying to do for a very long time (before deciding it was quicker just to lug the internet to my pc rather than get files off the internet and bring them to it) and i admit it is infuriating.

Dependencies are there so you dont have a million and one copies of library X installed (say if it was java, imagine having everything that depends on java shipping its own copy of the JRE?!)

---

### Post by 23meg on 2007-03-14
> **stevenjt said:**
> 
Just out of curiosity, is there a reason why dependencies aren't included with packages?  Or at least a single, archived, download that includes packages and dependencies? 

Dependencies are usually shared libraries, or programs that other programs use to accomplish tasks. This is a trait of the UNIX design, which the current GNU/Linux design inherits: lots of small programs that communicate and share resources with each other instead of giant blocks of monolithic applications. 

It also has to do with the fact that the Free software community works with a distributed development model; once a library is written by one author, lots of applications can use it for entirely different purposes, without the original author ever having to know about it, and it would be far from optimal to have a copy of a shared library for each program that utilizes it.

> **stevenjt said:**
>  I ask because to me, this is just a natural way to distribute something, rather than having to go through trees of downloads to ensure all dependencies are covered (which is how it seems to be now).  It just seemed overly complex to me. Maybe complex isn't the correct word, as I had no problems understanding the system, I just got very fustrated, after I hit about three levels of dependencies deep trying to get a single application, and quit.

Normally, you don't do the work of picking dependencies; the package manager does. It's no more complex than selecting a package in Synaptic and clicking "Apply"; it will take care of sorting out and installing the dependencies along with the package you want to install. 

> **stevenjt said:**
> I understand that for computers that are wired in, this system works fine...am I just an anomaly (trying to do this on an isolated system)?

Yes. If you get a chance to use APT / Aptitude / Synaptic, you'll see for yourself. Without them, you'll most likely have a tough ride.

---

