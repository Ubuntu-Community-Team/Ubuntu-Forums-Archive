---
title: "Trouble installing Xunbuntu"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by Wadeisabeast on 2006-07-19
I am trying to get Xunbuntu on my computer, and have downloaded and burned it onto a disk.  I put the disk in the computer, then click start/install.  After about 5min or so, it has loaded and the desktop is up.  I click on install, and get to the 5th of 6 parts.  It is supposed to partion the hard drive or something, and it freezes.  Am I doing something wrong?

BTW, my comp has a Pentium III processor, 10gb HD, and 128 ram.

---

### Post by John Morgan on 2006-11-02
I empathise.  I am trying to do something similar on a very similar machine, probably for similar reasons i.e., to rejuvenate an otherwise useless piece of junk.  I have as yet not been able to get a complete iso by downloading so I&#8217;m trying to download Etchy rather than Dapper tonight.  Which version have you been trying to get to run?

ATB

John

---

### Post by Bartender on 2006-11-02
I can't confirm this, but have read that the LiveCD requires 256 RAM to work.  I'd try the alternate install CD.  I don't think it's really any harder to go thru than the LiveCD, just no pretty pictures is all.

---

### Post by DirtDawg on 2006-11-02
I had a friend who had this same problem. It does have to do with too little RAM.  Downloading the alternative install disk is the best idea. 

But if don't have the time or access to the internet, when it gets to the point where it "freezes", I suggest going to bed. When you wake up in the morning, you may find Xubuntu installed. That was my friend's experience. The graphical installer just ran really, really slow with 128 RAM.

---

### Post by slipperhead on 2006-11-02
i am running xubuntu on a 96mb machine. i got it to install from the live cd by making a swapfile first so the installer has enough ram to run

---

### Post by Bartender on 2006-11-02
slipperhead -
I think I understand what you're getting at, making a swap file first, but how'd you do that?  Have seen a lot of posts recently where folks with minimal RAM had trouble with LiveCD's.  If your method isn't too technical it might be a good thing to pass on...

---

### Post by DirtDawg on 2006-11-02
> **Bartender said:**
> slipperhead -
I think I understand what you're getting at, making a swap file first, but how'd you do that?  Have seen a lot of posts recently where folks with minimal RAM had trouble with LiveCD's.  If your method isn't too technical it might be a good thing to pass on...

Yes, I'm curious as well.

---

### Post by slipperhead on 2006-11-02
actually,i meant swap partition
well if you can load up the live cd, you can make a temporary swap file of at least 256mb.
start live cd,
in terminal(or crtl,alt,f1): $sudo fdisk /dev/hda (create swap partition)
sudo mkswap /dev/hda1 (hda1 is used in my case)
sudo swapon /dev/hda1
sudo swapon -s (to make sure swap is working)
ctrl alt f7 to get back to desktop and then run the installer.
this gives enough memory to run the live cd and the installer.

i did this as i did not want to dual boot and would only have xubuntu on the hard drive.

you could also do the same by using damn small linux for example and use its cfdisk to partition the swap while running live.

---

### Post by slipperhead on 2006-11-02
p.s this is a good way to install if you dont want to use the alternate cd.

---

### Post by doobit on 2006-11-02
> **slipperhead said:**
> p.s this is a good way to install if you dont want to use the alternate cd.

I have tried it both ways, and I really strongly recommend the alternate install CD. It just works better. I love Xubuntu once it's installed. It's a clean looking interface and works very fast on my Athlon 800 machine.

---

### Post by slipperhead on 2006-11-02
it will probably install faster with the alternate cd. took a while to install with the above method, cant remember exactly how long, maybe about a hour and a half? but worked okay for me and i wasnt worried too much about how long it would take as i did it just to see if xubuntu would run ok.

---

