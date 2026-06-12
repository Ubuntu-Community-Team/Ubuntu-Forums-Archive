---
title: "Few questions regarding installation of ubuntu on dell inspiron 6400"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by death__machine on 2007-09-12
Hi guys,
I am about to use Ubuntu or any version of linux for the first time, so i need help regarding stuff..
I have downloaded this iso file-ubuntu-7.04-desktop-amd64.iso, for my Dell Inspiron 6400 with the following config:
2.0 Ghz Core 2 duo(since core 2 duo's are 64 bit i downloaded 64 bit from the ubuntu website, and the file reads amd64 though)
2.0 Gb ram DDR2
ATI X1400 128 MB Dedicated
120 Gb HDD 
Xp home came installed and I reinstalled XP home on the same partition after formatting it.
I guess an intel wireless card(i dont use it and the drivers werent even reinstalled i guess after the reinstallation of xp, thus it is listed as unidentified hardware in device manager i guess)

There are total of three partitions right now:
Partition 1: Close to 100 Gb having Xp installed on it(50 gb free)
Partition 2: Dell utilities n stuff close to 150 mb i guess
Partition 3: Mediadirect(i dont use it, the only thing that i like abt mediadirect are the front keys which can be used for controlling volume)
Partition 4: I deleted this partition, it included the default factory settings flash, which is of no use after reinstalling xp as i dont get the dell.com screen to press ctrl+f11.

I hope i downloaded the correct Iso image for my system.
I have a few questions though:
1)I really dont know how to partition the 100 Gb thru windows. I plan to keep this windows installation and boot into both ubuntu or xp whichever i wish.
I understand i need three partitions for linux, one for booting, one for swap, and one more(i dont remember the purpose for this one).
I need help regarding this partitioning.
2)I use a usb modem which my Internet provider has given me. Its an Alcatel Lucent Cellpipe2 USB 20A. I have only xp drivers for it, this is what i found upon mass searching [http://eciadsl.flashtux.org/download.php](http://eciadsl.flashtux.org/download.php) , over here i checked and my modem is supported, i just need to know if the correct ubuntu drivers are present here. After installation of ubuntu how do i install these drivers if they're good enough.

3)Is there a way to use a part of my drive with both windows and ubuntu eg. i want to make my documents common between both of them...

4)I have heard some trouble installing ubuntu cuz of X1400 drivers. I googled and i found this link [http://www.ubuntugeek.com/howto-install-feisty-beryl-on-dell-inspiron-6400-ati-x1400-dell-1390-wifi.html](http://www.ubuntugeek.com/howto-install-feisty-beryl-on-dell-inspiron-6400-ati-x1400-dell-1390-wifi.html) 
> After booting into the CD X won’t start. Hit Enter to say OK to the error messages and get back to the black screen. You may need to switch to ALT-F4. Do the following, one at a time, to get X working:

wget [http://www.mylittleubuntuguide.com/files/ati](http://www.mylittleubuntuguide.com/files/ati)

sudo chmod +x ati

./ati

I dont understand this part, ubuntu isnt installed + over here they mention to get the drivers as i understand from the commands written, and how does that happen when ubuntu isnt installed and internet is also not working.



I guess and hope i have given all necessary details.  I would also like to know any errors which i may encounter and how to solve them. :)
Thanks guys.

DeAtH MaChInE

---

### Post by benerivo on 2007-09-12
> 1)I really dont know how to partition the 100 Gb thru windows. I plan to keep this windows installation and boot into both ubuntu or xp whichever i wish.
 I understand i need three partitions for linux, one for booting, one for swap, and one more(i dont remember the purpose for this one).
 I need help regarding this partitioning.I would just defrag this volume in windows and then resize from the ubuntu live cd, using the gparted program. You only need two partitions for linux. One is linux OS, the other is for the swap.

> 2)I use a usb modem which my Internet provider has given me. Its an Alcatel Lucent Cellpipe2 USB 20A. I have only xp drivers for it, this is what i found upon mass searching [http://eciadsl.flashtux.org/download.php](http://eciadsl.flashtux.org/download.php) , over here i checked and my modem is supported, i just need to know if the correct ubuntu drivers are present here. After installation of ubuntu how do i install these drivers if they're good enough.I don't know about this one, but adsl usb modems will require some work. I had one about a year ago and never got it to work, but it should be possible.

> 3)Is there a way to use a part of my drive with both windows and ubuntu eg. i want to make my documents common between both of them...Yes. You are best off making a partition (from the live cd) that is just full of your own files and not part of any OS - and using the ntfs format.

