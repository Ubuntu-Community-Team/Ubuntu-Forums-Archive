---
title: "Apt-Get Error"
date: 2006-01-16
forum: Absolute Beginner Talk
---

### Post by Jaygo333 on 2006-01-16
Every time I run apt-get, I get the following erro at the end.No matter what I'm getting/installing or removing, I always get the following comment at the end of the update.What is it, and How do I remove it?

W: Couldn't stat source package list [http://kanotix.com](http://kanotix.com) ./ Packages             (/var/lib/apt/lists/kanotix.com_files_debian_._Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://kanotix.com](http://kanotix.com) ./ Packages (/var/lib/apt/lists/kanotix.com_files_debian_._Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

I've run apt-get update but still get the error, enev at the end of the apt update.

:confused:h34r: Jaygo333 :confused:h34r:

---

### Post by rado_london on 2006-01-16
Did you check your sources.list package. It looks like it doesnt recocnize the kanotix repositories. Check if the name is correct.

Good luck:D

---

### Post by newuser111 on 2006-01-16
either you are using kanotix or you are using kanotix repositories in ubuntu (bad idea)

if you are using kanotix, on the kanotix forum they have a script that updates the sources.list file, better go there and find out

---

### Post by rado_london on 2006-01-16
I am curious what are the benefits of using a Kanotix repos?

---

### Post by newuser111 on 2006-01-16
[QUOTE=rado_london]I am curious what are the benefits of using a Kanotix repos?[/QUOTE]

none that i can see, kanotix is based on debian sid (unstable) whereas ubuntu breezy is based on debian stable, adding kanotix repos could probably mess up your system

---

### Post by Jaygo333 on 2006-01-16
Managed to fix the error. Removed the Kanotix info from the sources.list

To the Kanotix problem, don't know what it is but all I know is that I downloaded/added it to the list to downlaod and use FreeNX

:):h34r: Jaygo333 :):h34r:

---

