---
title: "Installing to a partition on an external drive"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by FishyFish on 2007-12-28
I'm trying to complete my first Ubuntu install. I downloaded, burned, and booted to my CD yesterday. I then started the install and proceeded until I ran into the partitioner phase.

After some research I found that I need to choose "Manual" at [http://98115.net:4520/~craigm/ubuntu%20pics/IMG_7370.JPG](http://98115.net:4520/~craigm/ubuntu%20pics/IMG_7370.JPG) if I want to use an existing partition.

I selected "Manual" and was presented with 14 partitions (My external has 3, and my internal has 1. I don't know about the others) - [http://98115.net:4520/~craigm/ubuntu%20pics/IMG_7372.JPG](http://98115.net:4520/~craigm/ubuntu%20pics/IMG_7372.JPG)

The names which were given before ( [http://98115.net:4520/~craigm/ubuntu%20pics/IMG_7369.JPG](http://98115.net:4520/~craigm/ubuntu%20pics/IMG_7369.JPG) ) were gone.

I wish to install to "Linux Drive" which is "Mac OS Extended (Journaled)" (HFS+). My firewire external drive has a few partitions which I made with Disk Utility on Mac OSX 10.5.1 (Leopard). See [http://98115.net:4520/~craigm/ubuntu%20pics/Picture%202.png](http://98115.net:4520/~craigm/ubuntu%20pics/Picture%202.png)

How can I install to "Linux Drive"? I want to avoid accidentally erasing my OSX install (On Macintosh HD). I do have backups, but they potentially at risk because I want to install linux on "Linux Drive", a partition of my backup drive. (I think I will make a third backup of just my data on another external which I will disconnect) Disconnecting the internal drive can be done if needed, but it is a pain with Mac Minis.

Another possibility is that I could spare a few GB (2, the minimum?) off my internal for the Ubuntu system install and keep all other documents, applications and such on the partition on my external. Is there anything special I would have to do to make it work this way? I would just disconnect the external and choose "Guided - Use largest continuous free space" correct?

Looks like the second possibility is probably easiest. Any other advantages ether way? (other than hard-drive space use and ease of install) I really just need a good way to test Linux versions of software. (Of course there are other benefits to having an Ubuntu install!)

Also, I can drag my mounted partition onto the installer (which launches it) but it does install to it (It launches normally). I'm not sure if applications in Ubuntu can restrict what files can be dropped onto them, but if they can, it is a bug. It should ether offer to install to the dropped partition or not accept the file drop.

Thanks for your time,
- Craig

---

### Post by Q4U on 2007-12-28
If you did not press "write changes to disc" at the end of the partitioning stage then it's normal that the names assigned on your previous install attempt "disappeared" (actually they were never written in the first place).

Sorry can not help with the rest as the attached JPG's don't load in my browser. So I don't want to say anything without having had a chance to look at your drives layout.

---

### Post by FishyFish on 2007-12-28
The names that did not show up were the names assigned on my Mac. The names showed up correctly on the partitions that mounted on my desktop when I first booted to the CD. They do not show up correctly (or at least not how I expected) in the partition thing in the installer. I have never pressed "write changes to disk" because I have no way to tell what I'm writing over. I don't know partition is witch because I have no idea what "/dev/sdb7" is for example. I don't even have 7 partitions total as far as I know. I was expecting to see "Linux Drive" which was mounted on my desktop. I have four 134 MB "free space" partitions and a 0 MB one (The CD?).

Those images are a tad large so I will scale them down. (They should be fixed in about 2 minutes) (Edit: Pics now much smaller and cropped)

Thanks!

---

### Post by candtalan on 2007-12-28
I support your caution in such a situation. I would do some initial investigation using something like a partitioner live CD (such as parted magic live cd or gparted live cd?) and without changing anything (!) just look around, see to identify what you can understand etc, and be more confident in what you have. The partition sizes, file systems, and locations can often be used to help confirmation.

Be aware that installing onto an external drive will be convenient mostly only if the boot directory is located in a (small, megabytes) partition on the internal drive. This will allow the removal of the external drive and continue to allow the internal drive OS's to boot ok.

---

### Post by Q4U on 2007-12-28
Sorry, still no luck with the images: seems like I can not connect to the website (office firewall?).

Anyway, cantalan is right of course: the easiest way to see the partitions is to run a liveCD. Mount each partition and check things such as the size and files inside to make sure you know which is which.

After you have done this, you can go ahead with your idea, even if this post from February describes some problems you might encounter: [http://ubuntuforums.org/archive/index.php/t-356529.html](http://ubuntuforums.org/archive/index.php/t-356529.html)

---

### Post by FishyFish on 2007-12-28
I think I'm going to just avoid the whole issue and install to a 2-3 GB partition on my main drive. The 37 GB slot on my external is nice, but I don't need much space for debugging apps one at a time.

I will explore the partitions some time later (with a Live CD or some other method).

I thought I could just install to my partition (after all, it did mount when using the Live CD) and boot to it my holding option to select a boot disk, but it seems to be more complicated. I don't have much time to spend on it now so I will do the easy thing.

I don't know why the pics don't work. I have the port routed through the fire wall to apache. My CGIs there seem to work for people. Strange...

Thanks for the help guys!

---

### Post by FishyFish on 2007-12-28
I decided to try to add an Ubuntu partition to my internal. Didn't work.

Attached (see below) are two pictures, one with Ubuntu's partitioner application showing over 30 GB of free space, and the other showing the installer failing to find enough free space.

What am I doing wrong?

---

