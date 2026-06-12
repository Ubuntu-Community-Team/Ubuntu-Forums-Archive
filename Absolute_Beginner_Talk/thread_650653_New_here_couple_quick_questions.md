---
title: "New here couple quick questions"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by gruss on 2007-12-26
Hi all been playing around with Ubuntu and xubuntu for a cuople weeks, mostly in VMware but did an install on an older notebook a few days ago.  After seeing Vista I wanted an alternative ;)
Anyway, I kind of want to convert my older PIII with tons of HD space to Ubuntu or X ubuntu but I have some wacky hardware in it, is there a quick little prog out there to test compatibility?  Just want to know what I'm up against.  Mostly want to know if my trendnet usb network adapter will work cause I dont want to run a cable upstairs. If I can get the internet working I can figure out the rest.

BTW Nice forums here, I've meddled with linux before and have found some places to be a little "standoffish" but seems pretty newbie friendly around here so kudos and searching around has actually solved a couple probllems already.

---

### Post by ncappel1 on 2007-12-26
You could try using a live cd first, test it out to get the feel and if you like it, install, if not, no one is offended!

---

### Post by overdrank on 2007-12-26
> **ncappel1 said:**
> You could try using a live cd first, test it out to get the feel and if you like it, install, if not, no one is offended!

+1 and feel free to ask away and welcome.:KS

---

### Post by p_quarles on 2007-12-26
According to the [hardware support wiki]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported"), trendnet USB adapters will require you to install the Windows driver using ndiswrapper. So, no, it probably won't work with the live CD, but you will still be able to get it working after a bit of fiddling.

---

### Post by jan quark on 2007-12-26
> BTW Nice forums here, I've meddled with linux before and have found some places to be a little "standoffish" but seems pretty newbie friendly around here so kudos and searching around has actually solved a couple probllems already.

Ubuntu stands for humanity, not for an avantgarde-nobody-can-understand-highfalutin-overblown-err.. thing.

So ask, and replies will be immediate. 
:)

When you encouter problems with the internet there are hundreds of people who already had your problems and are eager to help.:)

---

### Post by gruss on 2007-12-26
Yeah I thought about that after I hit enter...but the quick replies are impressive.  
OK heres a better one, any good file recovery software for ubuntu?  I had a HD that was placed in an el cheapo box to convert to USB/firewire that one of the partitions bit the dust(NTFS).  Well not really just something corrupt, so the pc can't see the files.  "getdataback" will "see" the files, when I put it in this PC, but I don't wanna blow 80 bucks right now.  I have the data saved in other places so its not a big deal, but I was hoping to restore them cause thats where they're the most organized and I'm terribly lazy ;)  
Think I'll go throw the cd in that pc now and see what happens.  Thanks again folks.

Hmm ndiswrapper, havent had to use that yet...oh well always a good time to fiddle.  guess I could always take a notebook up there and share the internet connection until I straighten out the wireless.  Or I'll look through the Wiki i just saw posted and find hardware that works oputta the box...prolly some good sales right now!

---

### Post by p_quarles on 2007-12-26
The standard data recovery tool for Linux is testdisk. There may also be a GUI front-end for it, but I'm not aware of one off the top of my head.

---

### Post by gruss on 2007-12-26
Hmmm..Live CD never started on that pc.  Just hung up, got the wallpaper but nothing else.  
I didnt think there was anything in it that would keep it from booting.
Its an old Midwest Micros (Systemax) PIII 450 with 392 meg of Ram.
I think its an Intel BX440 chipset, not sure why I remember that but it was relevant during some install or another.
I do have an IDE controller card installed taht I don't remember the brand, but I could see it not working but not stopping a boot, a USB 2.0 card and an Audigy gamer soundcard.  Anything ring a bell with you pro's?  I"m going to go try to check out that hardware but thought that was kind of wierd since ubuntu had no issues other than being slow on the live cd (but installed flawlessly) on a PIII compaq Armada notebook (which I always needed to grab drivers for windows)

---

### Post by p_quarles on 2007-12-26
The live CD doesn't work for every computer. You'll probably have much better results with the alternate installation disk, though you won't be able to test drive it.

---

### Post by gruss on 2007-12-26
Ur probably right, pcs fairly slow, prolly try xubuntu and load to the hd that lost the data, I think I have a 10 gig partition on there that I used for transfers so no "real" data to lose and should be plenty for the OS? 
Thanks again

---

### Post by cjm5229 on 2007-12-27
If  you have Windows installed try Wubi,  it will install Ubuntu into Windows and let you test drive it that way. [http://wubi-installer.org/index.php](http://wubi-installer.org/index.php)

---

