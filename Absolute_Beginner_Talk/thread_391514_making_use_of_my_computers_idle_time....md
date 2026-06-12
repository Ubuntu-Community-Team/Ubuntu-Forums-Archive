---
title: "making use of my computers idle time..."
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by Incompetnce on 2007-03-23
is there something like seti at home or some other distributed computing time endeavour that i can set my computer working on while it is idle on ubuntu?

---

### Post by tcpip4lyfe on 2007-03-23
Torrents :)

---

### Post by justleen on 2007-03-23
> **Incompetnce said:**
> is there something like seti at home or some other distributed computing time endeavour that i can set my computer working on while it is idle on ubuntu?



loads! check [http://distributedcomputing.info/](http://distributedcomputing.info/)


personally, i like Folding @home.. slightly more useful IMHO

---

### Post by toecutter on 2007-03-23
[http://folding.stanford.edu/](http://folding.stanford.edu/)

install info: [http://fahwiki.net/index.php/Running_the_FAH_client_on_Linux](http://fahwiki.net/index.php/Running_the_FAH_client_on_Linux) (although replace '502' in the commands with '504' for the latest version

---

### Post by Incompetnce on 2007-03-23
awesome i got the BOINC thing from synaptic and set up a couple of projects. now all i need to work out is how to get it to start running when the computer has been idle for, say, ten minutes...

---

### Post by rabbi1337 on 2007-03-23
SETI: Search for Extra-Terrestrial Intelligence :-)

[http://www.seti.org/](http://www.seti.org/)

---

### Post by wpshooter on 2007-03-23
Since you are probably using Ubuntu/Linux, I would recommend FAH, which has already been mentioned.  I have 4 Ubuntu boxes running this 24/7.

If you happen to have any of those M/S boxes still hanging around I would suggest [www.grid.org](www.grid.org)

I highly recommend donating your idle computer time to these projects.  When you think about it, it is almost a crime to spend who knows how much $$$ to obtain a computer with so much processing power and then only use it occassionally at certain periods during the day.  

Install either FAH or grid.org on that baby and crank it up and let that beast process **all day and all of the night**.  It will NOT hurt it (but you do want to make sure you have a good UPS on it), indeed it may last longer than letting it hang around not running the majority of the time and starting and stopping it when you need to use it.  

**AND**, the life that you might wind up saving might be **MINE** or even your sons, your daughters, etc., etc.

Thanks.

---

### Post by dwblas on 2007-03-23
Here is a "how to set up folding@home" link.  Join the Ubuntu team, #45104
[http://ubuntuforums.org/showthread.php?t=101817](http://ubuntuforums.org/showthread.php?t=101817)

---

### Post by Wallace on 2007-03-24
> **Incompetnce said:**
> awesome i got the BOINC thing from synaptic and set up a couple of projects. now all i need to work out is how to get it to start running when the computer has been idle for, say, ten minutes...
Go to your account page on one of the projects that you're running, and edit your "General preferences."

Have a look at the "Do work while computer is in use?" and "Do work only after computer is idle for" settings. In your scenario above, you'd want to set those to "no" and "10" respectively.

The default setting ("Do work while computer is in use" = yes) has BOINC running all the time, but it runs at the lowest priority possible so other applications that you run can get CPU time when they need it.

---

### Post by jvc26 on 2007-03-24
I'd personally +1 for F@H its possibly a more useful outcome than SETI to be fair.
Il

---

### Post by NyteGeek on 2007-03-28
> **Wallace said:**
> Go to your account page on one of the projects that you're running, and edit your "General preferences."

Have a look at the "Do work while computer is in use?" and "Do work only after computer is idle for" settings. In your scenario above, you'd want to set those to "no" and "10" respectively.

The default setting ("Do work while computer is in use" = yes) has BOINC running all the time, but it runs at the lowest priority possible so other applications that you run can get CPU time when they need it.

Actually the default is almost always no and 3, and look at the other options carefully before resetting them, you may notice that the version of boinc in the repositories does not support many of the options.

---

### Post by Cheese Sandwich on 2007-04-24
> **Wallace said:**
> Go to your account page on one of the projects that you're running, and edit your "General preferences."

Have a look at the "Do work while computer is in use?" and "Do work only after computer is idle for" settings. In your scenario above, you'd want to set those to "no" and "10" respectively.

The default setting ("Do work while computer is in use" = yes) has BOINC running all the time, but it runs at the lowest priority possible so other applications that you run can get CPU time when they need it.

My BOINC doesn't seem to honor the "do work after idle for..." preference. No matter what I set it at, it always runs a process in "sleeping" mode & "nice=19" which nevertheless keeps the CPU cranking at 100% & uses tens of MB of memory. However, when I hit the "pause" button in the manager UI, the usage does in fact stop.

:?

---

