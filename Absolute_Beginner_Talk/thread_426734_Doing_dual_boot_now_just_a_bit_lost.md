---
title: "Doing dual boot now just a bit lost"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by philby on 2007-04-28
OK - I've done a fresh install of XP and left 20gig free for 7.04, watched a vid on what to do but this was based on an earlier version not 7.04. am doing it under manual as the other options did not see the empty partition.

So far (I'm running off the disk as I type with the install phase waiting) have set the swap space (512meg) (/dev/sda2   swap) and have 23211 gig left but it's asking for the root file system and I'm not to sure what to do next....

But I have to admit this is the only problem hell even the wireless system is working when running of the disk. So really all I need to know is "what to do next" to get the dual boot system running.

Any help is appreciated - Thanks Phil

---

### Post by annda on 2007-04-28
use your 23211 MB to be formatted as ext3 and mounted as root (mount point: '/')

have fun!

---

### Post by philby on 2007-04-28
OK now have /dev/sda3 ext3/root - but when I continue I get root system is not defined??? - I know it sounds simple but - OK - I typed in root but I think I was supposed to simply type / have deleated and corrected

---

### Post by annda on 2007-04-28
just choose the sda3 partition and mount it as '/' - you should have a drop-down list for that.

you can take a look at this giude:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

i hope it doesn't confuse you but clears up some things.

---

### Post by expatCM on 2007-04-28
The Psychocats link is nice but it appears to be based on an earlier release of Ubuntu.  The idea is the same but the page layout in the 7.04 set up is a little different.  No problem ...  bar one .....   I suggest you take a look at where your ext3 partition is located, something like hda,5. 

When you get to the summary screen, after disk partitioning, you will see what you are about to do and a button for forward in the bottom right ...  Just above that button there is a button called Advanced.  Press it.  This will show you where to put your boot loader.  If you were not dual booting this would be no issue ... but you are.  So you will need to edit this setting to show where your ext3 partition is so that the boot loader is installed in the right place....

---

### Post by philby on 2007-04-28
OK all good now running 7.04 on the 20gig side and XP is all good also - Thanks for your help - Phil

PS all I need to do now is figure out how to install programs and have a play - thanks again

---

### Post by zvacet on 2007-04-29
**system>administration>software properties>chek all boxes>reload**

With this you are enable all repositories.Common way to install programs is with synaptic(system>administration<synaptis package manager) or with add/rremove.

---

