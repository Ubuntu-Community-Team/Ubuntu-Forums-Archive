---
title: "No Bootable Disk Error - BUT I DIDNT INSTALL UBUNTU- HELP?"
date: 2009-03-13
forum: Apple Hardware Users
---

### Post by kreuz35 on 2009-03-13
Help!  I have the new unibody 15" macbook pros running OSX 10.5.6... decided i would give ubuntu a try so i downloaded the 64-bit version, burned the ISO and partitioned my drive 23 GBs (leaving 120 to OSx)...I put the disk in and only ran the "run ubuntu without making changes to your computer" setting... played around with it a little and turned it off, decided i wasn't going to install it.  Now when i turn my mac on, it gives me the "no bootable disk, insert boot disk to continue" error crap ****. ???
When i hold down Alt during startup, i only have the Macintosh HD drive show up and when i click on it, it'll take me back to using OSx, but if i don't it'll just give me that error every time.
any clue what i did?? any clue how to fix it? -__- 
first time poster, and i apologize for that...dono where else to turn to.
thanks a lot in advance.

---

### Post by Therion on 2009-03-13
Help me out here because I'm not understanding something.  You burned a LiveCD of Ubuntu but you partitioned your hard drive... How, exactly?  

This, I think, is the root of your problem, not the Ubuntu LiveCD.

---

### Post by kreuz35 on 2009-03-13
errmm. it was an iso?? i burned it... then after i partitioned the drive, it said but in the boot CD to install... i pressed continue on boot camp and it restarted, then loaded ubuntu. 
oh and also, i ended up deleting the partition i made (the 23gb) and converted it all back to OSx, but i'm still having the problem. still asking me for a CD

---

### Post by Therion on 2009-03-13
> **kreuz35 said:**
> errmm. it was an iso?? i burned it... then after i partitioned the drive, it said but in the boot CD to install... i pressed continue on boot camp and it restarted, then loaded ubuntu. 
oh and also, i ended up deleting the partition i made (the 23gb) and converted it all back to OSx, but i'm still having the problem. still asking me for a CD
I'm not asking about the disk you burned.  I'm asking how you partitioned your hard drive.  And for that matter, WHY did you partition the hard drive?

---

### Post by kreuz35 on 2009-03-13
i partitioned it with boot camp. made space for 23 gb's... thought i was suppose to partition it before i installed a new OS?? then was supposed to put in the install disk for ubuntu? 
-___-

---

### Post by Therion on 2009-03-13
I'm confused.  At one point you say you just wanted to try Ubuntu without installing, but then you're talking about "installing a new OS".

All you need to do with an Ubuntu LiveCD is boot to the disk; there is no need to partition your hard drive, or do anything with your hard drive at all for that matter, if you just want to take Ubuntu on a little test-drive.  That's the whole point, really, for the LiveCD -- absolutely no changes need to be made to the existing install to run the Live environment.

The fact that you have partitioned your hard drive and are now getting errors that your hard drive is un-bootable lead me to believe that you've overwritten your computer's boot record.

I'm sorry to tell you this, but I just realized your a Mac user, and I really have no idea how to help you recover from this since I'm not.  I'm sure someone else will come along though that can help you recover your boot record.

---

### Post by kreuz35 on 2009-03-13
blah. -___- i didn't know that. wish i wasn't such an ubuntu noob. woulda avoided this problem in its entirety.
well, thanks anyways Therion.. you tried. I failed. haha

---

### Post by cyberdork33 on 2009-03-13
get rFEIt and make a CD. Use the partition tool to sync the patition tables, then you should be able to get things working again.

---

### Post by kreuz35 on 2009-03-13
Okay i think i got it?  Dled it, mounted it, restarted it and ran the partition tool.  Now when i restart rEFIt opens up everytime and i have 2 disk to choose from, my Mac HD and something called Legacy OS ??
is it going to be like this forever now? Or is there a way for me to turn on my computer and not have to choose an OS everytime.

---

### Post by cyberdork33 on 2009-03-13
> **kreuz35 said:**
> Okay i think i got it?  Dled it, mounted it, restarted it and ran the partition tool.  Now when i restart rEFIt opens up everytime and i have 2 disk to choose from, my Mac HD and something called Legacy OS ??
is it going to be like this forever now? Or is there a way for me to turn on my computer and not have to choose an OS everytime.
well, it sounds like you installed rEFIt  instead of burning the CD... so now you need to uninstall it. (you don't need it unless you plan to actually install Ubuntu)

---

### Post by kreuz35 on 2009-03-13
siiiiiiiiiiiick. it worked.
thanks a lot cyberdork. saved me pain, frustration, and depression. heh

---

