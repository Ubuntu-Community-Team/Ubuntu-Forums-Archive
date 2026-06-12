---
title: "can't repartition XP with Live CD"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by Obi-Wan on 2006-12-27
My thanks in advance for all your help. 
I have a Sony Vaio laptop. It currently has been reformatted about 4 times now trying to get this Linux install correct. In th epast it has been an id10t error on the operator side. Being new I tend to make a lot of mistakes. Reformatting is rough but at times takes less time. 

I am trying to set up a dual boot on this machine. It has a 30GB HDD with 256MB RAM. I have WinXP set up and it's on hdla1. I have it partitioned to take the whole 30GB thinking I could use the Live CD (with GParted) to resize and then install Ubuntu 6.06 Dapper. The problem I'm facing now is that on three different attempts Gparted has failed to resize. It' states that there isn't enough room. I only have 5 GB taken up with WinXP so there is at least 22GB free. 

I get this error when I let Gparted automatically set it for 50%. Of course I also get it when I try to go manual also. It just won't accept anything. I don't know if Live GPArted with help and being new to the iso files I tend to mess those up as well. That's why I had a CD sent to me from Ubuntu. 

Can someone help me figure out what is wrong and what I need to do to correct this? I really don't want to reformat if I can help it but I will if necessary. I just tired of all of the MS downloads, reboots, etc. I'm tired of wasting time by having to repeat everything over and over again. 

I do want to use Gnome with Dapper.

---

### Post by ron999 on 2006-12-27
Hi

It sounds to me like you have the right idea.

Boot from the Live CD and use GParted (Gnome Partition Tool) to partition your drive.

Do this before you even try to do the install.

Try partitioning your drive 15GB/15GB and reformat the new partition as type ext3.

If it's any consolation to you, it took me several attempts to sort mine out.

I don't know why it's telling you 'not enough room'.

Try again (carefully), just persevere.

Good luck
:)

---

### Post by Bartender on 2006-12-27
Obi-
I don't know if this will help, but I'd sure try the GParted LiveCD (GPLCD) again.  What sort of burning utility are you using?  XP's default burner can't do it right.  Stupid Microsoft.

This utility has been recommended for doing the conversion from .iso download to bootable CD

