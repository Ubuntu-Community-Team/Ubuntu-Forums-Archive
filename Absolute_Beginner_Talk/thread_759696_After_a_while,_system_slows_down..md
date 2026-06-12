---
title: "After a while, system slows down."
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by Saardox on 2008-04-19
I can't stop thanking all of the corroborators of the wonderful Ubuntu community.
This is my third poblem:

I've been doing some heavy downloading lately and been leaving my computer(laptop) on for about 3-4 days straight. After my 21 gig file finished downloadng, the Ram usage of the computer was 90% even if I had no programs opened, this that was instantly solved after restarting. However, now my ram seems to be running out faster... After 3-4 hours of heavy pc usage (Eclipse, Firefox, open office) The screenlet's pc usage feature tells me that I've used about 80% of my ram and I feel my PC greatly slow. Even though I close all the programs and even pkill them, my comp keeps being slow. My noob guess is that the ram is stored in some kinda buffer or something.
Is there anyway to fix this?
How can I retrieve this ram?
What is happening?

Excuse me for my sloppy English and once again, thank you all for your kind help

-Saardox

---

### Post by quirks on 2008-04-19
The amount of memory that is shown as being used by your screenlet is not representative. Linux caches a lot of stuff in memory, in case you need it again later. If there is not enough memory left when you try to open a new program, it automatically frees unnecessary cached memory. You can use to command-line utility free to see how much is cached.

How much memory do you have? I recommend at least 256 MB. My machine has 512 and it constantly runs fast (even over days and dozens of hibernation cycles). If you have only little memory, the system might start swapping (i.e., put some of the memory on disk). Hard disk access is very slow compared to RAM access. You can check how much memory is being swapped out using the System Monitor (Resources tab). When you access and application which has been swapped to disk, the system takes some seconds to retrieve it from there, but after that, it should run fast again.

---

### Post by Saardox on 2008-04-19
Thank you for your response. I use the free command and this is what comes up:

             total       used       free     shared    buffers     cached
Mem:       1034184     960760      73424          0       4244     386620
-/+ buffers/cache:     569896     464288
Swap:      3028212      34796    2993416

by the way, I have 1 gig of ram.

-Saardox

---

### Post by StOoZ on 2008-04-19
what is the command line utility ?

---

### Post by Saardox on 2008-04-19
type "free" in command line.

---

### Post by cardinals_fan on 2008-04-19
The important line is '-/+ buffers/cache: **569896 464288**'.

The first number is the total memory used, the second is the memory free.  You seem to be using a lot...

---

### Post by Saardox on 2008-04-19
What may be happening then?
Is there anything I can do to fix it?

---

### Post by sailor2001 on 2008-04-19
in terminal:  sudo apt-get autoclean    also to really do a good clean-up, [http://ubuntuforums.org/showthread.php?t=664742&highlight=clean+old+files]("http://ubuntuforums.org/showthread.php?t=664742&highlight=clean+old+files")

---

