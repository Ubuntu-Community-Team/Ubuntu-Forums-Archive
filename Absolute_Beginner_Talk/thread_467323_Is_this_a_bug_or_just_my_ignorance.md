---
title: "Is this a bug or just my ignorance"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by ICUR2Ys on 2007-06-07
This morning I had an 11 Gig root and the Disk Usage Analyzer showed root as 100% usage.  
I reinstalled ff increased the root to 22 Gig. I have only partially reloaded the applications.  Now the Disk Usage Analyzer still shows 100% usage.


file:///home/dace/Desktop/Screenshot.png

I tried to drag and drop a screenshot but was not successful.

---

### Post by Hendrixski on 2007-06-07
I'm assuming it's because you have a root and a home partition
your root is probably too small, like 3 gigs... and the remaining 20-something gigs are your /home.. or other partitions.

if you run df -h you can find out.
if you have a chroot or pbuilder installed then you're  out of space ... and you'll need to move them and create soft-link (most likely gritting your teeth like I did when I had that problem).
 
Sometimes the graphical applications that show you how much disk space you're using can make mistakes, df -h on the command line generally won't.  it'll also show which partition has what amount of usage and what amount of alocation.  sooo... yes, it could be a bug.

---

### Post by starcraft.man on 2007-06-07
Assuming  you use a separate partition/drive for storing all your data/media, then yes I would find it extremely difficult to believe that you could max out an 11 GB root system. I only use around 4 I think... and I've installed a tonne of things.

Easy way to check you have space is to open up Nautilus (for instance your home folder). And then just go up one directory until you hit root. At the bottom, free space should be indicated.

If that number is less than 1 GB or less than you expect, you have a problem. Otherwise, ignore it.

Edit: Terminal command is good to like Hendrixski pointed out. Either way :).

---

### Post by ICUR2Ys on 2007-06-07
Root is 22 Gigs, /home is 42 Gigs.

---

### Post by starcraft.man on 2007-06-07
> **ICUR2Ys said:**
> Root is 22 Gigs, /home is 42 Gigs.

Right uh, but did you check how much free space their is?

Open any terminal and type 

```
df -h 
```
First entry should be root.

Or alternatively, use my method and navigate to the root.

Either way you should see that root has space left over. You might wanna shrink it again after... 22 GB will just be wasted on a root.

---

### Post by ICUR2Ys on 2007-06-07
I opened Nautilus in /home went up to root, but it only said that I had 4 items in /home.  However, I am certain that I haven't loaded anything that would take up that much space.  With the exception of Wine.  If that takes up the rest of the partition for windows apps.  I don't know aboout wine I have never used it yet.

---

### Post by ICUR2Ys on 2007-06-07
I have lots of space.

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              21G  2.6G   17G  14% /


Only using 2.6 Gigs.

---

### Post by starcraft.man on 2007-06-07
> **ICUR2Ys said:**
> I opened Nautilus in /home went up to root, but it only said that I had 4 items in /home.  However, I am certain that I haven't loaded anything that would take up that much space.  With the exception of Wine.  If that takes up the rest of the partition for windows apps.  I don't know aboout wine I have never used it yet.

You have to deselect the folder your looking at. Just click in an empty space when on the root folder. Then look at bottom again, free space will be indicated in the Root (excluding mounted and home).

Edit: LOL! Well I guess ya ought to shrink it back down to like 8, up to you. Job done :).

---

### Post by ICUR2Ys on 2007-06-07
OK thanks it shows freespace 38.1 Gigs.

---

### Post by ICUR2Ys on 2007-06-07
I don't know how to put a screenshot on these replies or I would show what the Disk Usage Analyzer is showing.  It is either a bug or I am misunderstanding it.

---

### Post by Rui Pais on 2007-06-07
> **ICUR2Ys said:**
> I don't know how to put a screenshot on these replies or I would show what the Disk Usage Analyzer is showing.  It is either a bug or I am misunderstanding it.

when you make a post theres a clip on the top of the frame where you type. 
Click on it and then on Browse button... that allow you to pick an image and upload it.

The Disk  Analyzer tools have a button that will search folder by folder the disk and shows the  size occupied (i prefer a kde tool named filelight that, one of the few apps from kde i always install...)

---

### Post by ICUR2Ys on 2007-06-07
Thanks for the guidance.  I hope the screenshot will show up now?

---

### Post by Acglaphotis on 2007-06-07
Dude that means that the / folder has 100% of the total weight of the disk. Its normal, if you dont understand, see media... you hsave 78% of the 2.gigs there... get it?

---

### Post by Rui Pais on 2007-06-07
The Disk Analyser is little ... (well i will not say what i think of it, btw the name of app is baobad, what a name!)

It take mounted partiions as real space inside your root #-o render it useless. 
In your case, according to your pic, 91.2% of your root is occupied by media, but media should be (unless you have something wrong), where others partitions and external drives are mounted (and of course that space is not root partition space)

