---
title: "need help custom partition install"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by nynoah on 2007-12-27
I just redid my ubuntu install.  I messed up on my other system.  I tried to install the custom installer from Ubuntu Ultimate Edition onto my Gnome system.  Well needless to say, it killed my Gnome system in less than 2 days.  

So..........I can still access my files on there.  I am now trying to install my next Ubuntu install with a other than the "Guided partitions" .  So I went online and researched and set up some custom partitions so that I can keep my home partition always and just reload Ubuntu without worry of wiping my files to oblivion.  

I created a partition for :

/BOOT
/
SWAP
/TMP
/VAR
/HOME

all as ext3

Now.......I am writing from my fresh install but for some reason my computer has not mounted any of the other partitions.  I hit the up arrow to the home partition level and it tells me that it is only 10Gigs of free space to it.  The HOME partition that I made though is 250Gig.  

What should I do now, or should I start over and what should I do different.

Thanks
Noah

---

### Post by Moop on 2007-12-27
All you really need is maybe a 10GB / partition and 1GB swap partiton. The rest of the space can be /home. You really don't need those other partitions and you're limited to four primary partitions anyway.

---

### Post by LaRoza on 2007-12-27
You listed six partitions, overkill I believe.

You can only have four primary partitions anyway.

Any compelling reason to do that?

I would start over, and keep it simple.

---

### Post by nynoah on 2007-12-27
That is what I did already

I know about the primary and secondary.  I have done the install like that.  But I need to somehow direct my ubuntu system to use the correctly.

Any advice.  I am willing to reinstall from square one if you say to do that.

Noah

---

### Post by rsambuca on 2007-12-27
You definitely don't want a separate /tmp when using Ubuntu, and frankly there is virtually no good reason for a regular desktop user to be using all of those partitions.  As others have suggested, I would highly recommend starting over with just a separate /, /home, and swap.

---

### Post by Moop on 2007-12-27
Use the partiton editor on the live cd and create the / and /home partitions ext3. Create your swap partition. 

During install choose manual and then assign the correct mount points for the partitons you made by choosing edit partition.

---

### Post by nynoah on 2007-12-27
Ok so just do a partition for

/
SWAP
/home

I am going to do that now.  Be back in 10 mins

N

---

### Post by nynoah on 2007-12-27
Ok I have done just that now.  

I have done a partition for    /            swap        and        /home

Now, how do I take my home partition from my older hard drive and apply it to this one?

N

---

### Post by Moop on 2007-12-27
If your old hard drive is connected then you will be able to access it after you install Ubuntu. Then you could just copy over the data you want. 

Is that what you wanted to do?

---

### Post by nynoah on 2007-12-27
That is what I wanted to do.  But I was wondering if there was a proper way to do it?  

Noah

---

