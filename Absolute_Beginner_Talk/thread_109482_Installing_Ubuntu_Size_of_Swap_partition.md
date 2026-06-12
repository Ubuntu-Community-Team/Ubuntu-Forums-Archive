---
title: "Installing Ubuntu: Size of Swap partition"
date: 2005-12-28
forum: Absolute Beginner Talk
---

### Post by uab999 on 2005-12-28
I'm installing ubuntu and I need a recommendation as to the size of the swap partition I should create. Thanks.

---

### Post by jbrader on 2005-12-28
The usual rule of thumb is to make it twice the size of your ram. So if you have 512mb of ram (for example) then you'll make your swap 1 gig.

---

### Post by chimera on 2005-12-28
I thought it was 2.5 times the size of your ram?:confused: 
That's the size I gave it, anyway...I may be wrong.

---

### Post by Herman on 2005-12-28
The amount of swap area you should use depends on several things.

1)How much RAM have you got already? If you already have plenty of RAM, you only need a small amount of swap area most likely. If you have say 1.0 GB of RAM, you hardly need any swap. If you have a very small amount of RAM, like 60 MB for example, you might need 180 MB of swap. (Three times the size of your RAM).

2)What are you planning on using you computer for? Some programs take up huge amounts of memory and others hardly use any.

3) How much room can you spare on your hard-disk? If you have a large modern hard disk, with plenty of GBs you'll never use, you can afford to allow extra swap area. If you have an small disk, where every MB is precious, then you might decide to budget on less swap area. Unfortunatly, older, or cheaper computers tend to have smaller hard disks and smaller amounts of RAM, so the shortage of hard-disk area and the shortage of memory often occur together, making this subject a worry for some people.

4) I would suggest to make your swap area as large as you can, if you have the space for it, but any more than three times the size of your RAM, I have read, is probably a waste, it will never be used.
Equal to the size of your RAM might be okay.

I have 512 MB of RAM, and a large hard-disk, so I have 1.0 GB of swap (double my RAM) to be on the safe side as I have plenty of disk space to waste, and open some heavy applications sometimes. 

To learn more, read the info in this link, it could be old information though, so use common sense too. [http://en.tldp.org/HOWTO/Partition/partition-4.html#SwapSize]("http://en.tldp.org/HOWTO/Partition/partition-4.html#SwapSize")

(Herman) :D

---

### Post by prizrak on 2005-12-30
2 to 3 times the RAM is a what's generally recommended. One thing I can tell is that Firefox is a hog on memory it runs about 100megs in RAM so keep that in mind.

---

### Post by ubuntuuser on 2005-12-30
Just to give you an idea: I have 768 MB RAM installed. My swap partition is 190 MB and whenever I looked (which I did very frequently to see whether it might not be enough space) there were rarely ever more than 10 MB swap used.
Right now I have open two Firefox windows, two nautilus windows, one gedit window, streamtuner, OpenOffice Writer, listen to a web radio using xmms and running john the ripper to see if my passwords are strong enough, and the gnome system monitor tells me that roughly 36% of my RAM and 0% of my swap space is used.

---

