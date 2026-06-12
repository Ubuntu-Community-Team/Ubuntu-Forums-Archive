---
title: "Separate /home partition ?"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by mediax on 2007-04-02
I've been running Ubuntu (first Dapper, currently Edgy) happily for about six months, dual-booting with Windows and using 20Gb of a 40Gb disk.

I currently have two partitions (/ and swap), but am thinking of creating a separate /home partition.  I've found a how-to covering this, but would appreciate any advice regarding partition sizes.

My swap is 1Gb, which leaves me with 19Gb to split between / and /home.

---

### Post by srunni on 2007-04-02
Give / about 5 GB and use the rest for /home. You can store all your data in /home, allowing you to do clean installs instead of the in-place upgrade without having to back up your data. I'd suggest that you make this modification when installing Feisty, as it's coming out soon. Just use the manual partition editor to set up your partitions so that your XP partition is first (and is whatever size it has been until now), / is second (and is 5 GB), /home is third (and uses all remaining space), and swap is fourth (and has a partition that is twice as big as your RAM).

---

### Post by antoz on 2007-04-02
It depends on how many extra programs you want to install on your "/" but myself would allocate 5 t0 8 GIG and the rest for my home partition.

---

### Post by go2dell on 2007-04-02
Yes.  Do it.  You can then play with Ubuntu, destroy it, upgrade to new versions... whatever... to your heart's content.  Just make sure you don't delete /home (unmount it before any major operations) and you won't have to worry about your data.

As for partition size, that's going to have to be up to you.  If you're only keeping some config files and such in your home, you won't need much space.  If you're planning to rip your entire CD collection to OGGs and store it there, you'll need as much space as you can get.

Similarly, the rest of the system will need a heckuva lot of space if you're planning to install both the Gnome and KDE desktops, plus experiment with every application in the repository.  The [Installation Guide]("https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/memory-disk-requirements.html") says 2GB minimum for a full Ubuntu install, and that amount will be plenty if you won't install more apps.

---

### Post by mediax on 2007-04-02
Thanks srunni and antoz - it's always reassuring to get two replies with similar answers :KS

Didn't mean to omit you, go2dell - our postings crossed in transit.

---

### Post by jvc26 on 2007-04-02
I'd give 5Gb to the main Ubuntu install tbh, (Ive always worked with a minimum of 5 gig for the Ubuntu / partition and usually around 20, but obviously you have less space available) So, I'd probably suggest 5Gb for Ubuntu and stick the rest in /home - to be honest it really depends on how much you want to have available for your /home files.
A good tutorial (may be the one you've found- this is the one I used) [here]("http://www.psychocats.net/ubuntu/separatehome")
Il

---

### Post by ComplexNumber on 2007-04-02
i would give 11GB to /home and 8GB to /. 
i have much more than everything that i will probably ever need, and i'm only using 7.1GB. in addition to that, all my themes and icons are stored in /usr/share. both icons and themes take up 1GB.


/home can act as a permanent storage area, so its best to have this as large as possible within your needs. this is especially important if you have a lot of videos or audio files. you may be surprised how much all other files can take up too.

---

### Post by mediax on 2007-04-03
I'm not much of an eye candy person, so I don't use a great deal in the way of themes, etc.  However, I suspect I will have a play with different desktops (when I get the time, of course . . . ), so that's tearing me both ways.

On the data side, I do mess around with a lot of video clips, so I know I'm likely to fill as much space as I've got available (I'll always remember getting my very first 20Mb hard disk - back when the alternative was 360kb floppies - and thinking "Wow! I'll ***never*** fill all that space!"  :lolflag: )

I suspect I'm likely to run out of data space before system space, so I'll probably go for 5Gb / and 15Gb /home.  Now, if I can only drag myself away from the decorating over Easter . . .

Thanks for the link, Illuvator - you're right, that was the one I found.  It's always good to know it worked for someone else, though :)

Thanks again to everyone who's replied - I appreciate your thoughts.

---

