---
title: "Partition Help"
date: 2008-03-21
forum: Apple Intel Users
---

### Post by Noob1234 on 2008-03-21
Alright so I have a 15gb partition that I setup using bootcamp.  Can somebody tell me exactly what to do from here, I was very confused when I went to install using the Live cd, mostly with what partition options I needed to choose from there.  A very noob friendly set of directions would be helpful.

---

### Post by sandysandy on 2008-03-21
r u dual booting or doing a single OS install

have a look here

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

regards

---

### Post by Noob1234 on 2008-03-21
dual

OSX/Ubuntu

---

### Post by tagra123 on 2008-03-21
This page contains a lot of details for installing Ubuntu.

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

At the bottom of the page

[https://help.ubuntu.com/community/forum/installation/Partitioning](https://help.ubuntu.com/community/forum/installation/Partitioning)

and there's this too

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Some good reading to help you understand more about partitions.

---

### Post by sandysandy on 2008-03-21
> **Noob1234 said:**
> dual

OSX/Ubuntu

have a look 

[http://ubuntuforums.org/showthread.php?t=719101&highlight=mac+dual+boot](http://ubuntuforums.org/showthread.php?t=719101&highlight=mac+dual+boot)

[http://ubuntuforums.org/showthread.php?t=594298&highlight=mac+dual+boot](http://ubuntuforums.org/showthread.php?t=594298&highlight=mac+dual+boot)

[http://ubuntuforums.org/showthread.php?t=721278&highlight=mac+dual+boot](http://ubuntuforums.org/showthread.php?t=721278&highlight=mac+dual+boot)

[http://ubuntuforums.org/showthread.php?t=573611](http://ubuntuforums.org/showthread.php?t=573611)

regards

---

### Post by blznazn on 2008-03-21
First I recomend installing rEFIt.  Then restart and hold the alt/option key.  Select to boot rEFIt.  Then reboot again with the Ubuntu Live CD in.  When rEFIt starts pick to boot from the cd.  When installing select the 15 GB partition in manual partition manager (set it as "/"). to install on.  You don't have to create a swap space even though it's recomended.  Then before hitting install tell it to install the boot manager on /dev/sda3(sda1 if EFI, sda2 is OS X, and sda3 should be Ubuntu).  If you have a newer mac you can use 64 bit even though you'll run into a few more problems.

---

### Post by Noob1234 on 2008-03-22
Just tried it, when i select ubuntu in refit it say no bootible device found - please insert boot disk and press any key.

what happened?

---

### Post by blznazn on 2008-03-22
The boot manager needs to be installed on the ubuntu drive.  When you tried it, when you select where to put the boot manager it should be on /dev/sda3 (on mine it was 3).  I got that same message my first time.  It's a little tricky getting it right.

---

### Post by Noob1234 on 2008-03-22
> **blznazn said:**
> The boot manager needs to be installed on the ubuntu drive.  When you tried it, when you select where to put the boot manager it should be on /dev/sda3 (on mine it was 3).  I got that same message my first time.  It's a little tricky getting it right.

What do I need to do to fix this?

---

### Post by blznazn on 2008-03-22
I recomend trying to reinstall ubuntu again on the same partition.  Just like keep track of the partition it's on "/dev/sda something" and use that for the partition to install the boot loader.

[edit]

if you type Ubuntu MacBook (in firefox), they have a whole guide on everything.  Sorry I confused you, I triple boot, so I had to go about things kinda differently.

---

### Post by Noob1234 on 2008-03-22
> **blznazn said:**
> I recomend trying to reinstall ubuntu again on the same partition.  Just like keep track of the partition it's on "/dev/sda something" and use that for the partition to install the boot loader.

WTF did I do wrong?

I put the CD in. Launched.  Then clicked the install icon on ubuntu desktop.  Figured out my time location etc.  Then i got to the partition part.  Clicked manual.  Then clicked on the spot where i wanted to put ubuntu (i partitioned 15g of space for it).  Cicked ok and it said something like you need to put it in the correct spot.  So i put in sda3 with root of "/" then clicked ok.  It gave me a warning that if i didnt do something else i may have trouble with something but i forgot what it was.  What else do i need to do next time (im going to try and reinstall on same partition).

Thanks (please make it as easy as possible, step by step would be great)

EDIT: i used the guide and this is what happened.

---

### Post by blznazn on 2008-03-22
The thing it said was about making a swap space.  But on the last part (step 7 I think), it should have a button for like advance options or something like that.  When you click it, put the partition ubuntu is on for the install location for the boot loader (/dev/sda3 if that's the partition ubuntu is on).  [http://foxdemon.net/nerdish-things/68/triple-booting-macbundows](http://foxdemon.net/nerdish-things/68/triple-booting-macbundows) << that's my blog on tripple booting.  It should be like that, except don't make a windows partition.  What version and cd are you using?  I used the Live CD.

---

### Post by cyberdork33 on 2008-03-22
> **blznazn said:**
> I recomend trying to reinstall ubuntu again on the same partition.  Just like keep track of the partition it's on "/dev/sda something" and use that for the partition to install the boot loader.You do not need to reinstall ubuntu, and you do not have to move the bootloader. This is very simple, and for some reason, everyone is making it difficult.

Before you do anything more, please boot from the Ubuntu LiveCD and check what your partitions look like. You can use the partition editor for this. System > Administration > Partition Editor

If you want to just reinstall, then in partition editor, delete the partitions at the end of the disk after your OSX partition (probably an ext3 partition and a swap if one was created....) you should end up with the EFI partition, the OSX partition, and a bunch of blank space.

Once you are done there, start the Ubuntu Installer. When prompted, choose to install to the largest free space. Ubuntu will handle the rest. There is no need to move the bootloader on a dual-boot system, so the default should be fine.

---

### Post by Noob1234 on 2008-03-22
> **cyberdork33 said:**
> You do not need to reinstall ubuntu, and you do not have to move the bootloader.

I have reinstalled it twice with same results. I dont know what to do differently?

---

### Post by cyberdork33 on 2008-03-22
> **Noob1234 said:**
> I have reinstalled it twice with same results. I dont know what to do differently?
please see my updated thread.

---

### Post by Noob1234 on 2008-03-22
> **cyberdork33 said:**
> please see my updated thread.

Finally got it installed and running good with refit.  Next is to figure out the wireless issues.  Im going off of what this thread says.
[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

Those commands, where do I type them in? Or how do I install what they are talking about? And how does it download the driver with no connection?

---

### Post by cyberdork33 on 2008-03-23
> **Noob1234 said:**
> Finally got it installed and running good with refit.  Next is to figure out the wireless issues.  Im going off of what this thread says.
[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

Those commands, where do I type them in? Or how do I install what they are talking about? And how does it download the driver with no connection?

Pretty much any commands you see are typed in a terminal. Most people try to distinguish terminal commands by placing the commands in code tags```
like this
```

You can follow those directions, but I don't know that the dell driver will work. Someone claimed that it worked earlier, but most have been having to use the driver off the leopard restore dvd that came with your Mac. There also seems to be a bug with ndiswrapper in Hardy, so if you are using Hardy, then there are some extra steps.

---

