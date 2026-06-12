---
title: "Partition help PLEASE!! goin nuts..."
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by SPRL on 2007-07-06
Hi.
Trying to install but partition is getting frustrating.
Ok. Here's my problem... I make a / (root) no problem then do my swap no problem but when I try to do my third /home no mater how I do it I keep getting the error (cant have the end before the start).
Can someone please tell me how to create a /home.
I'm using the live cd and a brand spanking new hard drive.

---

### Post by jrusso2 on 2007-07-06
How many partitions are on that hard drive?  Is there any free space left?  Are you dual booting?

---

### Post by SPRL on 2007-07-06
no partitions - bran new 320gb drive clean - just installed it.

---

### Post by SPRL on 2007-07-06
can anyone direct me on how to partition - bump-

---

### Post by por100pre1 on 2007-07-06
What about deleting all partitions and just let the installer do the job? I know it's not the ideal way but it can give you some peace of mind.

---

### Post by overdrank on 2007-07-06
> **SPRL said:**
> Hi.
Trying to install but partition is getting frustrating.
Ok. Here's my problem... I make a / (root) no problem then do my swap no problem but when I try to do my third /home no mater how I do it I keep getting the error (cant have the end before the start).
Can someone please tell me how to create a /home.
I'm using the live cd and a brand spanking new hard drive.

HI and welcome. When you set your root partition you probably set it at the beginning of the drive. Thus when you try to set your  home partition it is set by default to set a the beginning, thus you need to set your home partition at the end of the drive. I hope this helps good luck!:popcorn:

---

### Post by SPRL on 2007-07-06
When you just let the installer do it does it take the minimums of everything? ie if I have 1gb of ram will it only put swap at 256mb?

---

### Post by pbaumgar on 2007-07-06
> **SPRL said:**
> When you just let the installer do it does it take the minimums of everything? ie if I have 1gb of ram will it only put swap at 256mb?

This is a clean drive right?  For swap space I'd set about 1.5 times the amount of RAM you have.  What exactly is your question?  I'm confused by your post.

---

### Post by SPRL on 2007-07-06
At the partition part I add the / root
then Swap,
then /home - when I add the /home it gives me the error (can't have the end before the start)

I have tried putting it at the end and no matter what order I do the partition it won't take /home without giving me the error message.

---

### Post by pbaumgar on 2007-07-06
what happens if you add /home before /?

---

### Post by SPRL on 2007-07-06
trying to put in /home in any order gives error message

---

### Post by pbaumgar on 2007-07-06
what is the error you are getting?  I'm confused...  This is during the graphical install off the Ubuntu CD right?

---

### Post by kvonb on 2007-07-06
The usual way would be to put:

/ first
/home second
swap last

There is a button or something that sets "at end of free space" or "beginning of free space" somewhere on the partition page (I can't remember exactly), but try changing it, it should be always "at beginning of free space".

Oh, and I usually make them all primary partitions (personal pref) which is ok if you are planning on having 4 or less total, and not planning on adding more later.

---

### Post by SPRL on 2007-07-06
ok tried all suggestions and I stll get the error message.
It will just not take a /home partition
thanks

---

### Post by candtalan on 2007-07-06
> **SPRL said:**
> ok tried all suggestions and I stll get the error message.
It will just not take a /home partition
thanks

Just a thought here - I am no expert. In some of my partitioning activities I noticed that I had to commit (apply) the initial changes as a first stage, then at a second stage still in the partition editor, continue with the second stage. Your new drive is empty so you have nothing to loose?

I often have fond gparted (live CD) to be useful 
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
- it is a bit more flexible than the built in partitioner in the ubuntu installer, at least I have found it easy to use, when I intend to install k/ubuntu using manual methods.
hth

---

### Post by SPRL on 2007-07-09
OK so I toyed around with this and ended up with the default setup.
 I was able to put a /home partition at a very low gig that it would accept. I gues it wont do a /home of 300 gb, but it did take 200gb.

I'm all set up now..not everything worked in the media setup tutorials. I had to use a few tutorials and peace them together as to what would work for me. But now all my multimedia works.

The only issue left is the resolution. Its a bit on the small side but if I try to bump it down a notch my monitor gives me the "out of frequency range" and the bump down from that is to big. I did do some adjustments as per some tutorials like adjusting default depth but nothing has worked so far.

Oh well...thanks for all the help to everyone :D

---

