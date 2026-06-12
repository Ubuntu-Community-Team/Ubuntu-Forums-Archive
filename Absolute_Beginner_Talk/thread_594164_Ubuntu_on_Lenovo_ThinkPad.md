---
title: "Ubuntu on Lenovo ThinkPad"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by Onay on 2007-10-27
A quick question...

I resized the windows vista partition from 80gb to 70gb, then made 2 partitions for ubuntu (ext3 and swap). The problem was that the resizing of the partition took about 2.5 hours, and it seemed to "move" the entire filesystem over. Now, when I try to boot into windows, it goes into lenovo's rescue and recovery.

Is this normal? I understand that when doing this with XP, you may get the message for it to "chkdsk" or check disk, but this is a Vista laptop with lenovo software installed on it. Has anyone using lenovo experienced this problem? Or should I allow it to "recover" my files and then windows will boot up normally?

---

### Post by oilchangeguy on 2007-10-27
> **Onay said:**
> A quick question...

I resized the windows vista partition from 80gb to 70gb, then made 2 partitions for ubuntu (ext3 and swap). The problem was that the resizing of the partition took about 2.5 hours, and it seemed to "move" the entire filesystem over. Now, when I try to boot into windows, it goes into lenovo's rescue and recovery.

Is this normal? I understand that when doing this with XP, you may get the message for it to "chkdsk" or check disk, but this is a Vista laptop with lenovo software installed on it. Has anyone using lenovo experienced this problem? Or should I allow it to "recover" my files and then windows will boot up normally?

did you use gparted, from the live cd, to change your partition? the leveno recescue and recovery will give you a factory fresh install of windows.

---

### Post by Onay on 2007-10-27
> **oilchangeguy said:**
> did you use gparted, from the live cd, to change your partition? the leveno recescue and recovery will give you a factory fresh install of windows.

I partitioned using the Live CD's Partition Editor, but I made sure that all removable media drives and cd's would not automatically mount through Removable Drives and Media.

---

### Post by drs305 on 2007-10-27
I can answer part of your queston. No, it is not normal. I have a lenovo laptop and have installed several versions of ubuntu on numerous occasions. It never took more than an hour to have the complete system installed (with a hard drive that was at most 1/4 full).

I think you are correct about it trying to move all the data - that would at least in part explain why it took so long. I haven't experienced your problem so I can't really advise you on the main part of your question.

There is a site/app called Super Grub Disk that can really help with boot problems. I'd try something like that but as a last resort would let the lenovo recovery do its thing and try the ubuntu installation once you got windows back.

Good luck.




Edited: Onay, here is the link to the Grub Disk site. If you have a way to burn a cd with the iso it can probably tell you what's happening. The site is now mostly linux but I used the disc several times to investigate windows issues.


[http://supergrub.forjamari.linex.org/?section=home](http://supergrub.forjamari.linex.org/?section=home)

---

### Post by Onay on 2007-10-27
So this is probably a vista issue? Do you think that the installer of grub during the installation is directing me to the wrong partition? I know there are 2 partitions for vista, one for the OS and one for Recovery. 

The problem, though, is that I tried rebooting after the partitioning of the vista partition BEFORE installation and the same thing happened. What happened when I resized the disk?

---

### Post by Onay on 2007-10-27
Might my system be booting to that Recovery partition only and not even attempting to go into vista? Or is it trying to login to vista but ends up going to recovery?...

---

### Post by Onay on 2007-10-27
...Bump

---

### Post by drs305 on 2007-10-27
I edited a previous post to cut down on the number of posts and perhaps you didn't notice it. I added a link to the super grub site. If you can burn a cd on another computer, super grub is going to give you a much more definitive answer than any speculation on our part. 

You may be able to get some of the same informaton off a linux cd but I'm not as familiar with what's on those besides partimage and gparted, which I regularly use.

Wishing you the best...

---

### Post by rscarriere on 2007-12-30
Did you ever solve this using supergrubdisk?  I'm experiencing exactly the same problem and I am struggling to get things up and running again.  SGD (so far) hasn't helped.

---

### Post by bwtranch on 2007-12-30
Same thing happened to me about a year or so ago on my Acer AMD 64 that I just bought at Circuit City. Wiped the disk clean, use the entire disk option and have never looked back. Dual boot is a bad option even if you are running Linux. One OS per machine is always the best course. Happy hunting :)

---

### Post by rscarriere on 2007-12-30
Ok solved it.

Downloaded the vista recovery CD from:
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

and followed the instructions on that page.  Worked like a charm.

@bwtranch - would love to have a single boot (like my other 2 computers) but it is a tablet and I'm finding Ubuntu/Linux not as capable on the tablet. (although cellwriter is helping)

---

