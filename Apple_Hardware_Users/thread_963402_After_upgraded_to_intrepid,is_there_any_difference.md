---
title: "After upgraded to intrepid,is there any difference on xorg.conf?"
date: 2008-10-30
forum: Apple Hardware Users
---

### Post by milkwood on 2008-10-30
I just want to know that after upgraded from Hardy to Intrepid,xorg.conf is overwritten?
I mean after upgrade,xorg.conf is refreshed to default setting?
I don't remember.I might have messed up all things just because of that.
Please,tell me.
Thanks.

milkwood.

---

### Post by eldragon on 2008-10-30
> **milkwood said:**
> I just want to know that after upgraded from Hardy to Intrepid,xorg.conf is overwrittened?
I mean after upgrade,xorg.conf is refreshed to default settings?
I don't remember.I might have messed up all things just because of that.
Please,tell me.
Thanks.

milkwood.

if im not mistaken, if you modified your xorg.conf, you will be asked what to do concerning your configuration, 

i would backup all modified config files and let it step over everything...then if anything breaks, restore them.

---

### Post by cyberdork33 on 2008-10-30
> **eldragon said:**
> if im not mistaken, if you modified your xorg.conf, you will be asked what to do concerning your configuration, 

i would backup all modified config files and let it step over everything...then if anything breaks, restore them.
Yes I always backup important config files before an upgrade. You can copy from the commandline very easily to make a backup:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.hardy
```

---

### Post by milkwood on 2008-10-31
Thank you for immediate responses!

Cut to the chase,I upgraded dapper to hardy before.And after booting I came to a black login window.
I thought it was a problem,but there was a login's sound,thus booting was fine. 
Then I reffered to "PowerPc FAQ" wiki and followed "known issues" things.
There was an answer.I've been running Ubuntu on imac G3.It was a G3 problem.
Then I followed that wiki,and rebooted,and everything had gone to be fine.

Next,I'd decided to take a risk to upgrade from hardy to intrepid.
I predicted there sould be a problem as well.Then I had done!

Here is the problem.I'd got the lowgraphic solution thing.
And I'd had open xorg.conf though,I can't remember what it was and how I did with that.

Then I was pissed off and reinstalled hardy.There was another problem here.
I followed predescribed thing but I couldn't get to the login screen.
I tried over and over and over again.Then I went over that instruction.

This is my writing...HorizSync "58-62" VertRefresh "75-117"
but,in fact,to that says...HorizSync 58-62 VertRefresh 75-117.
As you know,There is no need to add "".

I can't believable!I might have messed up all things with that simple mistake.

That's why I want to know.

By the way,Anyone succeeded in installing intrepid on G3 with ATI graphic card?

Thanks.

milkwood.

---

### Post by milkwood on 2008-11-01
Perhaps I've remembered.
I think xorg.conf had not been changed when I upgraded to intrepid.
Maybe you need to know your appropriate xorg.conf setting on intrepid.
I don't know where you should know that.
Only what I can tell you is wait until gut people will get answer.
What's wrong with hardy? 

If my life were over tomorrow,I would like to hear the end of my favorite manga "One Piece".
Life is such a history.

---

