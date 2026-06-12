---
title: "How on earth do people install Ubuntu?"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by gerry1936 on 2007-08-21
Been trying to install ubuntu/xubuntu/...  for weeks.
Intel Celeron 600 Mhz 256M RAM 26G disc.

Friend recommended I try Xubuntu rather than Ubuntu. Downloaded ISO, and tried to install it. Whatever it did, and then whatever I did, it complained that the partitioning was wrong, then when I got that right using g-parted, that there were errors in the file structure. Then I tried the alternative CD, with similar results. So i put Xubuntu  on the back burner, and installed a number of other distros, most of had features which I disliked, some were miles too slow.
Then I came across "Installation/Low Memory Systems" on the Community Documemtation. I tried this, but when I got to the
sudo nano /etc/apt/sources.list
stage, the file was empty. So I could not edit it as suggested. I carried on, but it insisted on looking on the CD for the lightweight apps that I wanted to use- but they are not there are they?
Then I found on psychocats site his method for barebones install, using the mini.iso. Seemed to be working until I did step
sudo apt-get update

it then crashed at 99percent, the bottom line on the screen being 
99% [3 Translation-en_GB bzip2 0]

So I'm having to kick Ubuntu into touch. There must be some way that I can install it- but how?

---

### Post by tgm4883 on 2007-08-21
Did you check the md5sums of the iso's you downloaded?  Did you burn at a slow speed?  Did you check the cd after you burned?

Even though the sources.list was empty, we can also tell you what goes in there.

---

### Post by nvteighen on 2007-08-21
At what speed did you burn the ISOs? Maybe you burned them too fast, that can make install fail.

---

### Post by wpshooter on 2007-08-21
If it were me I believe I would try to download, burn and install Feisty/Gnome.  I believe that you are at a bare minimum on memory and it may be a bit slow but I believe that might be your best bet.  Try downloading the ALTERNATE version of Feisty.

Also, let me ask you if you have any other information (O/S or programs or data) on this computer that you need to keep.  If not let me suggest that before you attempt to install Ubuntu that you WIPE the hard drive clean with [www.killdisk.exe](www.killdisk.exe) 

Make sure that when you boot up to the Ubuntu installation CD, that the very first thing that you do is to run the CD integrity check function that is found on the initial Ubuntu boot screen menu.

Let us know how it goes.

Thanks.

P.S. - Make sure that when you partition your drive that you make a separate **/home **partition.

---

### Post by dptxp on 2007-08-21
Make a SWAP partition of 1 GB first with GParted Live CD (download Gparted and make one).
You will be able to run and install from Live CD, that is if your iso is OK and you burned it using
'burn image' command. The SWAP partition shall be needed anyway, make it at end of disk if possible.

You can use InfraRecorder in Windows (free program). Go to Actions>Burn Image.

Use torrents to download. Point it to existing download, any files with errors will get corrected and you need not download every byte again.

Yes, you can install regular Ubuntu (Gnome).

---

### Post by ddrichardson on 2007-08-21
> **dptxp said:**
> Yes, you can install regular Ubuntu (Gnome).

Just to expand, with 256 Mb you will need the alternate install CD for Ubuntu.

---

### Post by dptxp on 2007-08-21
> **ddrichardson said:**
> Just to expand, with 256 Mb you will need the alternate install CD for Ubuntu.

With SWAP, the Live CD can be used. It worked for me.

---

### Post by ddrichardson on 2007-08-21
> **dptxp said:**
> With SWAP, the Live CD can be used. It worked for me.

True but the reality is that it's going to run like treacle in the artic with this chaps specs.

---

### Post by philinux on 2007-08-21
Ubuntu installed fine on my machine with the specs below. It runs pretty fast enough for me.

---

### Post by gerry1936 on 2007-08-23
Solved.

First I burned a new CD at the lowest speed my drive will do- 8x.

This got further than the previous one- the installer complained about what I understood to be debris in the spare disk space that I intended it to install Xubuntu in.

So I downloaded KILLDISK (free)  and ran it- when I tried to install again, everything worked and it is up and running.

---

### Post by leedsdevil on 2007-08-23
Gratz Gerry glad to hear that i was going to reply last night but went to bed instead . i had install Ubuntu Full version 6.6? on a opalex dell with 194 megs of ram 13.5 gig HD worked well easy and also with Ubuntu studio 7. version still no probs    Leeds

---

### Post by gundumfx on 2007-08-23
i see you were trying but you did not do this you did not read the instractions well first you are pose to download ubuntu an after it is done the download was the iso image of ubuntu so you take a blank cd an then all the file that gave you in the ubuntu download witch is the iso so you have to burn the iso image the put the cd in an then restrat an an you will go to the ubuntu or xubuntu edubuntu or kubuntu ok

---

### Post by tgm4883 on 2007-08-23
> **gundumfx said:**
> i see you were trying but you did not do this you did not read the instractions well first you are pose to download ubuntu an after it is done the download was the iso image of ubuntu so you take a blank cd an then all the file that gave you in the ubuntu download witch is the iso so you have to burn the iso image the put the cd in an then restrat an an you will go to the ubuntu or xubuntu edubuntu or kubuntu ok

What?

Try using some punctuation.

---

### Post by ddrichardson on 2007-08-23
> **tgm4883 said:**
> What?

Try using some punctuation.

Spits coffee on screen. Fantastic. :-)

---

