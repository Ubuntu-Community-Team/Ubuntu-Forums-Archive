---
title: "Creating Backup of UBUNTU  !"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by B34ST1Y on 2007-12-19
Hey, is there a really easy program to use for gutsy ubuntu 7.10 that can create a partition image that I can burn to a dvd and make a live boot or better yet....an installation that restores my computer to the state its in *right now*   ? ?

---

### Post by kpkeerthi on 2007-12-19
Try [http://www.partimage.org/]("http://www.partimage.org/"). Its included in [System Rescue CD]("http://www.sysresccd.org/")

---

### Post by B34ST1Y on 2007-12-19
Ok, I looked at that one and used synaptics to install and run it under root. It prompts me to unmount my partition (the one I'm obviously on) in order to continue. So....how am I supposed to run it?

---

### Post by kpkeerthi on 2007-12-19
Use system rescue Cd

---

### Post by hyper_ch on 2007-12-19
a while ago I thought that making images backup is great... however then I changed my mind because you'd do that regularly and it just uses a lot of cd-r/dvd-r or whatever... so I changed to file-based backups... I make now backups every 6h back for 90 days.

---

### Post by Sef on 2007-12-19
Get [Clonezilla]("http://gpartedclonz.tuxfamily.org/index.php").  It is a live cd, so your hard disk is not mounted.

---

### Post by Frank Golden on 2007-12-19
Using the Sysrescue CD which has partimage on it make a recovery image
and store it on another partition of your HDD. It is much faster to restore from a partition on your HDD than from a DVD. I have become very proficient at using partimage and use it all the time to backup up Ubuntu and PCLinuxOS 2007.  You can use built-in compression to make the image smaller. 

On my multi-boot (XP Pro, Gutsy,PCLinuxOS) I maintain a rather large Fat 32 partition for sharing files etc. between the various OS's.
This is where I place my images. 

I suggest you create the image to a partition on the same drive as your Ubuntu install. You can copy it to DVD for safekeeping. But always restore from your HDD storage partition.
It is very much quicker.

On my system it takes about 8 minutes to create an image of my 4 GB Ubuntu install. Using the provided Gzip compression the resulting image is less the 2 GB.

Restore takes about 4 minutes. The more ram you have the faster the process should be. Below is a link to a How-to I posted as well as another
adapted by a much better writer than I am. Feel free to PM me if you have any problems or questions.


[http://ubuntuforums.org/showthread.php?t=226402](http://ubuntuforums.org/showthread.php?t=226402)

and

[http://ubuntuforums.org/showthread.php?t=287522](http://ubuntuforums.org/showthread.php?t=287522)

Once you have used partimage a couple of times it will get easier.

Here is a link to where you can get SystemRescueCD.

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

I use partimage to backup my linux distro before making changes that could break things (like updating/installing my ATi 3-D video drivers).
I have to recompile and reinstall the ATi drivers every time a kernel upgrade is performed. On more than one occasion I have rebooted after reinstalling these drivers only to find myself at the command line  with a non-functioning X. Rather than spend time trying to perform dubious repairs, I just dust of my SysrescueCD and do a restore.
I can't count the number of times it has saved me from a complete reinstall.

---

### Post by B34ST1Y on 2007-12-19
I think I'm being misunderstood. I *want* to create a DVD that will install the image that is currently on my HDD....onto any computer of my exact model. I dont want to repartition anything on my hard drive. 


I ran PartImage on the rescuecd....and it somehow ran out of space??....I think it was defaulting to fill up my swap partition.....which is *completely* not what I want...

---

### Post by kpkeerthi on 2007-12-19
> **B34ST1Y said:**
> better yet....an installation that restores my computer to the state its in *right now*   ? ?
Partimage does that.

---

### Post by Frank Golden on 2007-12-19
Nevermind

---

### Post by B34ST1Y on 2007-12-19
can I get a walkthrough of commands to do that? I'm running the rescueCD, and I just type in:

Partimage



and the gui comes up and I name my ISO, tell it to back up my system and away it goes....but it will only back it up to my swap partition (the only other partition besides my partition im backing up)

---

### Post by kpkeerthi on 2007-12-19
Check out Aysiu's website in my signature

---

### Post by cub682 on 2007-12-19
[http://www.remastersys.klikit.org/](http://www.remastersys.klikit.org/)

---

### Post by Frank Golden on 2007-12-19
Please read the how-to's I referenced in my earlier post. If you have an external HDD you can copy to it or maybe to an external DVD burner. It will be very slow.


BTW looking at the website referenced by cub682 above seems to be what you *want*. It doesn't unmount your volume and you can burn to a DVD.

You have many options, good luck.

---

### Post by B34ST1Y on 2007-12-19
Ok, I tried out Remastersys, and it finished whatever it was that it was doing.....I used remastersys backup....so when it finished it created a folder in my /home/ directory called remastersys and it's 4.5gB big......the problem is...do I just burn that folder to a dvd ?    I do see a .iso file in the folder, but it's nowhere near 4.5gB

---

### Post by crjackson on 2007-12-19
> **B34ST1Y said:**
> Ok, I tried out Remastersys, and it finished whatever it was that it was doing.....I used remastersys backup....so when it finished it created a folder in my /home/ directory called remastersys and it's 4.5gB big......the problem is...do I just burn that folder to a dvd ?    I do see a .iso file in the folder, but it's nowhere near 4.5gB

I don't use this particular program, but I do the exact same thing using Acronis TrueImage (It's costly though).  My guess would be that you copied or backed-up 4.5GB of data and it's compressed onto a much smaller ISO that you can burn.

You should be able to boot a rescue CD/DVD and then replace it with the CD/DVD that have the backup image and restore.  It may even be placing the restore program on the ISO with the backup image so it's all on one piece of media.  You'll just have to test it a see.

---

### Post by cub682 on 2007-12-20
> **B34ST1Y said:**
> Ok, I tried out Remastersys, and it finished whatever it was that it was doing.....I used remastersys backup....so when it finished it created a folder in my /home/ directory called remastersys and it's 4.5gB big......the problem is...do I just burn that folder to a dvd ?    I do see a .iso file in the folder, but it's nowhere near 4.5gB

Just right click on the .iso file and select "write to disk".
It will probably be larger than 700MB..... so you will have to burn to dvd.
After you're done and have a good burn.... run - sudo remastersys clean.....this will cleanup that large folder.

---

