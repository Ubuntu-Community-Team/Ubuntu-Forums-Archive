---
title: "ubuntu File structures"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by usarmykr on 2007-10-20
I use Kubuntu gutsy, and used to use a partitioned windows system, OS on one partition and files on another.  I used the guided install method and am not sure how to ubuntu files are structured.  I have a /root, and within the root there is a shortcut to a home folder, but I think its the same partition.  How do I partition kubuntu (Ive heard 10g for os, swap, then rest for files) whats the best name (mount-point) for the partitions, and how do I install applications into the files partition, or is 10G more than enough for anything I would want?  Ive noticed all the . prefixed(hidden) folders in my home directory, is this where all apps go?

---

### Post by adamorjames on 2007-10-20
Prefixed(hidden) folders in your home dir are app configs(prefreneces, etc).

---

### Post by llamakc on 2007-10-20
/root is the "root" (god-level admin) user's home directory. You should not be logging in as root.

In /home you should see a directory that is the name of the initial user you set up during install.

Store stuff there. [B]Install applications from Adept (apt-get, aptitude) and let the package management system manage what belongs where. 
[/B] 
If you choose to install software that you personally compile, you can build it anywhere, but when you run the "sudo make install" the files will be normally placed in /usr/local (unless the software is configured otherwise).

---

### Post by usarmykr on 2007-10-20
What I am wondering though, is this:

I am installing a fresh copy of kubuntu, and don't want to lose my files.  I need everything on a seperate partition.  I can back up what I have now, its not much, but I want to set up the next install to have one partition for the OS, and one partition for my files.

---

### Post by adamorjames on 2007-10-20
Normally you'd have - root, home and swap
Root should probably be about 8 gigs.
Home stores your files and should be the biggest.
root = /
home = /home
So when you make a partition for home when you install, make it say /home.

---

### Post by usarmykr on 2007-10-20
Ok, so the 10g / partition will be more than enough to install from adept?  or do installs from adept go into /home?  10G is alot for programs, especially for linux ones.

---

### Post by adamorjames on 2007-10-20
> **usarmykr said:**
> Ok, so the 10g / partition will be more than enough to install from adept?  or do installs from adept go into /home?  10G is alot for programs, especially for linux ones.

10 gigs is enough. Installs go into your root partition.

---

### Post by llamakc on 2007-10-20
The OP may be confusing / and /root as evidenced in the first post.

OP, you want to CREATE a separate /home partition.

[http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

To do it now.

If you're doing it on a clean install (after moving your important stuff elsewhere), when you get to the partitioner, you tell it that you want to do it manually, and you create THREE partitions:

/   (this is the "root" of the filesystem)

swap (your swap partition)

/home (your home directories for any users)

There's a visual step-by-step guide somewhere. I'll see if I can find it.

---

### Post by adamorjames on 2007-10-20
Yes there is no /root, it is called /. Root is called /. :) Just a  forward slash.

---

### Post by usarmykr on 2007-10-20
No no no lol, not confused, I want to know if a 10G partition for root will be more than enough space.  Lets say I wanted to install 15000 packages, will 10G for root be enough, or will kubuntu start installing the packages into the home partition?

---

### Post by adamorjames on 2007-10-20
> **usarmykr said:**
> No no no lol, not confused, I want to know if a 10G partition for root will be more than enough space.  Lets say I wanted to install 15000 packages, will 10G for root be enough, or will kubuntu start installing the packages into the home partition?

15000 :eek: I don't think you'd need that many. 10 gigs is enough for me. Right now I'm using 5.5 and I have both KDE and Gnome installed with quite a few packages. :)

---

### Post by llamakc on 2007-10-20
> **usarmykr said:**
> No no no lol, not confused, I want to know if a 10G partition for root will be more than enough space.  Lets say I wanted to install 15000 packages, will 10G for root be enough, or will kubuntu start installing the packages into the home partition?

Thanks for clarifying. Your first post literally says "/root" which is why I thought so. 

K|Ubuntu will not install packages into /home.

I have a very package-full system and I'm using just under 12G (with 1752 packages installed [dpkg -l | grep ii | wc -l]

---

### Post by usarmykr on 2007-10-20
OK cool, so I will do one partition 10GB as '/' and one as '/home' for the rest.  with a 4gb swap.  Thanks for the help:D

---

### Post by usarmykr on 2007-10-20
> **llamakc said:**
> Thanks for clarifying. Your first post literally says "/root" which is why I thought so. 

K|Ubuntu will not install packages into /home.

I have a very package-full system and I'm using just under 12G (with 1752 packages installed [dpkg -l | grep ii | wc -l]

Well maybe I will make it 20GB just to be safe lol, have a 250GB drive.  Ive got 1200 now but don't think I need them all.

---

### Post by adamorjames on 2007-10-20
> **usarmykr said:**
> OK cool, so I will do one partition 10GB as '/' and one as '/home' for the rest.  with a 4gb swap.  Thanks for the help:D

welcome :-D

---

### Post by llamakc on 2007-10-20
I'm glad I saw this thread. I've got some bloat to hunt down and remove. Good luck.

---

### Post by adamorjames on 2007-10-20
1743 pkgs for me :lolflag:

---

### Post by DarkOx on 2007-10-20
Not like it really matters with a 250G hard drive (heck, I haven't even filled up 60G worth of data yet, and that's with dual booting Windows and Kubuntu), but you don't need 4G for swap. The most I'd ever toss at a swap partition would be 1G and if you've got enough RAM you could easily get away with half that.

A typical Linux install can fit comfortably under 5G (mine, with something like 1200 packages installed, is taking up just under 4 gigabytes). Tossing 20G at your / partition will pretty much ensure it'll never want for space again and if you don't think you're ever gonna fill up your hard drive there's no real reason not too.

---

