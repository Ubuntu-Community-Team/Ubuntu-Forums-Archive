---
title: "How to use NEW 2gb ipod shuffle"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by neurostu on 2008-03-07
So apple just released a new ipod shuffle a few weeks(?) ago. I couldn't sync it using gtkpod and rhythmbox when I tried. So i searched around a bit and found a python scripts called "RebuildDB".

Its great because I can manage my music  however I want (Nautilus my preferred method).

Then I just run the script from the ipod root directory and it rebuilds the ipod's music database.

I would recommend anybody trying to sync the new 2gb shuffle to try this method.

Here is a link to the sourceforge page:
[http://shuffle-db.sourceforge.net/](http://shuffle-db.sourceforge.net/)

---

### Post by midlifecrisis on 2008-03-29
I've spent 24 hours trying to sort out my 2gb shuffle. My win xp and vista boxes wouldn't play with it. I've tried amarok, rhythmbox and gtkpod with various amount of success, I've found that the database becomes corrupt the second time I turn the shuffle on, the shuffle function and skip track doesn't work.

This script has my shuffle up and running, I wish I'd found it yesterday, Cheers

---

### Post by nebu on 2008-03-29
this is gr8!!!

+1 to u!!

---

### Post by midlifecrisis on 2008-03-30
I've written a script that uses LAME to resample mp3's to 96kbps it can be seen here [http://ubuntuforums.org/showthread.php?p=4616116#post4616116](http://ubuntuforums.org/showthread.php?p=4616116#post4616116)

I think it really complements this script.

Cheers

---

### Post by neurostu on 2008-03-30
Glad to be off help!

---

### Post by neurostu on 2008-04-29
In the past I accidentally deleted my ipod control folder, which sucks b/c (at least for the 2gb shuffle) it can't be restored without itunes.  My ipod has been sitting dead now for about a month until I found a windows box I could plug it into to fix it.

Now I'm sure that no one else has ever done this ;-)  so I've posted the tar.gz file here so I (and others) will be able to restore my (our) ipods in the event that ipod_control/ gets deleted again.

---

### Post by badboyrh on 2008-05-14
I'm trying to completely erase my ipod shuffle so it has free space (essentially iPod restore in linux)...how do I do that?

---

### Post by neurostu on 2008-05-14
If you have a 2gb shuffle then you can try to erase everything , download the .tar.gz in my previous post and unzip that into the ipod.  

The iPod_Control.tar.gz contains the iPod_Control dir. When you place this dir on your shuffle it should work.

Essentially when you restore your ipod in Mac OS X or in XP/Vista, it reformats the drive and puts a new control dir on it.

give it a try and let me know if it works for you.

---

### Post by Uncle_John on 2008-06-19
hey, i got a the new 2GB shuffle few days ago, first i installed it on xp windows and it worked fine there. Now i want to use it on ubuntu but shuffle keeps un/mounting all the time. What should i do?

---

### Post by neurostu on 2008-06-19
when you plug it in what happens? It mounts then unmounts? You should probably start a new thread about this.... You'll get better visiability

---

### Post by mcarni on 2008-07-05
THANKS,

I had an old ipod shuffle that i could use only as a memory stick.

I almost decided to ask one of my friends with Windows if I could download the Apple Restore utility thing and use it from there, when I found your post.

I downloaded the file you attached and I extracted it and copied into my Ipod's folder and voila, ipod restored, fantastic.

Thanks 

M

> **neurostu said:**
> In the past I accidentally deleted my ipod control folder, which sucks b/c (at least for the 2gb shuffle) it can't be restored without itunes.  My ipod has been sitting dead now for about a month until I found a windows box I could plug it into to fix it.

Now I'm sure that no one else has ever done this ;-)  so I've posted the tar.gz file here so I (and others) will be able to restore my (our) ipods in the event that ipod_control/ gets deleted again.

---

