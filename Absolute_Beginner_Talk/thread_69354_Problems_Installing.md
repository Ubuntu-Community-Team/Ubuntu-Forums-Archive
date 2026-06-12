---
title: "Problems Installing"
date: 2005-09-26
forum: Absolute Beginner Talk
---

### Post by Baethan on 2005-09-26
A little background info: I'm a Windows user who's computer literate, but not necessarily computer knowledgeable. I don't know what type of computer or hardware I have, just that Ubuntu should work on it and the harddrive has around 4 gbs of space. I've never used Linux before (neither has anyone else I know) and it will be the only OS on the computer I speak of. 
Now, from what I've read, this seems to be a fairly common problem. The base system fails to install again and again. The error message is: "The debootstrap program exited with an error (return value 1). Check /target/var/log/bootstrap.log for details." I have no clue how to check that log. 
So, I move on to the next step, copying remaining packages to the hard disk. That fails. 
I just tried to see what I have as far as partitions, but the thing froze on me. 
Any suggestions? I am going to download the file again, and I'll try burning at a slower speed. (What is the difference with speeds?) Those were two of the solutions I found; another was something about changing the way the partitions are set up. I just used the default partitions, or whatever, so any advice on that is much appreciated. 
Thanks so much! I really do hope I can get Ubuntu to work. (At least I'm learning a whole lot through all this!)

---

### Post by Perfect Storm on 2005-09-26
I've no idea what's wrong with your system. But the suggestion that burning ubuntu on low speed seems to be a good Idea. The reason is when burning at low speed is the chance for errors occur is minimal. So it could sound like a faulty CD or bad burn. Just a guess.

---

### Post by Mustard on 2005-09-26
I have a suspicion that older CD drives can sometimes have trouble installing Ubuntu.  I haven't confirmed it, but I have encountered installations where a perfectly good Ubuntu installation CD is constantly failing to complete the installations steps.  I've used the same CD to install Ubuntu on other systems, hence my (unproven) theory about older CD drives. :)

I would suspect that it has something to do with the burn speed used when creating the disc.

---

### Post by josebalius on 2005-09-26
That happened to me when installing it. I received 2 copies from Ubuntu. I used the first one and it failed to load it, I used the second CD and it loaded it perfectly. Maybe try another copy? Or like Mustard say burn the img at a different speed?

---

### Post by Kodiak3000 on 2005-10-05
I'm having this problem too.  I read that I should burn the CD at about 8x, so I did that, but I still get that error.  It's happened twice now.  Think I can get away with just burning another CD or am I going to have to download again?

---

### Post by taygan on 2005-10-19
enable dma.. hdparm -d1 /dev/sda or something similar during install.

---