Whats the output of:
```
df -h
```

---

### Post by ICUR2Ys on 2007-06-07
I would never have thought of that interpretation.  I will watch this graph as I load up the other partitions on the disk.  I would have expected the percent of usage to refer to the percentage used compared to total available for the root.  Well thank you all very much for your help and guidance.  I appreciate your time.

---

### Post by ICUR2Ys on 2007-06-07
Well Here is the results.

dace@dace-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              21G  2.6G   17G  14% /
varrun               1014M  100K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
procbususb           1014M  156K 1014M   1% /proc/bus/usb
udev                 1014M  156K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   33M  981M   4% /lib/modules/2.6.20-16-generic/volatile
/dev/hda4              47G  181M   45G   1% /extended
/dev/hda2              41G  195M   39G   1% /home
/dev/hdb1             111G  188M  105G   1% /media/sdb1
/dev/sda1             459G  7.9G  428G   2% /media/disk
/dev/sdb1             163G   19G  145G  12% /media/LACIE
/dev/sdb3             111G  1.4G  109G   2% /media/disk-1
/dev/sdb5             193G  206M  193G   1% /media/disk-2
/dev/sdc1             466G   79M  466G   1% /media/disk-3
dace@dace-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              21G  2.6G   17G  14% /
varrun               1014M  100K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
procbususb           1014M  156K 1014M   1% /proc/bus/usb
udev                 1014M  156K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   33M  981M   4% /lib/modules/2.6.20-16-generic/volatile
/dev/hda4              47G  181M   45G   1% /extended
/dev/hda2              41G  197M   39G   1% /home
/dev/hdb1             111G  188M  105G   1% /media/sdb1
/dev/sda1             459G  7.9G  428G   2% /media/disk
/dev/sdb1             163G   19G  145G  12% /media/LACIE
/dev/sdb3             111G  1.4G  109G   2% /media/disk-1
/dev/sdb5             193G  206M  193G   1% /media/disk-2
/dev/sdc1             466G   79M  466G   1% /media/disk-3
dace@dace-desktop:~$

---

### Post by Rui Pais on 2007-06-07
> **ICUR2Ys said:**
> Well Here is the results.

dace@dace-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              21G  2.6G   17G  14% /
...

so, as you can see in fractions of secs (not the eternity that GUIs  take), it says (correct btw) that you have 14% of occupied, 2.6G of 21G.

:)

---

### Post by ICUR2Ys on 2007-06-07
I Think that they need to work on that analyzer some more.  And I will check out filelight.  I appreciate the input.

---

### Post by Rui Pais on 2007-06-07
> **ICUR2Ys said:**
> I Think that they need to work on that analyzer some more.  And I will check out filelight.  I appreciate the input.

yes, never get why Analyzer (baobab) is so weird. A simple python interface for dh output should be more then enough..

Don't know if filelight is too heavy in terms of dependencies, if one don't have kde or at least kde base (i don't use it, but my kid use some games from kde, so i keep it at hand) There is another one with no dependencies but i don't remember the name, i will try to find it and post back.

---

### Post by ICUR2Ys on 2007-06-07
Thank you.
I just looked at filelight, Have to play with it more, but I like it better than DUA already.

---

### Post by Rui Pais on 2007-06-07
ok i found it. Is gdmap. 
But it looks a little strange (use squares to represent space) and have an odd "old" look. 

Nothing like good old df and du (and there is a di on repos that seems to give even more info)

If you mean while installed filelighter give him a serious try. It's nice. 
I just use fileligh to visualize what drains my free space and delete junk. 

For normal use a simple df is more then enough :)

---

### Post by ICUR2Ys on 2007-06-07
Thank you.

I use df, ls, and fdisk the most but once in I while Iike to see a graphical view.  Just to see what is going on,  that is if I can interpret the graph being used.  Thanks again for your help.  Thought I was loosing it with that DUA output.

---

### Post by Rui Pais on 2007-06-07
No prob :)

A graphical view is important. I had recently a problem, when i print a large number of docs, sometimes they stop. 
Nothing come out of printer and i need to restart cups, some times even reboot.

I search a lot and couldn't find any clue or any report on these.

One day i was downloading something and i got a message that i run out of space...
I run filelight to see what was draining my space and found a huge /var/log/cups/error_log ( a HUGE!, more then 4G!) I deleted and problems with pinter disappeared. 
I deduct that at any warning cups had to register it need to open and add a line to a 4G text file and save it again and that take so much time that it seems that all printing was frozen.

Moral of the story... well none, but i wonder if i could find that with only command line, and even i found the correct path if my eyes would had catch that huge file - just a number - when with a graphical view i couldn't even not pretend not to see, it was 1/3 of my partition!!

GUIs are important.

---

