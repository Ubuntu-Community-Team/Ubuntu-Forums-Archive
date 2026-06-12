---
title: "Installing Icewm and Rox on Xubuntu"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by WADemosthenes on 2006-06-15
Xubuntu doesn't come with icewm, I need some help installing it, including rox and any other things I may need.  Thanks, I'm not sure where to start.

---

### Post by cotcot on 2006-06-15
ROx-filer is in ubuntu universe repository.

So check in /etc/apt/sources.list if this repository is marked.
(sudo gedit /etc/fstab : backup this file to /etc/apt/sourcesold.list; check if there is a hash # in front of the line with the universe repostory and save as /etc/apt/sources.list) 

Install ROx-filer with Synaptic (sudo synaptic; then mark ROx filer)

---

