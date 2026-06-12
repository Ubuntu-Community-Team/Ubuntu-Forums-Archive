---
title: "Something worth noting?"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by andraxion on 2007-09-27
I am not sure if it is major or anything, but since I installed Ubuntu my HDD usage light on the front of my computer has not gone off. I am sure it is just a false signal or something, but I wanted to make a post about it to make sure nothing is wrong.

Also, is it normal for Ubuntu to take up a lot of system resources? Whenever I open the system viewer program, it reports that I am using 45% of my memory and 30% of my CPU. This normal or is there something I can do to fix it?

2.7ghz Intel Celeron Processor
512mb DDR-SDRAM

---

### Post by mcduck on 2007-09-27
> **andraxion said:**
> I am not sure if it is major or anything, but since I installed Ubuntu my HDD usage light on the front of my computer has not gone off. I am sure it is just a false signal or something, but I wanted to make a post about it to make sure nothing is wrong.

Also, is it normal for Ubuntu to take up a lot of system resources? Whenever I open the system viewer program, it reports that I am using 45% of my memory and 30% of my CPU. This normal or is there something I can do to fix it?

2.7ghz Intel Celeron Processor
512mb DDR-SDRAM

I wouldn't worry about the hard disk light. Probably just a minor glitch with your hardware & Linux.

It's hard to say about the CPU usage, you should check what program is using all the CPU power. Go to System/Administration/System Monitor and check what's the program causing the problem.

For the RAM usage, memory not used is memory wasted. Linux tries to use all available RAM to increase your system's performance. All RAM not used by the OS and applications you are running is used as disk cache, to store data you have recently accessed from your hard drives as you are likely to need it again and reading it from RAM is roughly 1000 times faster than reading it from your hard drive. If programs need more RAM, cached data is immediately dropped. To check how much RAM programs are actually using run 'free -m' in a terminal and pay attention to the '+/- buffers/cache'-line.

---

### Post by andraxion on 2007-09-27
Ok sweet thanks. I am still adjusting to Linux in general. I am completely amazed at the repository. That system runs so smooth and it helps a lot when you are new and have no clue how to install things that make no sense.

Thanks for all the help I have received from various people throughout the course of this journey. I am having a blast haha

---

### Post by floke on 2007-09-27
From the terminal:

top = shows all running processes along with memory and cpu used (q to exit)
df -h = lists hd space used
sudo fdisk -l = similar to above but for all partitions

---

### Post by andraxion on 2007-09-27
There is a tool for the same thing that I found on the panels. System Monitor I think. I am now at like 8% CPU which is better but is it normally that high?

---

