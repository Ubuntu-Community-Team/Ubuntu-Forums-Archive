---
title: "Installing Nvidia legacy driver on 6.10 server"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by KunoNoOni on 2007-03-28
Well I'm a first time Ubuntu user but I have had a linux box for a couple of years. I used to run slackware 10.2, but I was having problems with MySQL and PHP, so I decided to wipe the box and install Ubuntu Server. I found the install pretty easy but along the way I made some errors and had to wipe and reinstall. no problem, second time through was even easier. I got linux installed, setup my static ip, installed webmin. the next day I got xorg, fluxbox, azureus and firefox installed. Life was good :) but I noticed that the webpages were kinda of sluggish. I check the xorg.conf file to find out that the video driver was vesa... I have a nvidia geforce2 gts video card. I also noticed that my monitor settings didn't loog right either. I found the settings for the monitor and entered them in. I also did some reading for installing a driver for the nividia video cards. I tried *apt-get install nvidia-glx-legacy* ubuntu came back with *Package nvidia-glx-legacy is not available, but is referred to by another package...* ok, thats odd... I made sure that all the repositories were uncommented in the source.list file. I did an *apt-get update* before trying to get the package too... I did some more reading and found a program called *envy*. I installed the program, ran *apt-get -f install*, then ran the program. installed the driver but xorg would load as it said that module nvidia didn't exist. the only thing I can think of is when I type *uname -r* I get *2.6.17-10.server*. So I believe that what might have caused the envy program to not install the driver. Let me backtrack a little, I've *never* had to install a video driver in linux before. I'm really new to this and I feel kinda lost. I would appreciate some advice on installing a video driver for a nvidia geforce 2 gts on ubuntu 6.10 server :)

Sorry for being so long winded....:/

---

### Post by Bachstelze on 2007-03-28
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by KunoNoOni on 2007-03-28
Thank you for the link, but I must confess that after I typed my post I saw this thread: [READ THIS FIRST prior to posting - IMPORTANT links]("http://ubuntuforums.org/showthread.php?t=232059") and then this link: [http://users.bigpond.net.au/hermanzone/p7.html]("http://users.bigpond.net.au/hermanzone/p7.html")

so I ran dpkg-reconfigure xserver-org, followed the instructions and xserver falied to start :) I ran it again, changed a couple of options and xserver came up!! Now firefox runs more smoothly :)

I may still try to install an updated driver though... just for the learning experience :)

---