[http://imgburn.com/](http://imgburn.com/)

You can't resize a partition that's mounted.  I think (don't understand this entirely but it's just a feeling after reading numerous threads) that has something to do with why you can't resize from the installer CD sometimes.

Try using imageburn to make yourself a GPLCD.  Then boot from the CD just like you would an install CD and see if you can make the changes.

EDIT:  If you succeed in making a separate primary partition in GPLCD, set it up as ext3.  When you go back to the Ubuntu install CD, use the manually edit partition table option, not the resize option.

---

### Post by jvc26 on 2006-12-27
Sounds like you're going the right way about it, it may be a matter of trying the 50/50 split that ron999 tried. Get the new ubuntu partition formatted as ext3, and put in a small swap partition. Then try installing again. I think it could just be a matter of trying again, or maybe if there is a fault with the livecd, and its not unknown to have a problem with one of the downloads, then you could try downloading the livecd again or the GParted CD.
Good luck!
Il

---

### Post by MrKlean on 2006-12-27
Just a comment I didn't see mentioned...Defrag your hd first.. before you run gparted.  It might save you problems in the long run ; )

---

### Post by Bartender on 2006-12-27
I'm adding an attachment.  I spent half of Christmas Day making this.  It's geared toward creating the proper partitions for an all-Linux dual boot but it might still help you get a feel for moving around in the GPLCD environment.

Well, that didn't work.

It's attached to post #9 in this thread

[http://www.techsupportforum.com/alternative-computing/linux-support/131773-dual-linux-os.html](http://www.techsupportforum.com/alternative-computing/linux-support/131773-dual-linux-os.html)

---

### Post by ron999 on 2006-12-27
Hi

Yes, defragging XP first might help.

I suggested the 50/50 split as a starting point, you can shuffle the partitions around after install if you wish.

If you're using a shipped Ubuntu CD then it's probably OK, not a burning error, specially if the desktop loads OK.

If you boot from CD then none of the drives are mounted, so that's not an issue (imho).

No need to worry about setting up a swap file until you come to do the install. 
:)

---

### Post by Obi-Wan on 2006-12-27
I did the defrag twice just to make sure. Ha. After all it is windows. I was using Easy CD Creator 5 by Roxio but that cd isn't wanting to come up. I think I may have burned it wrong. As this is my first experience with this sort of thing could someone explain the steps necessary to burn the right image and such? This one is sort of weird to me. After 9 years with nothing but windows you can probably get an idea. thanks.

---

### Post by ron999 on 2006-12-27
Hi obi

Why do you need to burn an image?

Did you not say that Ubuntu had shipped you a Live CD by post?

---

### Post by Obi-Wan on 2006-12-27
Correct but Live CD from Ubuntu won't create the partition needed to install Ubuntu. I have created a GPLCD and I'm attempting to create the partition as we speak. Multi-tasking isn't always that much fun. I just received an error message from GPLCD indicating that the HDD has a bad sector. Funny this didn't come up when I defragged. In fact it states "This software ahs detected that the disk has at aleast 8 bad sectors. I guess that could be the reason?????

---

### Post by moshuptrail on 2006-12-27
Absolutely.  If there are any bad sectors, Gparted will not shrink the partition.
You will need to use a command line utility, ntfsresize.  As luck would have it, it's on the Live CD.  Just open an aterm.  BUT FIRST, you should read up on resizing a partition using ntfsresize.  It's not that bad after you've done it a few times, but to the un-initiated it can be daunting.

---

### Post by Obi-Wan on 2006-12-28
ok, silly question. Would I be better off plugging in a second HDD to my desktop computer and installing Ubuntu there (so that I can learn this software) or to keep trying to do a dual boot on my laptop? I beginning to think I may have bitten off a bigger chunk than I can handle. The reason for this seems to be all of the problems I'm encountering while trying to set up this dual boot. Would a straight Ubuntu install on it's own HDD be a better answer until I learn the in's and out's?

---

### Post by Bartender on 2006-12-28
Obi -
Can you afford to buy a replacement HDD for the laptop?  If it's got bad sectors now it's probably just going to get worse until the drive fails completely.
I was gonna say "get a replacement, download the utility from the HDD manufacturer, copy your existing data to the new one" but I don't know how to do that with a lappy.  Desktops are easy what with all the extra plugs...

Anyway, however you'd go about doing that, I'd move my existing data to a new HDD then take another shot at partitioning.

I had no idea GParted could identify bad sectors and warn you about them.  That's pretty neat!

---

### Post by ron999 on 2006-12-28
It's your call obi

If you have an old PC somewhere then you could rob the hard drive out of it and put it in your desktop PC. You only need a small drive to experiment with - a 4GB or 6GB would do the trick.
You can use it on its own or if you want to dual-boot then connect the drive as a slave. Install Ubuntu on it using the Live CD.
There's a write-up here showing how to use two drives:-[http://www.ehomeupgrade.com/entry/2622/how-to_dual-boot_install]("http://www.ehomeupgrade.com/entry/2622/how-to_dual-boot_install")
:cool:
But you don't need two separate hard drives on your desktop PC, you could just partition the existing one.

---

### Post by Obi-Wan on 2006-12-29
I went in and did a chkdsk through Windows with /f. It came back with 32mb of bad sectors. Good grief!. Anyway, I have lots of extra HDD laying around from all of the computers that I have worked on in the past and scavenged parts from. Never know when one of your kids will kill something on a computer! My laptop though is a different story. I just got it. Used of course but I didn't think I would have problems this fast. I'm heading to the website to download tools from the manufacturer to see if I can recoup something here. Then to the website of a wholesaler in the area who has great prices. It will be a HAPPY new year! If I get it fixed I will append. I will keep cheking here though because I'm not done with Ubuntu.

---

