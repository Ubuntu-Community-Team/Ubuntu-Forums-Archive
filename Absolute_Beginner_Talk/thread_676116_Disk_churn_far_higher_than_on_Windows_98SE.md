---
title: "Disk churn far higher than on Windows 98SE"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by LittleTyke on 2008-01-23
As a new Linux user (Ubuntu 7.10) one thing that strikes me immediately is the very busy hard drive. It seems to be constantly on the go. If I put a Windows 98SE rack in the same machine (in place of the Ubuntu rack) it isn't anything like as busy.

Is this something to do with swap page or similar? Or is it just a "feature" of Linux? Or does Linux need a much faster CPU than Windows? (This one is an AMD Sempron 2.8 running in an ABit KV-85 mobo. Hard drive is a Western Digital 20.5 GB)

---

### Post by philinux on 2008-01-23
It's maybe trackerd, most people have disabled it.

Use the command top in a terminal see whats using the disk or system monitor.

---

### Post by macogw on 2008-01-23
trackerd, since philinux didn't explain, indexes your home drive to make it easy to find your files if you're not someone who keeps them well-organized.  Since it just does your home drive (by default) and indexes per-user, it doesn't really make sense to use on a server--regular old updatedb and slocate are the norm for that.

---

### Post by Iowan on 2008-01-23
Someone correct me quickly if I misstate:
Other posts have suggested that after a few days(?) trackerd will get things organized and the thrashing should taper off.

---

### Post by macogw on 2008-01-23
> **Iowan said:**
> Someone correct me quickly if I misstate:
Other posts have suggested that after a few days(?) trackerd will get things organized and the thrashing should taper off.

That's true, but as I said, it's not needed on a server.  Updatedb handles the full file-system, so per-user isn't necessary.  Besides, how would you use the tracker GUI on a server?

---

### Post by Iowan on 2008-01-23
No argument whatsoever. Dunno if/how the GUI would work on a server... but don't remember server being mentioned in original post.

---

### Post by LittleTyke on 2008-01-23
This is what Top says:
Tasks: 100 total,   3 running,  96 sleeping,  0 stopped,  1 zombie
Cpu(s): 2.7%us,   1.0%sy,  0.0%ni,  0.0%id,  96.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:   190920k total,   188372k used,   2548k free,   536k buffers
Swap:  554200k total,   117904k used,   436296k free,   30008k cached

Does that give you any pointers? Thanks!

---

### Post by Delkster on 2008-01-23
> **LittleTyke said:**
> This is what Top says:
Tasks: 100 total,   3 running,  96 sleeping,  0 stopped,  1 zombie
Cpu(s): 2.7%us,   1.0%sy,  0.0%ni,  0.0%id,  96.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:   190920k total,   188372k used,   2548k free,   536k buffers
Swap:  554200k total,   117904k used,   436296k free,   30008k cached

Does that give you any pointers? Thanks!

Well, the output reveals that most of the time in the system is spent in I/O wait ("wa" in the CPU usage listing says 96.0%), most probably waiting for data from the disk. The most interesting part would probably be the process listing below that. It should, by default, be sorted so that the processes using the most CPU resources appear at the top (hence the name of the monitoring tool itself). Try running "top" again and seeing which processes take up the most. The name of the process is the rightmost column, and the %CPU column shows the percentage of CPU time used by that process.

Edit:
On the other hand, the listing you gave also shows that more than 100 megs of swap is being used. It might be interesting to see if something is using up all RAM, causing the system to swap.

Are you running Ubuntu as a server or desktop system? If you use it as a server, have you installed it with a graphical desktop environment?

---

### Post by john.cato on 2008-01-23
Yeah, I just wanted to chime in on the trackerd problem myself. I'm a Java developer so part of what I do all day is use maven to constantly delete and recreate the target folders of the projects I'm working on. After a few hours of constantly creating and deleting thousands of files I noticed that trackerd was taking up 1.1 gigs of RAM. 

It would be nice if there were some system preferences that allowed users to specify exactly which folders they wanted indexed. That way the trackerd could still index, but only on the folders that would commonly be searched.

---

### Post by macogw on 2008-01-24
> **john.cato said:**
> Yeah, I just wanted to chime in on the trackerd problem myself. I'm a Java developer so part of what I do all day is use maven to constantly delete and recreate the target folders of the projects I'm working on. After a few hours of constantly creating and deleting thousands of files I noticed that trackerd was taking up 1.1 gigs of RAM. 

It would be nice if there were some system preferences that allowed users to specify exactly which folders they wanted indexed. That way the trackerd could still index, but only on the folders that would commonly be searched.

Uh, that's in the Indexing Preferences section.

---

### Post by macogw on 2008-01-24
> **Iowan said:**
> No argument whatsoever. Dunno if/how the GUI would work on a server... but don't remember server being mentioned in original post.

It says it's rack-mounted.  That's usually only done for servers, isn't it?

---

