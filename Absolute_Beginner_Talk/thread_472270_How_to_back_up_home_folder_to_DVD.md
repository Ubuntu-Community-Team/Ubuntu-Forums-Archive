---
title: "How to back up home folder to DVD"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by p_quarles on 2007-06-12
Now that I'm getting to the slightly more advanced (and therefore more dangerous-to-beginners) features of Linux, I'd like to backup my settings to a DVD (it's only like 2.5 gigs at this point). 

The dumbest thing I did (worth recounting only cause it's damn funny): I tried to use Keep to make an archive of my entire home folder. It simply did not occur to me that saving an archive of a folder inside of itself would cause . . . problems. I realized it was taking too long, though, and was able to kill the process after it built 25 gigs worth of recursive /home/documents/backup directories. But, disaster averted.

Tried some other things (all of which involved more forethought), and those didn't work either. Gnomebaker refused to copy it, telling me that the directories were too deep. Sbackup sends everything to a read-only directory (/var/backup), 

I'm guessing, at this point, that the simplest way to accomplish this would be to make a tar.gz of my home folder from the command line, and *then* burn it.  

If so, can someone more familiar with bash than myself tell me what is the best way to tell tar to archive the directory+subdirectories? Based on my reading of the (cryptic) man page, it does this by default. Is that right?

Any help appreciated.

---

### Post by southernman on 2007-06-12
[http://ubuntuforums.org/showthread.php?t=81311]("http://ubuntuforums.org/showthread.php?t=81311")

The above link will give you a descent break down of doing this. Just modify it to suit your needs. You could also have a look at Partimage. It's a nifty little backup app that you can install to your system or grab SystemRescue CD, which has it (PI) included on the LIveCD of SR.

---

### Post by starcraft.man on 2007-06-12
[Try partimage.]("http://www.psychocats.net/ubuntu/partimage") I think it may be a really good solution for you. Aysiu made a really good explanation, more details are of course on the forum and their site.

---

### Post by p_quarles on 2007-06-12
Thanks. The first option sounds like the easiest, but I'll try PI if it doesn't work.

---

### Post by southernman on 2007-06-12
Actually, Partimage *IS *the best way. And to me, it's better to use a LIveCD in doing so. Aysui howto is a good one... no doubt about that. However, his method calls for installing PI into your ram from the livecd. That's why I suggested using the SystemRescue CD. 

Here is the [http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page") link.

---

### Post by p_quarles on 2007-06-12
Partimage it is then. Thank you both for the help and the links.

---

### Post by starcraft.man on 2007-06-12
> **southernman said:**
> Actually, Partimage *IS *the best way. And to me, it's better to use a LIveCD in doing so. Aysui howto is a good one... no doubt about that. However, his method calls for installing PI into your ram from the livecd. That's why I suggested using the SystemRescue CD. 

Here is the [http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page") link.

DAMN! That is a good disk, I'm gonna burn it right now after I finish the download.

> **p_quarles said:**
> Partimage it is then. Thank you both for the help and the links.

Your welcome. Always happy to help out.

---

### Post by southernman on 2007-06-12
> **p_quarles said:**
> Partimage it is then. Thank you both for the help and the links.

Not a problem. Thanks for the acknowledgment. :)

> DAMN! That is a good disk, I'm gonna burn it right now after I finish the download.

You bet it is... kinda like Knoppix on steroids! ;)

---

### Post by starcraft.man on 2007-06-12
> **southernman said:**
> 
You bet it is... kinda like Knoppix on steroids! ;)

Kinda feel sorry now I wasted some CDs and now I have one that does it all... oh well. Thats progress :D.

Thanks again for link, I'll poke around this CD later or tomorrow.

---

### Post by southernman on 2007-06-12
> **starcraft.man said:**
> Kinda feel sorry now I wasted some CDs and now I have one that does it all... oh well. Thats progress :D.

Thanks again for link, I'll poke around this CD later or tomorrow.Progress indeed.

Sure thing, starcraft.man - Your quite welcome! :)

---

