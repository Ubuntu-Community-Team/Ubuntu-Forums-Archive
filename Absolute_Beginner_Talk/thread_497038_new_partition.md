---
title: "new partition"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by mixmastermike on 2007-07-09
Hello everyone,

I am currently trying to install ubuntu on my windows pc.  I was following a screencast i found that walked through the installation process.  I put in the cd and clicked the install icon on the desktop.  When it asked how to partition the drive the video said to use the top option and set it for around 10GB.  When i tried the slider would only go as low as 140GB... 

Its a 250GB Seagate drive with about 140GB used on it.

So i went to the system - administration - GNOME partition editor and tried to do it myself.  I set to change the free space on the drive from somewhere around 8MB to 10GB.

Its working on it right now and what i want to know is will this just free up that space or will it delete all of the data on the drive?  (all the windows stuff?)

Thanks alot

---

### Post by KIAaze on 2007-07-09
[B]Whatever you do in Gparted, do not delete or format the NTFS partition.
Doing so would delete all the data on your Windows partition.
[/B]

Resizing it however is possible if it is not too fragmented.

Have you defragmented your Windows partition before starting the installation process?

Now I don't fully understand what you said:
What do you want to set to 10GB? Your Windows partition or your future Ubuntu partition?

When you get to this [resizing screen]("http://img379.imageshack.us/my.php?image=feistydual06rw5.png"), you are actually resizing your Windows partition.
So if you reduce it to 10GB, you're reducing your Windows partition to 10GB.

Since the Ubuntu installation process tries not to destroy your Windows data and you have 140GB used, it's normal that it won't let you reduce it below 140GB.
But with a 250GB HD, that still leaves you 109GB for Ubuntu. :)
(approximately 1GB will be used by the swap space, which is an equivalent of the Windows virtual memory)

You should read these guides too:
[http://www.psychocats.net/ubuntu/partitioning]("http://www.psychocats.net/ubuntu/partitioning")
[https://help.ubuntu.com/community/GraphicalInstall]("https://help.ubuntu.com/community/GraphicalInstall")
[http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

---

### Post by Happy_Man on 2007-07-09
No, what the screencast meant was to set it for 10GB of *free space*, not so that the slider showed 10GB. So, naturally, the partition editor, seeing that 140GB of space was used, wisely wouldn't let you go below that. 

Now, for your second phase (the one it's working on), did you already create another partition, or what? That's what I'm confused on. Could you elaborate? Maybe post a screenshot of what the partition editor shows? Thanks!

---

### Post by mixmastermike on 2007-07-09
Yea i didn't realize that it was stating the size of the windows partition not what the linux one would become...

So i tried to do it myself and do it in the Gnome partition editor.
Its working on resizing the drive now and the keyboard wont work and i cant cancel it cause it says it will cause damage to the drive.  So i cant get a screenshot but ill describe it...

Resize /dev/sda1 from 232.88 GiB to 223.35 Gib

ntfsresize -P -i -f -v /dev/sda1

then under that it says the next task is

Create Primary Partition #1 (ext3, 9.53 GiB) on /dev/sda

Its been doing that second task for a good 3 hours now and i was kinda worried.

I have all my important stuff backed up but i still kinda feel like went ahead and did somethin that might mess it up...

I havent defraged it yet cause its only about a month old...

So all i really want is a space about 10 GB for linux and the rest for Windows...

---

