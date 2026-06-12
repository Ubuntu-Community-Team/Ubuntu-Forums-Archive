---
title: "A quick GParted question"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by djsroknrol on 2006-06-11
can this unallocated space that was peeled off of hda1 (win98, fat32) be apprended to hda2 (Ubuntu,ext3) or does it have to be behind hda2 ?

---

### Post by adam.tropics on 2006-06-11
Someone correct me as I am not entirely sure. I beleve that as the free space preceeds your ext3 partition, you would have to create a new ext3 partition to fill the space, copy your data to it, then wipe the original one so as to append it to the newly created partition!!

Personally I would consider just making a new partition (mounted as /home ) and keep everything else on the existing paertition. It's actually a pretty sensible approach anyway.

---

### Post by djsroknrol on 2006-06-11
What I originally wanted to do is give my hda2 some more storage and use the unallocated space tword my Dapper CD from shipit. 

Your idea is great as well. I would much rather use hda2 for playing around with Edgy and have the new bigger space for Dapper when it gets here. Would just a plain file copy of the filesystem and an edit in menu.lst get it moved intact ?

Never tried to do something like that....seems straightforward enough...

---

### Post by richbarna on 2006-06-11
[QUOTE=djsroknrol]What I originally wanted to do is give my hda2 some more storage and use the unallocated space tword my Dapper CD from shipit. 

Your idea is great as well. I would much rather use hda2 for playing around with Edgy and have the new bigger space for Dapper when it gets here. Would just a plain file copy of the filesystem and an edit in menu.lst get it moved intact ?

Never tried to do something like that....seems straightforward enough...[/QUOTE]

LOL, me too, I've got a thread pretty similar yours :-
[http://www.ubuntuforums.org/showthread.php?t=194597]("http://www.ubuntuforums.org/showthread.php?t=194597")

I already tried to do a double install and it borked my system up.
If I get any replies i'll post here ;)

Also look at aysiu's site about partitioning
4 Newbies [COLOR="Red"]1[/COLOR]
|
|
v

---

### Post by adam.tropics on 2006-06-11
Gparted does copy, although I have never tried it, and frankly large file copy events have always made me nervous!. Personally looking at it again, I would backup my data, then really re-organise things a bit. Do you still need the windows partition? You seem to have alot on it, so perhaps you do? Anyway, this is what I have for edgy and Dapper. 2 small partitions of around 6Gb each, one as / for edgy, and one as / for Dapper and then one larger (the rest! ) as /home for both Dapper and edgy. I use seperate usernames on each so /home contains two folders, one for each. For me that means that I can easily gat at any personal files/data from both Edgy and Dapper regardless of wich I am logged into, and also reinstalls if really needed are simple and quick, so long as you tell gparted NOT to format the /home partition. Of course Dapper shouldn't require any reinstalls, but with Edgy, it's more than likely at some point, and at least this way data is safe. You do however need to keep an eye on menu.lst, as it can get a bit confusing as to which is editing it! Off topic, but if you're gonna be playing with both, you can also look at things like pointing you email at the same inbox so whatever you're logged into has some consistancy etc etc.

---

### Post by djsroknrol on 2006-06-11
I think what I'd like to do is move my current Dapper to the unallocated space after a  ext3 partitioning of the space like you suggested with a small (3-4GB) /home and then wipe the current hda2 and enlarge the new partition a little more by regaining the old swap. Then I would still have room in the new hda2 (hda3) for Edgy. 

Unfortunately, the kids still need to access the MS side, or I would have wiped it already...everything I need in MS I'm running in VMware...:O

Now the question is:

If I switch to the unallocated space, after it's all formated, does it become the new hda2 ?

 I would think that if you can't apprend to the front of a partition then in the order of the GUI, the old hda2 would become hda3, correct?

---

### Post by adam.tropics on 2006-06-12
Ok but you might want a bit bigger /home than that. As for the partition names, the order of mine have ended up as hda1, hda3, hda4, (extended)hda5, hda2 !! So I confess you would have to find out on the fly. But it will tel you on the confirmation screen, before you press play, what the new order and naming will be.

---

### Post by djsroknrol on 2006-06-13
Just one more thing...

Here's what I plan to do now. Look at the thumbnail and tell me if I can do what I'd like to:

use hdb2 as a image file for my current hda2,  rearrange hda for a 5GB /home and the rest for a new ext3 and swap. 

Question is, and maybe it sounds stupid (??), but can I put the image file on another drive and move it back to the new home? Everything I've read isn't very clear on locations to me.

---

### Post by djsroknrol on 2006-06-15
Well...I pooched the restore I think...the backup went fine but the restore went to about 60% and then came up with a message "cannot read block 0 on image"....

Is there any way to force it thru, or am I really back to square one ?

---

### Post by djsroknrol on 2006-06-15
Ok, this is a strange one....

I tried 7 times to restore the image thru partimage, and got the same error...very frustrating...I poked around the net and it seems there is a bug with partimage. Weither you compress the image or not, you might see this:

> cannot read block 0 on image (XXXXXXX)

On the Partimage forum someone had the same problem and tapped the "Scroll Lock" key every 1/2GB into the restore....

Sounded pretty stupid to me, but what did I have to lose...and I'll be darned if it didn't work!!

Just alittle FYI for everyone....and I'm a happy camper once again...:)

---

