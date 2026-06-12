---
title: "Can't see webpage videos in firefox, epiphany"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by Cheese Sandwich on 2007-04-28
The videos (such as in youtube) aren't showing up. I've followed the instructions in the multimedia how-to sticky (though the last command ended with:

> sudo apt-get install libdvdcss2 w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

), and I also ran some sort of "nspluginwrapper" script I found elsewhere here. Still no luck. Enabled all video-plugin related stuff I could find in Synaptic, as well, but no dice.

I'm running ubuntu64 on an AMD64 acer laptop...

-Thx

---

### Post by jmagsho on 2007-04-28
You're missing Flashplayer.   That's what all the Youtube videos are typically using for a media format.

The easiest (and quite frankly most noob friendly way to install this and a host of other apps is to use Automatix2.

You can get a copy here: [http://getautomatix.com](http://getautomatix.com)

This should help with the Flash issue and the ndiswrapper (windows proprietary wifi driver) issues if you're having any as you might have mentioned (although it seemed like you may have installed trying to get the videos working?)

---

### Post by JenniferRa3 on 2007-04-28
Hi yes I am new to Ubuntu and am having the same problem. However I have already downloaded the flashplayer on my desktop I just can not figure out the commands in terminal. Is there anyone that would be willing to help me, so that I can learn to navagate to the file?? 
I am running Drapper Drake 6.06 on a 1.5gig 2gigs ram 40gig HDD Toshiba Laptop.

I downloaded the TGZ flash player titled.   

install_flash_player_9_linux.tar.gz    which is chillin on my desktop just can't install it properly...

:KS

---

### Post by mgmiller on 2007-04-28
> I downloaded the TGZ flash player titled.

install_flash_player_9_linux.tar.gz which is chillin on my desktop just can't install it properly...


That is not how you want to install it.   Make sure you have multiverse enabled in synaptic package manager.  Go to  Settings>repositories and put a check mark next to the universe and multiverse listings.  

Then just do a package search on flashplugin-nonfree and install that.

If you want to do it from command line, after enabling the multiverse repository,  the command is:

```
sudo apt-get install flashplugin-nonfree
```

But since you are already in synaptic, it's easier to just do it from there.

---

### Post by fwojciec on 2007-04-28
I would suggest seeking help in the x86 64-bit Users forum, flash on 64bit systems is tricky (as are some other programs) - but certainly doable.  Consider whether you actually need a 64-bit version of Ubuntu - I'm running 32-bit version even though I have AMD 64 X2 processor - the advantages of 64 bit version are, at this stage, debatable for normal computer use.

---

### Post by JenniferRa3 on 2007-04-28
Just wanted to say thank you to mgmiller. Your help was apprciated greatly. 

Worked like a charm!

-Jennifer :KS

---

### Post by mgmiller on 2007-04-28
> Just wanted to say thank you to mgmiller. Your help was apprciated greatly.

Worked like a charm!


You are very welcome.  :lolflag: 

Remember,  Linux is not Windows.   Any time you want software, look in syanptic package manager or in Applications>Add Remove.  by doing it this way, you are sure you're getting an Ubuntu optimized package with all the dependency issues solved.  It will also automatically keep it updated for you.   

Have fun.  :popcorn:

---

