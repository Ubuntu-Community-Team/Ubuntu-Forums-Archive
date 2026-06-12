---
title: "Vista Dual Boot Question(s)"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by Aurora@FleetBuzz on 2008-02-28
I am in the process of planning a dual boot set up for my new laptop.  It has Vista Home Premium and I want to dual boot Gutsy on the same hard drive.  I've found some guides on how to partition the hard drive and install Linux (but any others would be appreciated!), but I can't seem to find a source that tells how to modify Grub via menu.lst so that Vista boots by default after a few seconds pass.  (I know it can't be the same as if the operating systems were on separate hard drives).  Can anyone provide any guidance on this?

Also, I've been reading that Vista tends to take over even after Linux is installed.  I would like to prevent this from happening.  Is it best to boot with Grub or the Vista Bootloader?  Can anyone provide guidance on the "how to" and best way to accomplish?

May thanks as always.

---

### Post by Joeb454 on 2008-02-28
GRUB Would be better, as the Ubuntu installation will detect that Windows is there and add it to GRUB.

We can help you make Windows boot first after you've installed (we'll need to see your menu.lst) :)

---

### Post by spamzilla on 2008-02-28
Install Vista then install Ubuntu, else yes, Vista will eat Ubuntu.

Grub should install over the MBR (when you install ubuntu), so you will end up with good old grub :)

---

### Post by jan quark on 2008-02-28
here is a nice step by step guide

[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)

---

### Post by Aurora@FleetBuzz on 2008-02-28
> **Joeb454 said:**
> GRUB Would be better, as the Ubuntu installation will detect that Windows is there and add it to GRUB.  We can help you make Windows boot first after you've installed (we'll need to see your menu.lst) :)
Thank you, Joeb454, and all who responded.  I'll do that when I install Ubuntu.  I'm planning on allocating 30gig for Gutsy.  Is that enough, or should I do more/less?

---

### Post by spamzilla on 2008-02-28
> **Aurora@FleetBuzz said:**
> Thank you, Joeb454, and all who responded.  I'll do that when I install Ubuntu.  I'm planning on allocating 30gig for Gutsy.  Is that enough, or should I do more/less?

The install will take up around 1.5gigs of space, so 30gigs is more than enough space - it just depends on how much space you need to store all your files.

---

### Post by Aurora@FleetBuzz on 2008-02-28
> **spamzilla said:**
> The install will take up around 1.5gigs of space, so 30gigs is more than enough space - it just depends on how much space you need to store all your files.

Thanks, spamzilla.  Previously, I had used a shared FAT32 partition to share files.  Now that Gutsy has the ability to read/write to NTFS, I'll probably forego this and devote most of the 160gig HD to Vista (hog that it is!).  So 20 gig ought to do it, home partition & all?

---

### Post by spamzilla on 2008-02-28
> **Aurora@FleetBuzz said:**
> Thanks, spamzilla.  Previously, I had used a shared FAT32 partition to share files.  Now that Gutsy has the ability to read/write to NTFS, I'll probably forego this and devote most of the 160gig HD to Vista (hog that it is!).  So 20 gig ought to do it, home partition & all?

Stick with 30gb just so you have that extra room to work with. This is what I'd do:

10gb /root (you don't want to run out of space!!)
18+gb /home
2gb or less /swap

Swap partition should be amount of ram multiplied by 2 but no more than 2gb and any space left over from swap, use up on the /home partition.

(I hope this makes sense :lolflag:)

---

### Post by Aurora@FleetBuzz on 2008-02-28
> **spamzilla said:**
> (I hope this makes sense :lolflag:)
Indeed it does!  Thank you.  RAM is 3 gig, so instead of a 6 gig swap, I should make it no more than 2 gig, correct?

---

### Post by spamzilla on 2008-02-28
> **Aurora@FleetBuzz said:**
> Indeed it does!  Thank you.  RAM is 3 gig, so instead of a 6 gig swap, I should make it no more than 2 gig, correct?

Yep that is correct, as you will just be wasting space that will probably never be used.

---

### Post by Bartender on 2008-02-28
> **Aurora@FleetBuzz said:**
> I can't seem to find a source that tells how to modify Grub via menu.lst so that Vista boots by default after a few seconds pass.

Once you get Ubuntu installed, go to repositories and download "startupmanager".  Just like that - all one word.  It's a neat little GUI that lets you change the default OS and several other parameters as well.  After download/install, you'll find it in System>Administration, listed just above the entry for Synaptic Package Manager.

It's not a bad idea to at least look at the long-hand way to do it.  Google "grub windows default".  I got lots of returns.

---

### Post by Aurora@FleetBuzz on 2008-02-28
Many thanks, Bartender, for that suggestion!  I'm not a "command line guy", so anytime I can stick to a GUI, I'll go that way.

BTW, your avatar speaks volumes about those of us who just can't resist the urge to find out how things work!  :)

---

### Post by sayakb on 2008-02-28
> **Aurora@FleetBuzz said:**
> Many thanks, Bartender, for that suggestion!  I'm not a "command line guy", so anytime I can stick to a GUI, I'll go that way.

BTW, your avatar speaks volumes about those of us who just can't resist the urge to find out how things work!  :)

Also, after installing Ubuntu, don't forget to install Wine (Windows emulator), since you may need to run your EXEs (Windows executables) and setups under Linux also. 

Open a terminal and type:
```
sudo apt-get install wine
```

Check your application's compatibility at:
[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by sayakb on 2008-02-28
Get good Linux softwares from here:
[www.getdeb.com](www.getdeb.com)

Get good customizations and eyecandies from here:
[www.gnome-look.org](www.gnome-look.org)

While installing a software, always check it's version, compatibility and architecture (would be all included in the package name itself). It's safe to download anything using apt or synaptic.

---

