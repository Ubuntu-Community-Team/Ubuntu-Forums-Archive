---
title: "cd-rom as repo in sources.list gets higher priority?"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by nyinge on 2006-11-01
I'd like to know if the cd-rom entry in sources.list has higher priority than the rest of the online repos?

For example, if there are same packages (same versions, etc.) on both cd-rom and online repos, would apt-get grab the ones on the cd?

Thank you.

---

### Post by bluenova on 2006-11-01
Sources nearer the top get higher priority.

---

### Post by sbassett on 2006-11-01
First, unless there have been security updates, then the repos would have the same packages. If you have a high-speed network, just comment out the cd repo, that is the first thing that I do when I install Ubuntu.

---

### Post by taurus on 2006-11-01
> **sbassett said:**
> First, unless there have been security updates, then the repos would have the same packages. If you have a high-speed network, just comment out the cd repo, that is the first thing that I do when I install Ubuntu.
And you can comment out the line (at the top) regarding your CD-ROM by placing a # in front of it...

```

gksudo gedt /etc/apt/sources.list

```

---

### Post by az on 2006-11-01
> **bluenova said:**
> Sources nearer the top get higher priority.

Mostly.  

If the same package is available locally (on cd or on a repository on your hard drive) then it will not fetch it remotely over the net, wasting bandwidth.

If there is a newer version of the package in the repos, then the newest one will be gotten.  You can avoid this by temporarily dissabling the Dapper-updates and security repositories.

---

### Post by nyinge on 2006-11-01
> **azz said:**
> Mostly.  

If the same package is available locally (on cd or on a repository on your hard drive) then it will not fetch it remotely over the net, wasting bandwidth.

If there is a newer version of the package in the repos, then the newest one will be gotten.  You can avoid this by temporarily dissabling the Dapper-updates and security repositories.

Yes, it is merely to save the site's bandwidth.  I thank you all for the informative replies.

Another question:  Is it possible to designate the downloaded ISO as a cd-rom source?  I can do that easily on VM, but on a stand-alone OS, how would I go about editing the sources.list, or is there a similar command as apt-cdrom?

Thanks again.

---

### Post by az on 2006-11-01
> **nyinge said:**
>  or is there a similar command as apt-cdrom?

Thanks again.

sudo apt-cdrom add

or use synaptic.


You cannot use a live cd (like the Desktop cd) - you would need the alternate cd as a repository.

---

### Post by nyinge on 2006-11-01
> **azz said:**
> sudo apt-cdrom add

or use synaptic.


You cannot use a live cd (like the Desktop cd) - you would need the alternate cd as a repository.

Will this work with the iso file?  I understand that "apt-cdrom add" would only add the actual cd (burned from iso) as a repo in the sources.list.

---

### Post by az on 2006-11-03
> **nyinge said:**
> Will this work with the iso file?  I understand that "apt-cdrom add" would only add the actual cd (burned from iso) as a repo in the sources.list.

No.  But you can mount the iso as a disk and then use it as a local repository.

Offhand, you would add a line like this if you mounted the iso in /media/iso

deb file:/media/iso





I think...

---

