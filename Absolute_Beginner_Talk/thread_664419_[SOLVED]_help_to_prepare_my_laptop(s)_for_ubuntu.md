---
title: "[SOLVED] help to prepare my laptop(s) for ubuntu"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by paraglider on 2008-01-11
Hello!

I´m a total noob that just got a brand new Sony Vaio VGN-FZ21S laptop with vista preinstalled, and I need some help before I try to stick ubuntu on my beloved laptop. I also want to get rid of XP on my old laptop.

Here go my questions:
[LIST]
[*]I want to keep vista, so i defragged, shrank the C: partition and created a new partition. My HD has 186GB (on the docs it said 200 , so I feel slightly decieved by sony) but I could only shrink C: by 65GB. I´d like to dedicate at least an extra 35GB to ubuntu... haw can I shrink my C: drive further.

[*]Can I keep my music, photo´s, videos and other docs on a partition that can be read by both vista and ubuntu?

[*]Is there an itunes for ubuntu? Can i sync my Ipod from ubuntu?

[*]Whats the diference between gnome and KDE?
[/LIST]

I also have a compaq presario 900... slightly the worse for its use (battery died long ago, some days CD-DVD drive works, most it doesn´t, in summer when its very hot it overheats and switches off after 3 min, sometimes it sounds like something out of Alies VS Pred, has a couple of viruses but not as bad as the performance loss when it was running Norton...)
Anyway... i´d like to put ubuntu or some linux distrib. onto it, and then remove windows XP prof once i´m sure most functions work. 
[LIST]
[*]What ubuntu distrib is likley to be most compatible with the presario 900 (athlon processor, 1.5 GHZ i think, 256mb ram, 27GB HD and no idea what kind of graphics card on it)?
[*]Is there any way I can boot and install it if my CD drive doesn´t decide to work again -out of some mistic intervention by the god of fickle laptops-?
[/LIST]

Thats it for now... Thanks a million in advance for anyone who takes the time to answer a poor noob like me!

Happy ubunting!

---

### Post by Xavieran on 2008-01-11
I´m a total noob that just got a brand new Sony Vaio VGN-FZ21S laptop with vista preinstalled, and I need some help before I try to stick ubuntu on my beloved laptop. I also want to get rid of XP on my old laptop.
Yay!:)

Here go your questions:
[LIST]
[*]I want to keep vista, so i defragged, shrank the C: partition and created a new partition. My HD has 186GB (on the docs it said 200 , so I feel slightly decieved by sony) but I could only shrink C: by 65GB. I´d like to dedicate at least an extra 35GB to ubuntu... haw can I shrink my C: drive further.

Boot into the Ubuntu LiveCD and use GParted...it's pretty user-friendly so you shouldn't have any probs...

[*]Can I keep my music, photo´s, videos and other docs on a partition that can be read by both vista and ubuntu?

Yes...again with GParted create a partition with the size that you want and make it Fat32 fat32 is readable by both Windows and *Buntu


[*]Is there an itunes for ubuntu? Can i sync my Ipod from ubuntu?

Depending on the generation of IPod you can...very new IPods may not work completely but older (a year or so) ones will work fine...you can use gtkpod for this...

[*]Whats the diference between gnome and KDE?

KDE uses the QT Graphical libraries which are not truly free...GNOME is the GNU Foundations implementation of a Desktop Environment (There *is* a reason Ubuntu uses GNOME by default...)
You will most certainly want GNOME...

[/LIST]

I also have a compaq presario 900... slightly the worse for its use (battery died long ago, some days CD-DVD drive works, most it doesn´t, in summer when its very hot it overheats and switches off after 3 min, sometimes it sounds like something out of Alies VS Pred, has a couple of viruses but not as bad as the performance loss when it was running Norton...)
Anyway... i´d like to put ubuntu or some linux distrib. onto it, and then remove windows XP prof once i´m sure most functions work. 
[LIST]

