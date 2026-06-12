---
title: "install help"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by tadada on 2007-07-28
Ok I am installing 7.04 on a Abit is7 series motherboard with an ati raedon x1300 pro graphics card with sound and the nic (network interface card) built into the motherboard. it also has a dvd-rom drive sd-816.  Iit also has a floppy drive. I am absolutley clue-less on what drivers i need and how to install them. can anybody tell me which ones I need and where to get them. also the monitor came with a driver too it is a samsung syncmaster 172n. 

can anyone tell me what drivers I need and how to install (or a tutorial that will make sense to a first time ubuntu linux user)

---

### Post by Mornedhel on 2007-07-28
I can tell you ATI X1300 installations usually end with cries of "why won't ATI just release the goddamn drivers". (In other words, they fail.)

The rest should be installed automatically during the installation process. If it doesn't, then you can start checking out the stickies.

---

### Post by tadada on 2007-07-28
ohh ok thank you

---

### Post by Mornedhel on 2007-07-28
I forgot to mention that not having any working Linux drivers for your card (not that there are any for that particular model - a shame, since there are perfectly working ones for an X1400) will mean you will probably get not the best out of your monitor, and no 3D acceleration.

---

### Post by mgmiller on 2007-07-28
If you try to run it from the live CD and get an x failure and no gui, then try running it from the safe graphics mode or it might say graphics compatibility mode or similar.  You will see a choice something like that on the first boot up screen where there will be a list of numbered choices with the live CD.  That will start and install it with the vesa driver which works with darn near every video card.  Unfortunately, as a previous poster said, you will be limited to 2D only.  Consider a different video card (nvidia if possible) if you don't get it working to your satisfaction.

---

### Post by tadada on 2007-07-28
the linux driver from there site says it supports the x1300 the only question I have is does it support Ubuntu?

---

### Post by tadada on 2007-07-28
does the driver support ubuntu?

---

### Post by Mornedhel on 2007-07-28
This thread :
[http://ubuntuforums.org/showthread.php?t=489477&highlight=X1300](http://ubuntuforums.org/showthread.php?t=489477&highlight=X1300)
might help you understand the situation.

It's a Linux driver ; hence, it supports Ubuntu, but it's not developed specifically for the X1300, rather for a family/series of video cards to which the X1300 belongs. I recommend you try with the standard method of enabling the restricted ATI drivers, I've seen it work sometimes. If it doesn't, well, wait for ATI to release *real* drivers.

---

### Post by tadada on 2007-07-28
how would I do what you say

is it the stickie about ati raedon x cards?

and the documents for the driver said red hat and suse but might work with some other distrubutions so I hadda ask.

---

### Post by tadada on 2007-07-28
help please

---

### Post by xc3RnbFO8P on 2007-07-28
Look at this site: [http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")

---

### Post by xc3RnbFO8P on 2007-07-28
My mistake he has give up with ati!

---

