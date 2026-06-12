---
title: "[SOLVED] Reformatting ( erasing all data )"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by BluePlum on 2008-03-11
Hello. I have a dell Lattitude D600 with no driver CD's. It has a broken Windows Xp OS. ( realy screwed :P ) And i screwed my ubuntu up bad. I wanna erase all data and make a fresh start to ubuntu. How do i do this ?

---

### Post by jken146 on 2008-03-11
First, make backups of anything you want to keep.

Then insert your Ubuntu installation CD and go through the installation process.  Depending on what you choose at the partitioning stage, partitions will be deleted, made anew and formatted, and you'll get a brand new Ubuntu installation to play with.

---

### Post by BluePlum on 2008-03-11
But how to erase windows XP? And Cant i earase the ubuntu a diff way? im Realy Bad with partitioning. Dont no anything bout it.

---

### Post by bodhi.zazen on 2008-03-11
The above will work. If you want to wipe the drive clean (not really necessary), try dban :

[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

---

### Post by jken146 on 2008-03-11
If you use the Guided (use entire disk) option in the installer, it will delete all the partitions and install Ubuntu in the whole disk as the only OS.

---

### Post by BluePlum on 2008-03-11
> **bodhi.zazen said:**
> The above will work. If you want to wipe the drive clean (not really necessary), try dban :

[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

So which should i do? U a Guy with a red name you must be smart :D.

Jken Way sounds diifucult..... Are u 100% the guy with the cow avartar that it will Erase Windows two?

---

### Post by jken146 on 2008-03-11
Sorry if I made it sound difficult.  My suggestion was simply to install Ubuntu again.  This will overwrite everything on your hard disk, including Windows.

bodhi.zazen gave you a link for something that will wipe your hard disk clean before you reinstall Ubuntu, which isn't really necessary for you.

---

### Post by bodhi.zazen on 2008-03-11
You can do either.

If you just want to do the "simple" thing, just install Ubuntu and at the partitioning section choose "use entire disk".

If you want to somehow erase or overwrite the data first use dban. There is no need to use dban outside of personal choice.

---

### Post by prshah on 2008-03-11
> **jken146 said:**
> If you use the Guided (use entire disk) option in the installer, it will delete all the partitions and install Ubuntu in the whole disk as the only OS.

Guided-Use entire disk is not really a very good option.

It sets up a primary partition mounted at "/", eg sda1, then an extended partition, sda2, then a logical drive for swap sda5.

A better install will be to choose manual partition, then:

1) Add a primary partition of 10Gb, type Linux/ext3, mount point "/"
2) Add a second primary partition of 2Gb, type linux/swap
3) Use the remaining space for a third primary partition type linux/ext3, mount point "/home".

If you have a slow processor (< PIII-700Mhz), it's better you use ext2 instead of ext3.

Partitioning is very easy to do in Ubuntu's gparted program, which is what you will be using when you choose the manual partition operation.

Cheers,
PRShah

---

### Post by jken146 on 2008-03-11
> **prshah said:**
> Guided-Use entire disk is not really a very good option.> 
It's the easiest thing to do for beginners.  The OP said he wasn't very good at partitioning.

[quote]3) Use the remaining space for a third primary partition type linux/ext3, mount point "/".I think you mean /home, not / here.

[quote]If you have a slow processor (< PIII-700Mhz), it's better you use ext2 instead of ext3.Maybe.

---

### Post by bodhi.zazen on 2008-03-11
@prshah: you have / listed twice, I assume you mean /home for the second ;)

Also, I usually advise swap = RAM x 2 , max 1 Gb, unless you have a laptop in which case swap = ram.

Last, watch the trade off between speed (ext2) and potential data preservation (ext3). My preference is to use a journaled file system (ext3)

---

### Post by BluePlum on 2008-03-11
> **prshah said:**
> Guided-Use entire disk is not really a very good option.

It sets up a primary partition mounted at "/", eg sda1, then an extended partition, sda2, then a logical drive for swap sda5.

A better install will be to choose manual partition, then:

1) Add a primary partition of 10Gb, type Linux/ext3, mount point "/"
2) Add a second primary partition of 2Gb, type linux/swap
3) Use the remaining space for a third primary partition type linux/ext3, mount point "/".

If you have a slow processor (< PIII-700Mhz), it's better you use ext2 instead of ext3.

