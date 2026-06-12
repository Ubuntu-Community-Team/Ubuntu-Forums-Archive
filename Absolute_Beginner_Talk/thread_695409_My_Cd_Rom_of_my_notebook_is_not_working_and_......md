---
title: "My Cd Rom of my notebook is not working and ....."
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by sam1981 on 2008-02-13
the hard drive don't have no OS how can i install ubuntu on my lap top 
can i take the hard drive out and connect it to my other pc and make a partition and put the iso image
or i can use a USB i need a solution as of rite now its almost 6 hours i am trying to solve this problem the laptop is great but it doesnt have any OS help please

---

### Post by Presto123 on 2008-02-13
If you take out the HD and load it off of another computer, you will probably have some hardware issues moving back and forth between the two different computers.

*Edit* Sorry...my brain wasn't working...you said you don't have a CD ROM drive working. Sorry for the idiotic reply there.

How about using a USB drive? I don't know if that would really work in this case...never tried it. Odd that I haven't, too.

---

### Post by spiderbatdad on 2008-02-13
I've seen some post regarding installing Ubuntu from a flash drive. Linux Mint ( gutsy with creme de menthe) has a download iso for flash drives.

---

### Post by houstonbofh on 2008-02-13
Can you boot from USB?  If so, use a USB CD-Rom, or flash drive with the CD-Rom image.  If not, pull the drive, and slap it in another computer.  Install Ubuntu **minimal server** only.  This is no GUI.  You can move this drive without issues and it will autodetect the new hardware, but Xwindows is not so forgiving. :)  If you have a USB CD-Rom skip the next step.  Boot the laptop with the new system, and edit your software sources to ignore the CD.  Now type "sudo apt-get install ubuntu-desktop" to get the entire system over the net or from your USB CD-Rom..

---

