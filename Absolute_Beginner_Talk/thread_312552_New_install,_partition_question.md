---
title: "New install, partition question"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by charles.g.moore on 2006-12-04
I just got my new laptop and plan on running 6.06 exclusively.
The HDD is a 100GB SATA Drive
I ran across this table which gave some partitioning guidelines it looks like this:

/boot = 100mb
/     = 500mb
/swap = 2 * RAM (I have 2gig in the sys.)
/tmp  = min of 500mb
/usr  = 1.7 - 5.5 gig
/var  = min of 500 mb
/home = as large as possible

I plan to set up the scheme like this...

/boot = 500mb
/     = 5gb
/swap = 4gb
/home = 80gb

Any suggestions?  This puter will be my all around workstation, no games, just music, pics, vnc, vmware (for XP), and assorted other junk...

---

### Post by taurus on 2006-12-04
I would probably modify it a little to make it look something like

```

/boot = 500mb
/ = 10gb
swap = 1gb
/home = whatever left

```

---

### Post by charles.g.moore on 2006-12-04
Cool I think that looks pretty good.
so the "double your RAM thing" is not set in stone?

---

### Post by bodhi.zazen on 2006-12-04
> **charles.g.moore said:**
> Cool I think that looks pretty good.
so the "double your RAM thing" is not set in stone?

No, it is an art.

ram X2, 1GB max for swap should be fine. You likely will not use your swap. 

[Here is a post with some links on swap](http://ubuntuforums.org/showpost.php?&p=1801892&postcount=10)

---

### Post by taurus on 2006-12-04
> **charles.g.moore said:**
> 
so the "double your RAM thing" is not set in stone?
The double your RAM is sooooo yesterday...

---

### Post by bodhi.zazen on 2006-12-04
> **taurus said:**
> The double your RAM is sooooo yesterday...

taurus, what is the new word on swap size ?

---

### Post by taurus on 2006-12-04
As far as I know, any size you want.  Usually, I would make it either 512MB or 1GB, depending on what you plan to run on your Linux system.  If you only run some basic stuff like firefox, openoffice, etc., I would go with 512MB.  But if you plan to use all those and gimp, then I would go for 1GB.  I have 1GB of RAM on my machine and it's rarely touches my swap with 1GB even though I use openoffice, firefox, azureus (not all the time), 3 gnome-terminals, gkrellm, gdeskcal, and gdesklets.  And the machine in my office has been up for 16 days now.

---

### Post by charles.g.moore on 2006-12-04
I guess im going w/ 1gb ram then 
and taurus, the 80's are over man ;-)

---

### Post by taurus on 2006-12-04
> **charles.g.moore said:**
>  
and taurus, the 80's are over man ;-)

Hey, there's still the 90's...  :twisted:

---

