---
title: "after playing with a live cd...."
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by maddbaron on 2006-06-05
I am more than willing to jump into the linux frey cold....using kubuntu, after getting it to work on another machine that runs win xp.

it had a lot of programs preinstalled that i liked.

but i have questions.

how do u view windows media videos, real media and flash media?

i saw the mp3 player program so i see it can play mp3's.

also my laptop has two hard drives. one for media(music,movies, jpg's) and one for all my windows stuff.

now if i install will my media hard drive be erased or damaged? it has a lot of info and will take me hours to back up.

also does kubuntu have the apt-get program? i googled and found a lot fo programs i'd want like an alternative novel writing program and i know celtx for script writing, then i saw the linux version of aim, yahoo messenger and AMSN but i know kubuntu comes with gaim(speaking of which does gaim allow for file transfers and webcam between the windows native users who r likely using aim and yahoo?). so i know those are covered. but how do i get them? is it a simple process?

also how do convert video formats? in windows theres winavi which lets me convert avi's to wmv or rm. does linux have anything like that?

also there are sites like you send it for file transfer how does someone use that linux since those files r often winzip or winrar or .7zip files?

and is there built in driver support for ac97 sound controls and broadcom internal wifi(mines is a broadcom 802.11g network adapter and a SiS 900-based pci)?


i really want off of windows it drives me nuts with the freezing it does n lack of security even tho i have lots of security.

sorry for all the questions just want 2 b sure since my laptop is my main machine. and i can't dual boot since i'm the type to use the entire harddrive

thanks in advance!

---

### Post by bruenig on 2006-06-05
> how do u view windows media videos, real media and flash media?
The easiest way to do this is with Automatix, just follow the instructions here. [http://www.ubuntuforums.org/showthread.php?t=177646](http://www.ubuntuforums.org/showthread.php?t=177646) 

> also my laptop has two hard drives. one for media(music,movies, jpg's) and one for all my windows stuff.

now if i install will my media hard drive be erased or damaged? it has a lot of info and will take me hours to back up.

Need more information for this. Are you going to dual boot ubuntu and windows and if so are you going to install linux on the media hard drive or are you going to install it on the windows hard drive. Please list your partitioning scheme if you know it.

> also does kubuntu have the apt-get program? i googled and found a lot fo programs i'd want like an alternative novel writing program and i know celtx for script writing, then i saw the linux version of aim, yahoo messenger and AMSN but i know kubuntu comes with gaim(speaking of which does gaim allow for file transfers and webcam between the windows native users who r likely using aim and yahoo?). so i know those are covered. but how do i get them? is it a simple process?

Kubuntu does have apt-get. Gaim does have file transfer that works with other people using yahoo and aim. I am not sure about Gaim and webcam, don't use one. However, with Automatix, You can install AMSN which is an MSN client which allows you to use Webcam.

> also there are sites like you send it for file transfer how does someone use that linux since those files r often winzip or winrar or .7zip files?

I am a bit unclear as to what you are asking here. If you are wondering about .rar .zip and .ace support, that can be acheived in linux and specifically using Automatix.

Again: Automatix cures a lot of headaches. [http://www.ubuntuforums.org/showthread.php?t=177646](http://www.ubuntuforums.org/showthread.php?t=177646)

Anything else, feel free to post.

---

### Post by unicycler on 2006-06-05
[QUOTE=maddbaron]I am more than willing to jump into the linux frey cold....using kubuntu, after getting it to work on another machine that runs win xp.

it had a lot of programs preinstalled that i liked.

but i have questions.

how do u view windows media videos, real media and flash media?

i saw the mp3 player program so i see it can play mp3's.

also my laptop has two hard drives. one for media(music,movies, jpg's) and one for all my windows stuff.

now if i install will my media hard drive be erased or damaged? it has a lot of info and will take me hours to back up.

also does kubuntu have the apt-get program? i googled and found a lot fo programs i'd want like an alternative novel writing program and i know celtx for script writing, then i saw the linux version of aim, yahoo messenger and AMSN but i know kubuntu comes with gaim(speaking of which does gaim allow for file transfers and webcam between the windows native users who r likely using aim and yahoo?). so i know those are covered. but how do i get them? is it a simple process?

also how do convert video formats? in windows theres winavi which lets me convert avi's to wmv or rm. does linux have anything like that?

also there are sites like you send it for file transfer how does someone use that linux since those files r often winzip or winrar or .7zip files?

and is there built in driver support for ac97 sound controls and broadcom internal wifi(mines is a broadcom 802.11g network adapter and a SiS 900-based pci)?


i really want off of windows it drives me nuts with the freezing it does n lack of security even tho i have lots of security.

sorry for all the questions just want 2 b sure since my laptop is my main machine. and i can't dual boot since i'm the type to use the entire harddrive

thanks in advance![/QUOTE]

You can get Real Media Player for Linux. And for WMV, i like to use Xine media player, but you have to apt-get install xine-ui since components are used in other programs. Full xine works great (ui = user interface). And flash is not problem for firefox. Just install the flash plug in and Adobe will give you good instructions on that.

Are they two hard drives or two partitions? Ubuntu will let you choose which drive you want to format for installation and Ubuntu can READ ONLY NTFS but will be able to read/write FAT32.

apt-get is a command line installation tool that will check and install for dependencies. Gaim does not have video support and I don't think it will have audio either. You may not even be able to use video/audio for AIM, YIM, MSNM for linux.

Don't know the video converters, but there are some out there.

Linux can open .zip and other compressed file types.

Did your Sound/Wireless work with the Ubuntu live disk?

---

### Post by maddbaron on 2006-06-05
it is two hard drives a c drive and a d drive. with my cd drive as e i think.

thats the problem i cant seem to get the live cd to run on my laptop. the cd is read a picture file when installed....so i cant test the sound :(

and what do u mean it can read fat32? i think both hard drives r fat 32 but only one is full of my media.

but i have been googling and going thru kubuntu and i am confortable with it and i can find the programs i need. but what i really need to know is does ubuntu support wifi for broadcom 802.11g internal? if it does i am set to go.

---

### Post by macdo on 2006-06-05
To create and open rar files, you'll need to install unrar: ```
sudo apt-get install unrar
```
For all your multimedia needs (mp3, wmv, dvd, etc.) visit the wiki page [here]("https://wiki.ubuntu.com/RestrictedFormats") 
By default, kubuntu doesn't install gaim, which is part of Gnome (or at least Gnome-based). Instead it uses Kopete, which is less compatible with a lot of networks, IIRC. Gaim can be used to send files.
It's probably quite hard to convert avi to wmv under ubuntu as they are both MS formats. There is a tool to convert avi to mpeg, if that's useful: try [here]("http://flavor8.com/index.php/2006/02/19/how-to-convert-avi-to-mpg-on-the-linux-cli-2/")
Because (k)ubuntu is a Debian-based system, it works using apt. You should use Ubuntu files normally, though many people have used debian files with no problems.

---

### Post by maddbaron on 2006-06-05
ok i got ubuntu live cd to work on my laptop but i cant connect to the net and i dont know how to get it to recognize my wifi connection. it runs quick! I like Kubuntu more though. 

I'm using Xubuntu now on my second pc as a live cd and its pretty good. but i have a direct line to my dsl line so thats how i am online.

as for my hard drive i think its one big drive partitioned when i was in ubuntu it said it was a 55.6gb drive with 3 partitions. 

the 1st was like 3 or 4 gigs the second was 23.something gigs and the 3rd was the same. the 3rd part was inaccessable :( i clicked enable and it did nothing.

so here are my new questions how do i get it to recognize my wifi adapter and how do i get it to allow me to access my 3 partition once i install on main drive(and how can i tell the difference? by default when i reinstalled windows it installed on the 1st partition will kubuntu do the same?)?

once i know these answer i can make the leap lol(after backing up some files on cd lol)....

---

### Post by maddbaron on 2006-06-05
ok i am using the kubuntu live cd on my laptop still on xubuntu on my desktop. i accessed my file system but it konqueror said " cannot mount hard drives" it recognized the drives by name "acer" and acerdata" but can't mount them. how can i get them mounted and where do i go set up my wifi connection?

---

### Post by ????? on 2006-06-05
and Flash Player works in linux so that's the easy part.

---

### Post by bruenig on 2006-06-06
You can't mount the hard drives in the live cd but you will be able to mount them once you install. During the install make sure you go into manually edit the partition table and that will allow you to resize and format drives and partitions and also will let you determine which drives and partitions will mount on start up. I need to know again whether or not you are ditching windows altogether or trying to dual boot.

The wireless card might not be supported. There is a program called ndiswrapper i believe that helps see if you have the appropriate driver. I installed it with Automatix and the interface looked pretty simple to use.

You can install it seperately with 
```
sudo apt-get install ndisgtk
```
I'm not sure if that can be done in the live cd, I didn't really mess around with it. (went straight for the install)

Might want to take a look at this, don't know how helpful it is [http://lxer.com/module/newswire/view/46385/](http://lxer.com/module/newswire/view/46385/)

---

### Post by H.E. Pennypacker on 2006-06-06
> also there are sites like you send it for file transfer how does someone use that linux since those files r often winzip or winrar or .7zip files?

Yes, you can still use those websites, since Linux distros provide support for the file-types you've listed (zip, .rar, etc. - any compression file-type).  Just do what you've been doing on Windows already.  Go to your favorite upload website, and select the file you want to upload.  

When it comes to file-types, however, you can no longer use Windows-specific file-types, such as .exe (executable).  You also won't be able to use .sys and all that, but none of these are necessary.  What's most important is that your media file-types (.ram, .mp3, etc.), compression file-types (.rar, .zip, etc.), and others can be used with Ubuntu (and other Linux distros).

The basic rule is that just about anything Windows owns can't be used in Linux.

---

### Post by nalmeth on 2006-06-06
The reason you can't mount them is likely because you don't have the proper permissions. Use sudo in the terminal before the command to attain the needed priviledges.

Any question's not covered by other posters?

---

### Post by maddbaron on 2006-06-06
what is the sudo command to gain control please?

and i want to keep the second partition(my media files) the same and unformatted so I can access them. Is that possible?

My main partition means little to me and I can burn back ups of files so that is cool with me if its reformatted.

I cant find my wireless card. I have Kubuntu on my laptop as I said via live cd but can't find the wireless.

these 2 things r holding me back. I want off of windows but not at cost of media and net connection...

I am ditching windows since I am the type to stay with one thing. Windows gives me too many headaches.

Kubuntu is like a breath of fresh air to me...

I just dont want to lose my media files and have a net connection

---

