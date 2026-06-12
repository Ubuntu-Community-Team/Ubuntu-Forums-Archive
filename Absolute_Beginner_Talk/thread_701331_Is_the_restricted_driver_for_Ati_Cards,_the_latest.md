---
title: "Is the restricted driver for Ati Cards, the latest available? 8.2"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2008-02-19
Or maybe is the latest available when Gutsy was created?

What's exactly the difference between the restricted drivers in Gutsy and the Catalyst?   (Catalyst control panel for example)


I'm asking this because I'm building a gaming Ubuntu machine for a friend of mine, and I prefer installing latest ati drivers, but, you know at every single headers kernel update, the x.org will crash... So then I may install the restricted ones.

But New Catalyst have much better performance...     Guys, this is a difficult choice! 

Any suggestion?


Thanks!

---

### Post by bumanie on 2008-02-19
As far as I know 8.2 is the latest ati drivers for linux. As for your other questions, can't help, but would suggest nvidia supports debian very well with regards to drivers. I guess you aware there are not heaps of games that work on linux, without resorting to wine or cedega.

---

### Post by Kosimo on 2008-02-19
> **bumanie said:**
> As far as I know 8.2 is the latest ati drivers for linux. As for your other questions, can't help, but would suggest nvidia supports debian very well with regards to drivers. I guess you aware there are not heaps of games that work on linux, without resorting to wine or cedega.

Yes, Ati 8.2 is the latest available. 
But my question is; Restricted drivers are updated as well? Or are based on old Ati driver.

As you know, Ati made a very big effort improving Linux drivers performance in some cases more than 100% increase compared to previous versions.  

But the difficult choice is, if I install latest Ati drivers I will have better performance, but if Ubuntu has some kernel/header update... Then the x.org will crash. And then, my friend will call me asking for help.

If I use restricted drivers in ubuntu, this won't happen, even if the performance isn't that good.

---

### Post by Kilz on 2008-02-19
> **Kosimo said:**
> Or maybe is the latest available when Gutsy was created?

What's exactly the difference between the restricted drivers in Gutsy and the Catalyst?   (Catalyst control panel for example)


I'm asking this because I'm building a gaming Ubuntu machine for a friend of mine, and I prefer installing latest ati drivers, but, you know at every single headers kernel update, the x.org will crash... So then I may install the restricted ones.

But New Catalyst have much better performance...     Guys, this is a difficult choice! 

Any suggestion?


Thanks!

The ATI drivers from ATI have significant performance increases. My fps in glxgears went from 1400-1425 to 2300-2400 on my cheap x1050 card. But ATI started a new code base 4 versions ago. As such they still have some bugs. If you want to install the ATI drivers [here is a good howto for Gutsy.]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.2_Driver_Manually") You will have to get the latest drivers and edit the commands a little to match the driver file name.
One of the advantages of the new drivers is aiglx can be enabled for easier compiz installation. Though if this is going to be a game machine, you might run into problems running games and desktop effects.

---

### Post by bumanie on 2008-02-19
I think you are correct. I suspect that using the proprietry drivers from ati will cause a crash if there is a kernel update. Ubuntu doesn't and can't (for probably legal and logistical reasons) update proprietry drivers. May be you could teach your friend how to resurrect things in the event of a kernel upgrade.

---

### Post by Kosimo on 2008-02-19
That's what I will probably do, use restricted drivers even if are less performance. 

About compiz-fusion. I will turn off effects for sure, using effects and games is a mass! 

And the last question comes to my mind, Restricted drivers in Gutsy should be based in official ati drivers right? Witch version?

---

### Post by Kosimo on 2008-02-19
About games, I'm using some native games for linux like Unreal Tournament 2004 and for others, I'm happy with Cedega.

---

