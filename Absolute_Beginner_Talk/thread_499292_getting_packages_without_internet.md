---
title: "getting packages without internet"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by slackpipe on 2007-07-12
I need to find a way to download packages for Ubuntu on a windows machine.  I found an article about using it to generate a script and then take it somewhere else, and while that would be fine.  Is there anyway I can just download from a repository without generating the script? or being within 20 miles of an ubuntu install?

thanx in advance

mj

---

### Post by rax_m on 2007-07-12
Does this link help?

[http://packages.ubuntu.com](http://packages.ubuntu.com)

But I guess you have to know exactly what you need and the versions...

---

### Post by iver2435 on 2007-07-12
There's always [www.GetDeb.net](www.GetDeb.net).  They have some pretty popular packages, although it's not the "repos"

I'll leave it to someone more experienced than myself to deal with the repo problem, which I would be interested in knowing about also....

---

### Post by phr0ze on 2007-07-12
You can always just look for the software on the internet. All of it is out there. See if they have the software in a DEB file.

---

### Post by Espreon on 2007-07-12
With some packages like gDesklets and aDesklets you will be in dependency hell!
Be prepared to meet Dependency Satan....

---

### Post by scragar on 2007-07-12
you should be able to download the repositories from the repository site(eg: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)) then burn them to a CD and use the SPM to install them from there, alternatively if it's a debian package(ends in .deb) then you can just run it to install it provided that you have all of the necessary libraries.

---

### Post by Nythain on 2007-07-12
[http://blog.mypapit.net/2006/08/get-ubuntu-repositories-on-dvd.html](http://blog.mypapit.net/2006/08/get-ubuntu-repositories-on-dvd.html)

alternately, once you have the time and an ubuntu machine with the internet you can start making your own ubuntu repository dvd's

[http://ubuntuforums.org/showthread.php?t=352460](http://ubuntuforums.org/showthread.php?t=352460)

be warned it takes a LOT of time... i now store them locally on my machine and update once a week, but i dont do the iso part, i just point apt to my backup drive where teh repos are stored

---

### Post by slackpipe on 2007-07-13
thanks for all the replies, looks like there's a lot of useful info.  gonna start trying some of your suggestions.

as for just looking for deb packages (that's what i've been doing for some stuff) a lot of sites just say "it's in the repo's use apt-get to install. and just shows what to type to install it. :(

and yeah, i'll prolly be in dep hell. lol, wont have to do this for too long tho.  should have highspeed at the house in a month or so. three cheers for highspeed cable. w00t.


could you boot from the ubuntu live cd, let it dl the packages with all the deps that the live cd needs (might dl dups, but that wouldn't matter too much) and then save them to an ext hard drive and install them on my machine?  I think i remember seeing a "just download packages" option on the package manager.  but wouldn't larger packages need you to specify where to dl the packages to?

---