> 4)I have heard some trouble installing ubuntu cuz of X1400 drivers. I googled and i found this link [http://www.ubuntugeek.com/howto-inst...1390-wifi.html I dont understand this part, ubuntu isnt installed + over here they mention to get the drivers as i understand from the commands written, and how does that happen when ubuntu isnt installed and internet is also not working.](http://www.ubuntugeek.com/howto-inst...1390-wifi.html I dont understand this part, ubuntu isnt installed + over here they mention to get the drivers as i understand from the commands written, and how does that happen when ubuntu isnt installed and internet is also not working.) I think these instructions mean that you have a physical internet connection, but the desktop won't start, so you have to install the ati drivers from the 'command line', and then start the desktop.

---

### Post by p_quarles on 2007-09-12
First, partitioning: So you "deleted" the fourth partition. Is is just free space now, or did you add it to another partition?

This is important, because you can only have four primary partitions on your hard drive, and Linux will need to use two of them: one for the main part of the OS, and the other as an "extended" partition which allows it to make a series of smaller secondary/virtual partitions (things like the bootloader, swap, and so on). 

So, beyond just defragging all the Windows partitions, you might need to be ready to format another one of them to make room for Linux. The installation disk can do this for you, as well as resizing the main Windows partition. 

As for the USB modem, you should check it out on the live CD before doing anything else. If you can get it to connect to the internet using the live disk, you won't have any problems once Ubuntu is installed. If not, it might take some work to get it running; just be forwarned/prepared.

---

### Post by death__machine on 2007-09-13
> **benerivo said:**
> 

I think these instructions mean that you have a physical internet connection, but the desktop won't start, so you have to install the ati drivers from the 'command line', and then start the desktop.
How do i do this? :S

---

### Post by death__machine on 2007-09-13
> **p_quarles said:**
> First, partitioning: So you "deleted" the fourth partition. Is is just free space now, or did you add it to another partition?

This is important, because you can only have four primary partitions on your hard drive, and Linux will need to use two of them: one for the main part of the OS, and the other as an "extended" partition which allows it to make a series of smaller secondary/virtual partitions (things like the bootloader, swap, and so on). 

So, beyond just defragging all the Windows partitions, you might need to be ready to format another one of them to make room for Linux. The installation disk can do this for you, as well as resizing the main Windows partition. 

As for the USB modem, you should check it out on the live CD before doing anything else. If you can get it to connect to the internet using the live disk, you won't have any problems once Ubuntu is installed. If not, it might take some work to get it running; just be forwarned/prepared.
I think the partition that i deleted was automatically added as free space in this windows partition, but i'm not sure.

Hmmm so i can have only 4 main partitions, one for windows, two for ubuntu and one for documents(i can put songs n stuff here). So if u want i could delete the other two partitions, i dont use media direct anyway and the 3rd partition has some dell tools, which i wont use either. 

Ok I will delete these partitions, i have one question though. The partition that i want for storing songs n stuff, where do i create that from, and how do i move my songs frm windows into that. Will this partition appear in windows? So i can move the songs from windows directly...

And the iso file i downloaded is correct right?

Thanks guys(am off to school now, will reply later)
Bye


DeAtH MaChInE

---

### Post by death__machine on 2007-09-13
@p_quarles
Hi, I found out that the partition i deleted is listed as Unallocated space. I got 3gb of it and if i delete mediadirect then 5 gb. I have one more question though, will these media direct keys work without the partition? I just like to use them for volume..

---

### Post by benerivo on 2007-09-13
> How do i do this? :S

It looks as if you will only need to do this if the live cd fails to load properly. If so, then follow the instructions from your link. Unfortunately you have a adsl usb modem, and the solution described requires internet access - you will have no net connection straight away with your modem. This may be a pretty big problem, but i wouldn't get in to it right now - the live cd may load up fine.

---

### Post by benerivo on 2007-09-13
> And the iso file i downloaded is correct right?

I don't think it is. You have an Intel processor, but [this page]("http://releases.ubuntu.com/7.04/") implies it is only for AMD processors.

---

### Post by death__machine on 2007-09-13
The Ubuntu launch from the cd was a failure.
I verfied the contents and they were ok, i launched ubuntu with safe graphics mode and without it but the result was same a loading bar for some time followed by a blank screen.

I guess its cuz the image is not for 64 bit intel processors.
Should i download the other image which isnt 64 bit?

---

### Post by death__machine on 2007-09-13
I was thinking if this blank screen that i encountered was not due to 64 bit image, but due to my graphics, then i really dont think I will ever be able to install ubuntu :(

---

### Post by benerivo on 2007-09-13
It's definitely possible. Have you seen [this thread]("http://ubuntuforums.org/showthread.php?t=399913")?

However, it does assume you have a working internet connection to download the neccasary packages, so I would think you would need to get an adsl router to replace your usb modem. Someone in the above thread mentioned that the wi-fi on the Dell 6400 work out of the box, so you might have an internet connection if you take it to a wi-fi spot.

---

### Post by death__machine on 2007-09-13
I dont have wifi installed in windows, but if it works out of the box meaning that it will function in windows only in drivers, but without windows it doesnt need drivers... Am I right?

I can get to the local wifi spot on Saturday after 34 hrs.

i will try this over there.
I also downloaded the non 64 bit version just to see if my luck is good :P.
Will post here as soon as possible.
Thanks guys.

---

### Post by death__machine on 2007-09-14
> **benerivo said:**
> It's definitely possible. Have you seen [this thread]("http://ubuntuforums.org/showthread.php?t=399913")?

However, it does assume you have a working internet connection to download the neccasary packages, so I would think you would need to get an adsl router to replace your usb modem. Someone in the above thread mentioned that the wi-fi on the Dell 6400 work out of the box, so you might have an internet connection if you take it to a wi-fi spot.

I think the guy meant that the wifi worked instantly after the installation of ubuntu.

---

### Post by death__machine on 2007-09-15
I tried to type the codes in the wifi section as mentioned in [http://ubuntuforums.org/showthread.php?t=399913](http://ubuntuforums.org/showthread.php?t=399913) by pressing alt+f4 but nothing appeared.

---

