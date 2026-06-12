---
title: "Repartition Help"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by crimson90 on 2007-08-01
When I partitioned my HDD with the live CD, I gave a little too much to the Ubuntu partition, and am now down to under a gig for Windows. Is there a way to adjust the partition size so that Ubuntu has a smaller size?

---

### Post by thefoolisme on 2007-08-01
You could do it with gparted through ubuntu.  if it's installed it would be installed under administration, or else you can get it through synaptic or type 

sudo apt-get install gparted   

in the terminal.

should be a pretty easy task to accomplish.

---

### Post by candtalan on 2007-08-01
I do not think you can change ubuntu partitions while you are actually running ubuntu (?)

The way I would do what you want is to use a live cd such as Gparted live CD. You can boot with this and then identify which partition you want to resize. 
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Obviously backup data first in case of a disaster.
If the swap partition is in the way, or needs to be deleted and repositioned, them this would change the partition naming and ubuntu will not work without repair.

If all you need to do is resize partitions, ubuntu should be ok.

Windows will want to scandisk after a resize I think, should happen at first boot folowing, automatically.

---

### Post by Malh on 2007-08-01
Also a good CD to have on you at all times is Hiren's Boot CD, it has partition tools, HDD Regenerators, everything you need.  I use it every time i need to resize a partition using Partition  Magic Pro.

---

### Post by crimson90 on 2007-08-01
Am I going to have to burn the iso in Windows, or is Ubuntu capable of this?

---

### Post by splintercellguy on 2007-08-01
GPartEd should do the trick. To burn an ISO in Ubuntu, stick in a blank CD, press Ignore for the pop-up that comes up, right click the ISO, Burn to Disc or something like that.

---

### Post by crimson90 on 2007-08-01
Okay, thanks.

---

### Post by crimson90 on 2007-08-01
Well, when I right-click, there is no "Burn to disc" or whatever. Any other idea? I'm using Xubuntu. Does it not have the "Burn to disc" feature?

---

### Post by candtalan on 2007-08-01
Burning an iso image to blank cd:

I do not know just now what cd burning program you have in xubuntu.
 I am having a look at it, it will take 15 minutes or so, maybe someone else knows without looking. Otherwise I can comment again in a short time.

---

### Post by crimson90 on 2007-08-01
> **candtalan said:**
> Burning an iso image to blank cd:

I do not know just now what cd burning program you have in xubuntu.
 I am having a look at it, it will take 15 minutes or so, maybe someone else knows without looking. Otherwise I can comment again in a short time.

Did you find out what program it is?

---

### Post by candtalan on 2007-08-01
for xubuntu 7.04 as initialy installed with no extra programs, come with xfburn
this is under the menu Accessories>xfburn

I would expect you to have to use its file finder method of getting to the gparted.iso (or whatever) and begin the image burn process.

Be sure to choose a slow speed. Your equipment might offer a high speed, set to at least half of that, I would go lower to minimise the chance of errors.

If you hav egood internet access it woul dbe easy to install my own favourite which is k3b but it woud also bring down a lot of (kde) libraries and use hard disk space.

hth

---

### Post by crimson90 on 2007-08-01
I opened xfburn and chose "Burn CD Image." I choose the file and set the speed. But when I click "Burn Image." it pops up with a window that says "operation finished" and it doesn't even burn it. Am I doing something wrong?

---

### Post by crimson90 on 2007-08-01
Anyone got an idea?

---

### Post by crimson90 on 2007-08-01
Sorry to bump, but I really need this fixed.

---