[*]What ubuntu distrib is likley to be most compatible with the presario 900 (athlon processor, 1.5 GHZ i think, 256mb ram, 27GB HD and no idea what kind of graphics card on it)?

You could use 64-bit Xubuntu...there are many many different small distros available so do some research into them...

[*]Is there any way I can boot and install it if my CD drive doesn´t decide to work again -out of some mystic intervention by the god of fickle laptops-?

I think there is,but I knoweth not how :(
[/LIST]

Happy ubunting!

:):)

---

### Post by marufaberlin on 2008-01-11
About syncing IPods:

There is a media player called amarok (don't know it? shame on you!) and that syncs your IPods for you.

---

### Post by lgambett on 2008-01-11
To maximize free space when you shrink a Windows partition defrag must be accompanied by chkdsk /f.
I am succesfully using an Ipod with Amarok (the greatest music player ever made IMHO), gtkpod (which offers more control than Amarok on the Ipod) and ThinLiquidFilm (for transferring videos to the Ipod).

---

### Post by lgambett on 2008-01-11
Sorry, I forgot... Ubuntu reads and writes perfectly on the Vista partition (while the contrary is not true), so you can easily move your files back and forth between Vista and Ubuntu.

---

### Post by jken146 on 2008-01-11
> **paraglider said:**
> I want to keep vista, so i defragged, shrank the C: partition and created a new partition. My HD has 186GB (on the docs it said 200 , so I feel slightly decieved by sony) but I could only shrink C: by 65GB. I´d like to dedicate at least an extra 35GB to ubuntu... haw can I shrink my C: drive further.
You'll only need 10-15 gigs for / and then up to 1 gig of swap, if you plan on leaving your personal files on the NTFS Windows partition.  The 186 vs. 200 thing is all about the way you define a gigabyte... [http://en.wikipedia.org/wiki/Gigabyte](http://en.wikipedia.org/wiki/Gigabyte)

> Can I keep my music, photo´s, videos and other docs on a partition that can be read by both vista and ubuntu?
Yes, Ubuntu will read/write to NTFS partitions.  It'll probably save you some shrinking trouble if you leave everything on the Vista partition.

> Is there an itunes for ubuntu? Can i sync my Ipod from ubuntu?
No, Apple only makes itunes for Mac and Windows, although most ipods can be synced with Rhythmbox or Amarof ot Gtkpod amongst others.  You can't buy music from the itunes store.

> Whats the diference between gnome and KDE?
[http://www.psychocats.net/ubuntu/kdegnome](http://www.psychocats.net/ubuntu/kdegnome)


> I also have a compaq presario 900... slightly the worse for its use (battery died long ago, some days CD-DVD drive works, most it doesn´t, in summer when its very hot it overheats and switches off after 3 min, sometimes it sounds like something out of Alies VS Pred, has a couple of viruses but not as bad as the performance loss when it was running Norton...)
Anyway... i´d like to put ubuntu or some linux distrib. onto it, and then remove windows XP prof once i´m sure most functions work. 
[LIST]
[*]What ubuntu distrib is likley to be most compatible with the presario 900 (athlon processor, 1.5 GHZ i think, 256mb ram, 27GB HD and no idea what kind of graphics card on it)?[/list]
In theory Ubuntu will work, although you may want to try Xubuntu, which is lighter but still full-featured.

> [list][*]Is there any way I can boot and install it if my CD drive doesn´t decide to work again -out of some mistic intervention by the god of fickle laptops-?
[/LIST]
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation) has a section on installing without a CD drive.

---

### Post by paraglider on 2008-01-11
:):):)


Wow! Thanks a million guys, I really didn´t expect such great and quick answers! Its a real pleasure learning from you!


:popcorn:

Happy ubunting!

---

### Post by anoopjohn on 2008-01-11
You can also check out this set of [[COLOR="Blue"]_instructions on installing ubuntu on system with preinstalled vista_[/COLOR]]("http://www.zyxware.com/articles/2007/12/27/windows/installing-ubuntu-laptops-single-ntfs-partition-windows-xp-or-vista").

---

