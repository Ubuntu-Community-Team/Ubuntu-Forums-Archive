---
title: "[SOLVED] xubuntu live CD won't load"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by soaklord on 2007-08-14
I have an old Dell Inspiron 8000 with a whopping 128mb of RAM, PIII, so I know that I can't load anything but Xubuntu.  I downloaded the iso, burned the image using the recommended software and have a disk that loads/checks memory/verifies disk quality, but won't actually boot up xubuntu.  When I try to load/install, I get a lot of activity, but after two hours, I can only see the blue background with a frozen pointer.  At first, the ubuntu loading circle comes up, but disappears after a bit, then nada.  The machine s currently running xp pro (albeit VERY slowly).  I have tried the ubuntu 7.04 disc on a whim, and it halts long before the xubuntu disc.  Suggestions?

---

### Post by bapoumba on 2007-08-14
Did you download the desktop or the alternate CD ?

---

### Post by soaklord on 2007-08-14
I downloaded the desktop.  Desktop xubuntu 7.04 I believe.

---

### Post by ugm6hr on 2007-08-14
This ([http://www.xubuntu.org/get#requirements](http://www.xubuntu.org/get#requirements)) explains you need 128MB to run Xubuntu LiveCD.  I suspect you have shared graphics memory - so that will reduce your memory below the 128 total.

That's probably why it won't run.

Try the Alternate CD to install.  If you want to try the LiveCD first - it will probably run if you create a swap partition first.  But that would require you to run a linux LiveCD (DSL, PuppyLinux and GParted LiveCD come to mind as possiblities).

---

### Post by soaklord on 2007-08-14
Darn!  I didn't think of that.  OK, I may have to bite the bullet and get some memory for it, if I upgrade the memory to 256, I still won' t be able to run the full ubuntu version either, I am guessing, (shared and all) but can I install xubuntu, then using xubuntu upgrade to ubuntu?  Also, will ubuntu run reliably on that little memory (256)?

---

### Post by bapoumba on 2007-08-14
> **soaklord said:**
> Darn!  I didn't think of that.  OK, I may have to bite the bullet and get some memory for it, if I upgrade the memory to 256, I still won' t be able to run the full ubuntu version either, I am guessing, (shared and all) but can I install xubuntu, then using xubuntu upgrade to ubuntu?  Also, will ubuntu run reliably on that little memory (256)?
Should be okay, not that fast, but okay (I upgraded mine to 512 though).

---

### Post by soaklord on 2007-08-14
Hmm... I may have to look at that if it is not too cost prohibitive.  I am basically looking to turn the machine into a websurfer/text editor/etc.  It is not going to be a photoshop machine or anything, but I have family that may play flash games on it.  Any suggestions?

---

### Post by blithen on 2007-08-14
> **soaklord said:**
> Darn!  I didn't think of that.  OK, I may have to bite the bullet and get some memory for it, if I upgrade the memory to 256, I still won' t be able to run the full ubuntu version either, I am guessing, (shared and all) but can I install xubuntu, then using xubuntu upgrade to ubuntu?  Also, will ubuntu run reliably on that little memory (256)?

You could always try a small Linux OS. Damn Small Linux, and Puppy linux are the best for your situation. Maybe slax.
But Damn small can run on near nothing. Same with Puppy.
I booted both VERY quickly on an OOOOLLLLLDDDD desktop with on 64mb of ram.

---

### Post by soaklord on 2007-08-14
Does damn small run well with wireless?  As I said, this is going to be a web surfer and the wireless is a linksys PCMIA card.

---

### Post by ugm6hr on 2007-08-14
> **soaklord said:**
> Does damn small run well with wireless?  As I said, this is going to be a web surfer and the wireless is a linksys PCMIA card.

PuppyLinux works perfectly with wifi (easier than Ubuntu in some situations).  I'd recommend you try the Puppy LiveCD to see if it fits your needs.

If not - you could try a minimal Ubuntu install: [http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones) (or just try Xubuntu AlternateCD out for size)

---

### Post by blueBin on 2007-08-15
I had the same problem in starting up xubuntu live CD with 128mb ram.  

Just got it running.  My solution is using gparted live CD [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)  to create swap patition before running the xubuntu live CD.

---

