---
title: "Partitions troubles"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by Mushie on 2006-12-23
Okay, day 2 of having Ubuntu, and loving it to start off with. I'm starting to get frustrated a little bit though. I'm awake of the fact i need to be the root user of the computer to partition my computer and I want to set it up the following ways.
1 - Ubu Part
2 - Linux Swp
3 - Windows OS Part
4 - Windows Recovery (just a possibility, but that seems to be broken, they never work right...)
5 - Free space so that both Ubu and Win can access it and store information.

I'm not worried about losing information right now so I can reformat this completely if needed.

I'm also really new to using the terminal. I can navigate around a bit with the ls and cd commands. Use to be able to do more but it's been over a year since I learned any of this.

I'm really pleased with this OS and it's capabilities, just wanna have a windows backup in case there is something I have to do in windows. Not sure what it'd be yet, but I might find the day that I need it.:-D

---

### Post by housam on 2006-12-23
How many partitions you already have? and how many Gb in each one?
What windows version you have?

---

### Post by bulldog on 2006-12-23
Keep your windows partition as the first one on the disk,to avoid trouble.

Be aware you can have only four primary partitions,so you have to make an extended one which brings the primary's back to three.
Place the swap at the end of the extended partition, if you ever need to re-arrange your space,you don't want the swap as a show stopper.

---

### Post by steve.horsley on 2006-12-23
Good advice from Bulldog there. Another suggestion - consider using a separate partition for /home so that you can reinstall the OS or install an upgrade without losing all your data.

---

### Post by Mushie on 2006-12-23
Ok, I got it worked out. I'm just not going to use windows on here. I'm just going to figure out WINE. I got a desktop with windows on it and I'll just keep that. Thanks for the help though. I got it set with three partitions. One for Ubu OS, swap and ext2 for files. Thanks again.

---