Partitioning is very easy to do in Ubuntu's gparted program, which is what you will be using when you choose the manual partition operation.

Cheers,
PRShah

What did he just say? using entire disk is bad? Sighs.... im lost now i got it untill he posted this :(

---

### Post by BluePlum on 2008-03-11
Hello I was going to do it today dont wanna say impatient but ive got the time now. :D

---

### Post by jonnywombat on 2008-03-11
Hi Plum..

The easiest thing for you to do is select use entire disk when you get to the partitioning options..

That will delete everything and is very straight forward.

The debate after need not worry you too much, but basically what was being said is there are different ways of setting up your hard drive partitions, some of which have different pros and cons. There is a trade off here... Having these "advantages" vs simplicity... You want to go for the simple option.

You can always mess around with the partitioning tools at a later date and read up on them should you wish at a later date to give a more complex set up a try... 

Hope that helps

Jonny

---

### Post by BluePlum on 2008-03-11
Wow that realy helps man. Thx for telling me. :D. Now just need to get 1 more thing worked out and im good. Thx jhonny.

---

### Post by prshah on 2008-03-11
> **bodhi.zazen said:**
> @prshah: you have / listed twice, I assume you mean /home for the second ;)

Also, I usually advise swap = RAM x 2 , max 1 Gb, unless you have a laptop in which case swap = ram.

Last, watch the trade off between speed (ext2) and potential data preservation (ext3). My preference is to use a journaled file system (ext3)

OK, OK, the second "/" was a typo.. that's what happens with frigging cut-n-paste.

You're right about swap, but I always tell everybody 2Gb swap because everyone has a lot of disk space and memory nowadays anyway... how often does 1Gb of RAM swap out to disk? 

ext2 is also pretty bulletproof... it's a lot like how FAT was; you will get tons of lost clusters but very few to non-existent corrupted files. In a production environment, even in a slow machine, I would stick with ext3... but in a desktop for home/small business use? But as you point out, its a matter of opinion. 

I have a PIII500Mhz / 384Mb / 20Gb running Xubuntu, and when I first installed it with Ext3, I found it to be very slow. When reading on Wiki about the differences between ext2 and ext3, I realized that each file was being written, in effect, twice on ext3: (Once to the journal, the second time to the disk, after which the journal was marked as written). On a slow machine, especially one which uses lower DMA modes (such as mode 2), this leads to significant processor strain. Changing it to ext2 makes a marked, though not dramatic, difference.

That is why I recommend ext2 to those with low processor specs.

Cheers,
PRShah

---

### Post by BluePlum on 2008-03-12
OOOOO a brillient idear hit me. I wait until the next version of ubuntu is released then reformatt and install new version?

---

### Post by Tatty on 2008-03-12
> **BluePlum said:**
> OOOOO a brillient idear hit me. I wait until the next version of ubuntu is released then reformatt and install new version?

You can if you want...  But why wait?

Hardy isnt due out for over a month.  Might as well just install gutsy now.  If you are happy to erase everything on your Hard Drive (which you seem happy to), then theres really no problem i see with installing now. Just do it.  If you arent happy abotu something then just re-install again...

---

### Post by BluePlum on 2008-03-12
> **Tatty said:**
> You can if you want...  But why wait?

Hardy isnt due out for over a month.  Might as well just install gutsy now.  If you are happy to erase everything on your Hard Drive (which you seem happy to), then theres really no problem i see with installing now. Just do it.  If you arent happy abotu something then just re-install again...

fine .... :P

---

### Post by Tatty on 2008-03-12
> **BluePlum said:**
> fine .... :P

lol, its up to you of course ;)

---

### Post by BluePlum on 2008-03-13
mmmmmm 40 gb of space, feels like you just woke up and your all snug :P.

And this is a wired thing that happen ( install went fine ).

I always had the problem on ubuntu that i never worried bout, But when i reinstalled decided to see if it was still there. Whenever i change the screen rotation it freezes and the screen freezes on some muddled up view of what my screen looked like before freezing. But this time when it froze it had a window of the live CD at the end asks you to shutdown your computer and restart blah blah blah. And i had shutdown and stuff and there was 0 traces or data left from the live CD. But when it froze after i had restarted it had that window from the live cd. Like my computer rememberd it and it didnt even have to saved data. Well i got to go get the demon out of my laptop :P. THE POWER OF CHRIST COMPELLS U! " laptop doesnt move "

---

