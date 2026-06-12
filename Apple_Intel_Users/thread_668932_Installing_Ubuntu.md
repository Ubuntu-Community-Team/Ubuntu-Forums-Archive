---
title: "Installing Ubuntu"
date: 2008-01-15
forum: Apple Intel Users
---

### Post by Death_To_The_World on 2008-01-15
Hi everyone,

I want to install Ubuntu on my macbook and dual boot OS X and Ubuntu. Without Windows sense I do not have a windows install disk or like windows. I took a look at [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)  but as it says Bootcamp is discontinued and it doesnt say how to partition the hard drive. I also made a live cd but nothing happens when i press C at start up. It said it had to be converted from .ISO to .ISO.dmg could this be why? 

And last but not least....
Is there a way to get World of Warcraft to work on Ubuntu?

Thank you.

---

### Post by cyberdork33 on 2008-01-15
download the Ubuntu image and burn it to disk. There is no conversion needed.

You are going to have to shrink your OSX partition to make room for Ubuntu. Gparted and parted magic are capable of doing this.

---

### Post by Sef on 2008-01-15
Do you have an intel or PPC Apple?

---

### Post by Death_To_The_World on 2008-01-15
I believe it is Intel. I'll try burning ISO. and Gparted.

---

### Post by Death_To_The_World on 2008-01-16
It booted up into the GUI and I went to check the disk for errors but it seems my enter button isnt working so I couldn't pick anything. I tried spacebar as well and that didn't seem to do anything either. I also let it count down to 0 for it to start up and nothing happened :[

I burned the ISO to dvd with Toast.

---

### Post by cyberdork33 on 2008-01-16
> **Death_To_The_World said:**
> It booted up into the GUI and I went to check the disk for errors but it seems my enter button isnt working so I couldn't pick anything. I tried spacebar as well and that didn't seem to do anything either. I also let it count down to 0 for it to start up and nothing happened :[

I burned the ISO to dvd with Toast.

This keyboard firmware bug was suppossedly fixed with the round of Apple firmware updates... unfortunately, there is no sure way to get to work. I used to be able to unplug my keyboard on my iMac, then plug it back in to get it to work, but that no longer works for me.

I find that burning linux iso files on a Mac can be very buggy. First, try the CD image instead of the dvd image, and make sure you burn at a very low speed to avoid errors. good luck.

P.S. If it is a "Macbook" and not an "iBook" or "Powerbook" then it is an Intel Mac.

---

### Post by samuelsner on 2008-01-16
i've installed a few flavors of linux on my Macbook (Sabayon, Fedora, Ubuntu,) have burned all the iso's with Toast and have yet to encounter that problem.  All of them were installed after I updated the firmware, so my obvious question is: have you updated your firmware?

if you're still looking to resize your OSX partition, try using the diskutil command via the terminal.  (simply typing diskutil will bring up a list of uses)  this is just your normal Disk Utility app included in OSX but for some reason, when accessed via the terminal, you have more functionality.  where it would be of use to you is in its option to dynamically resize partitions without erasing data, just like gparted.  i find it more convenient to use this command rather than boot up a linux live cd to access gparted.  

check out: [http://www.commandlinemac.com/article.php/20071206112304635](http://www.commandlinemac.com/article.php/20071206112304635)   for a how-to on diskutil.  

hope this helps!

---

### Post by grammataki on 2008-01-17
> **Death_To_The_World said:**
> Hi everyone,

I want to install Ubuntu on my macbook and dual boot OS X and Ubuntu. Without Windows sense I do not have a windows install disk or like windows. I took a look at [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)  but as it says Bootcamp is discontinued and it doesnt say how to partition the hard drive. I also made a live cd but nothing happens when i press C at start up. It said it had to be converted from .ISO to .ISO.dmg could this be why? 

And last but not least....
Is there a way to get World of Warcraft to work on Ubuntu?

Thank you.

I learnt this the hard way to but found it on a post on the net.  In order to burn ISO discs, you need:

1 - download the iso file (which you have done)
2 - open up disk utility
3 - drag the ISO file into disc utility without opening it up at all, just drag the iso in there
4 - go to the top of the menu in disk utility and press burn

Your disc should boot up then but just to be sure and save you time, open up system preferences and choose start up disk.  If the disk is there it should say foreign OS or something, if its there, you can now boot from it.  Hope this helps.



Grammatis

---

