---
title: "freeing up space in my root directory"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by Rizla on 2006-09-12
Whats up guys,

Is there a program/utility that i can use to see which folders in my root partition are taking up the most space?  I used system monitor to check out my available space on my drives and my root partition is getting up there in space.  I used 4.9 gigs already, but when i initially setup the partition table I only made it a 6.5gig partition thinking that I wouldnt really have much installed on there.

Meanwhile i made my /home partition my bigger allocation giving it 18.3 gigs, but only 1% of it is being used.

Soo.. my question is how do i clean up my root partition?  Going forward how do i use my /home partition more effectively.

Right now, all my data/movies/mp3's/programs/etc i store on my data drives.  I've included a snapshot of my system monitor for you to check out:

Thanks,
Vic

---

### Post by Najand on 2006-09-12
maybe the command:
```

sudo apt-get autoclean && sudo apt-get clean

```
can help you get rid of download caches and open Hard Disk a little.

---

### Post by Jussi Kukkonen on 2006-09-12
du is the command you're looking for. Let's say you want to know if there's anything big in your /tmp:
```
du -s /tmp/*
```

If your disk should only have programs on it (i.e. you don't think you have stray video files or something on it), use Synaptic or other package management tools, don't just start deleting files: Take a look at "installed packages" ordered by size, and remove stuff you don't need.
 Another useful program, if you have installed and removed a lot of programs, is deborphan. It helps you find libraries no program is using.

---

### Post by Rizla on 2006-09-12
> **Najand said:**
> maybe the command:
```

sudo apt-get autoclean && sudo apt-get clean

```
can help you get rid of download caches and open Hard Disk a little.

That helped, it freed up almost a gig.  Is there an application that lets you view space usage via some sort of tree or hierachy view?  I think I read somewhere about this type of program, but i cant remember the name of it to save my life.  ITs got a weird name, much like all linux apps ;)

---

### Post by Najand on 2006-09-12
Something like
```

df -a

```

Hmm, searching wierd IT Command Names is very easy by using
```

apropos <KEYWORD>

```

---

