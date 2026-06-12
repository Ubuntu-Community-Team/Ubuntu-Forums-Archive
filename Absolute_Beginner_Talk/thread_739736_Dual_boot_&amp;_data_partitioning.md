---
title: "Dual boot &amp; data partitioning"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by edzell on 2008-03-30
I have 2 computers. The one I've been using is a Win98 machine with 2 HDs, clones of each other (I use xxcopy). Each has a system/software partition and a fat 32 data partition. I'm not a power user: The "big" drive is 15G and it's way more than I need.

On the newer box, recently donated, I want to have Ubuntu and Windows in a dual boot configuration. It has a 40G un-partitioned primary drive with Win98 installed and very little else. The secondary is 20G with nothing on it so far. I want to set this computer up in such a way that I can copy my fat32 data files from the other machine and have them accessible (read and write) to appropriate apps in both windows and Linux. But - at least until I get familiar with Linux - I also want docs created in Ubuntu to be equally accessible in Windows, if that's possible.

i.e. I'd like to have a single data partition but be able to work with its files in both Windows & Linux applications.

I haven't installed Ubuntu yet, but I have the 7.10 CD.

My questions:

1) Should I set up a Fat32 data partition & save all my Linux-created docs in it so that windows apps can work with them. or.....

2) Should I use an ext3 data partition for new Linux documents and enable Windows to work with them (assuming I can figure out how to do it.)

3) If I do that, is there a way to convert my existing Fat32 docs to the ext3 format and copy them to that partition??

4) If I instal new Windows apps after Ubuntu, (but not reinstal windows,) will that interfere with the dual boot arrangement?

5) Will I be able to continue my habit of cloning all my partitions from the primary to the secondary drive, and be able to (dual) boot from that one if the primary fails?

Apologies for the newbie-ness of my questions. I'm anxious to learn how to get my ducks in a row before making a move; hoping not to have to go through too many format & reinstals.

---

### Post by Cresho on 2008-03-30
They way I did it was to run boot up from the cd and try it.  when the cd boots up, you can just play with ubuntu like if it was the operating system.  See if you can access the files.  Try the cd and keep on trying and learning where things are.

After I got a good feel for it, I installed it.  it automatically resized my partition and now I have a dual boot system.  I copied all to ubuntu with no problems and I rarely use windows.  If you boot from cd, it will not install  If you are not sure what's going on, Usually the cd will warn you that it is going to write stuff to hardrive and needs your permission.  It is totally stupid proof.

---

