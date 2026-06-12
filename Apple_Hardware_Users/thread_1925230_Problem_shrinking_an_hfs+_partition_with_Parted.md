---
title: "Problem shrinking an hfs+ partition with Parted"
date: 2012-02-14
forum: Apple Hardware Users
---

### Post by Lensilvan on 2012-02-14
Hi,
[LEFT] I have a PowerBook G4 [http://www.everymac.com/systems/apple/powerbook_g4/stats/powerbook_g4_1.5_12.html ]("http://www.everymac.com/systems/apple/powerbook_g4/stats/powerbook_g4_1.5_12.html")
where I tried to install Lubuntu 12.04 in dual-boot with Mac OS 10.4 already installed, using the Lubuntu live-CD and GNU Parted. Since the CD drive is broken, I used a Live USB to boot from it. While booting, the following message appeared:
```
Bootstrap partition type is wrong: "Apple_HFS" type should be: "Apple_Bootstrap"

```Then, I arrived in the LXDE desktop without problems. I then run Parted in the terminal to shrink the existing Mac partition, to make place for the Linux partitions. I then run:
```
resize 3 134MB 35GB
```where 3 is the hfs+ partition number, beginning at 134MB and ending at 55GB. Here, I wanted to   to shrink the partition at 35GB.
But it replies with the following error:
```
Error: Unable to satisfy all constraints on the partition.

```I then tried this:
```
resize 3 134 35000

```Same error message. 
It's odd because I have disabled the Journaling in Mac OS X  and the values I gave for shrinking correspond to the unused space in the hfs+ partition. I checked the md5 sum of the downloaded USB image. I'm sure that it isn't a Parted bug, I had the same problem with a Xubuntu 10.04 live CD. 
Should I use Gparted instead, although I didn't find in the internet someone who used it for shrinking a Mac partition in Powerpc? 
Or, why can't I shrink with Parted?


[/LEFT]

---

### Post by rsavage on 2012-02-14
Don't worry about the bootstrap error.
 
Can you try out the automatic resizing feature of the installer please?  If you choose the install alongside existing operating system option it should give you a slider to adjust your partitions. It is a testcase that we have to complete on the installer and I don't have Mac OS X. 
 
Remember to backup any important files before doing any re-partitioning.

---

### Post by svtguy88 on 2012-02-15
I actually ran into a resize problem earlier today.  I was using the resize command, and it gave some warning about HFS filesystems/Macs and it being incompatible.  It also said to use Gparted froma live-CD, as Rsavage has suggested.

I'd say try the resize option from the GUI on the live-CD.  I've set up a dual boot (OS X/linux) before on PPC machines, and I usually ended up using OS X to shrink the Mac OS partition, and then installed Linux to the newly created free space.  The live-CD's installer (whcih is Gparted at heart) should do the same thing.

I didn't realize this was a test case.  If it still needs to be tested, I could track down an OS X disk (it's here somewhere) and see how the live-CD handles resizing on my Powerbook...

---

### Post by rsavage on 2012-02-15
Well it is not Mac OS X specific, but I thought it would be a good idea to test it [http://testcases.qa.ubuntu.com/Install/DesktopResize](http://testcases.qa.ubuntu.com/Install/DesktopResize) .  I did actually recently acquire a hard drive with Mac OS X on, it's just not in my machine at the moment.  So I can do the test too, but I won't be able to check if files have been wrongly deleted because I don't know what should be on the hard drive!

---

### Post by richerdey on 2012-05-03
If you want to install a new operating system in your mac computer without replacing previous OS then you need an advanced [partition mac]("http://www.partitionmac.com") software by which you can easily perform partitioning process without losing any important data. This application provides users easy to use GUI interface by which any one can use this application to create, edit, delete and modify your mac partitions.

---

