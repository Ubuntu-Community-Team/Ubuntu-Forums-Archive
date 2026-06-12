---
title: "Quickguide: Installing/upgrading advice to Gutsy"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Perfect Storm on 2007-10-20
[b][color=red]So you want to install/upgrade to the latest version of Ubuntu?

Here's some good advice before proceeding;[/color][/b]



**1) Wait a month before installing the latest version of X,Y,Z distro after its release.**
[size=1]That would give the devs some time to iron out some critical bugs that might appear after the release.[/size]

**2) Always backup you stuff.**
[size=1]No matter what, backup, backup, backup. Accidents can happen, better to be safe than sorry.[/size]

**3) Go for Clean install instead of upgrade.**
[size=1]No matter which OS or distro, an upgrade may be a hazardous process, especially if you have non-official libs/apps installed or if you have heavy modified your OS.
If you kept to the official sources there should be no problem upgrading.[/size]

**4) Download the torrent .iso of Gutsy.**
[size=1]The .iso file will less likely be corrupted than FTP/HTTP download. 
Also it will spare the Ubuntu servers a great deal.[/size]
[[size=1]Read more...[/size]](https://help.ubuntu.com/community/BitTorrent) - [[size=1]Download Torrent[/size]](http://releases.ubuntu.com/7.10/)

**5) Make sure the CD/DVD-drive is clean, also check the CD/DVD for damaging and dirt.**
[size=1]yes, this seems so obvious, but I helped a lot of people where these simple step did the difference.
Note: the quality of the CD/DVD also have an impact on success rate.[/size]

**6) Check the checksum of the downloaded .iso.**
[size=1]To avoid failure and corrupt Ubuntu CD. 
[[size=1]Read more...[/size]](https://help.ubuntu.com/community/HowToMD5SUM)[/size]

**7) Burn the CD/DVD image at 4x speed and verify it afterwards.**
[size=1]By burning it at low speed you'll avoid error on the Ubuntu CD, 
Verifying it to make sure it's identically with the downloaded .iso.
Use CD/DVD-r, not -rw as it may give installation errors.[/size]
[[size=1]Read more...[/size]](https://help.ubuntu.com/community/BurningIsoHowto)

**8 ) When inserting the Linux CD go to the verify/check CD option, and let it check itself.**
[size=1]Yes even it pass the other tests it still can happen there's error on the burned CD/DVD.[/size]

**9) Have seperated partitions.**
[size=1]A good idea is to have / (root), /home and /boot[/size]
[[size=1]Read more...[/size]](https://help.ubuntu.com/community/HowtoPartition)



=========================
**[color=red]Troubleshooting[/color]**

**a) If it continously fail regarding borked CD, mismath checksum, download the .iso from another mirror.**
[size=1]I have been there where one of the mirrors had a bad .iso.[/size]

**b) If check and verify is okay and it still fail to install/load go for the alternate CD instead - which have text installer.**
[size=1]It's much more stabil and not difficult if you read and follow the text installer guide.
Computers with low memory should also use the alternate CD, see release notes.[/size]

**c) Check your memory for bad sections**
[size=1]Yes, your hardware may have failure - insert the Ubuntu CD and run the memory check.[/size]

**d) ATI cards - Nothing new here, always been a struggle regardless which Linux distro.**
[size=1]This will change soon (hopefully) as the driver goes Open Source.[/size]

**e) Intel cards - clumbsyness and/or slow Desktop respond.**
[size=1]install : libgl1-mesa-dri[/size]

**f) Slow bootup?**
[size=1]This might be the problem + solution - [[size=1]this thread[/size]](http://ubuntuforums.org/showthread.php?t=580903).[/size]

[[color=red]**Release notes - Known bugs & workaround**[/color]](http://www.ubuntu.com/getubuntu/releasenotes/710) <= Click me.

> NOTE: This is advice thread, if you have problem please make a new thread or use our excellent search engine. 

---

### Post by ginestre on 2007-10-20
I'd also like to ask for clarification of something that I'm unsure of: what is likely, possible or certain to happen to a) installed applications and b) data files when I upgrade via a  clean install?

---

### Post by Dr Small on 2007-10-20
Excellent information. We have been needing something like this.
But I will add a few key points to it:

[quote=Artificial Intelligence]4) Download the torrent .iso og Gutsy.
The .iso file will less likely be corrupted than FTP/HTTP download.
Also it will spare the Ubuntu servers a great deal.[/quote]
The Gutsy torrents can be downloaded from here:
[http://releases.ubuntu.com/7.10/](http://releases.ubuntu.com/7.10/)

[quote=Artificial Intelligence]6) Check the checksum of the downloaded .iso.
To avoid failure and corrupt Ubuntu CD.[/quote]
The MD5 Checksums can be found here:
[http://releases.ubuntu.com/7.10/MD5SUMS](http://releases.ubuntu.com/7.10/MD5SUMS)

And to check a checksum, you run:
```
md5sum *ubuntu-7.10-desktop-i386.iso*
```
and it should be the same checksum as the one listed on the website.


Dr Small

---

### Post by Perfect Storm on 2007-10-20
No problem, that's why I kept this sticky open, so people can contribute to it.

---

### Post by overlord.gaurav on 2007-10-20
Hope this reduces a few up-coming threads. :)

---

### Post by Taters on 2007-10-20
Help... I probably should've waited a couple of weeks to install Gutsy, but I did it this morning. Now, when I boot up, I get a kernel panic message. Can I downgrade to Feisty for a bit? If I can, how?

Please help.

---

### Post by Perfect Storm on 2007-10-20
Please, post in a new thread. This is an advice thread. Thanks.

---

### Post by intense.ego on 2007-10-20
> **ginestre said:**
> I'd also like to ask for clarification of something that I'm unsure of: what is likely, possible or certain to happen to a) installed applications and b) data files when I upgrade via a  clean install?

I'd like to know the same thing. As much as I'd like to upgrade, the thought of installing all my apps and supplementary packages is daunting.

---

### Post by dptxp on 2007-10-20
Is there any specific reason why I see a lot of advice on burning CDs at very low speeds,
as low as 4X ? Very low speeds do not essentially generate better CDs. Yes, very high speeds
can result in poor burns.

I have been burning iso images to CD, at least 50 to 100 so far with speed set at 'AUTO' or 'MAX" in Infrarecorder in Windows XP and K3B in Ubuntu. CDs burn at about 20X speed and I have not had any problem with a single one yet. And my CD writer is pretty old now.

Bad burning can be due to dirty/defective CD drives or bad media. But I guess that the main reasons
are either corrupt iso files (when torrents are not used), or the 'burn image' command is not used.

---

### Post by Lord_Dicranius on 2007-10-20
> **Dr Small said:**
> 
The MD5 Checksums can be found here:
[http://releases.ubuntu.com/7.10/MD5SUMS](http://releases.ubuntu.com/7.10/MD5SUMS)

And to check a checksum, you run:
```
md5sum *ubuntu-7.10-desktop-i386.iso*
```
and it should be the same checksum as the one listed on the website.


Dr Small
Here's the Ubuntu Wiki page for verifying the integrity of the downloads using the MD5 checksums: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM).  Includes a link to a page with **ALL** of the MD5 checksums :)

---

### Post by adamorjames on 2007-10-20
> **dptxp said:**
> Is there any specific reason why I see a lot of advice on burning CDs at very low speeds,
as low as 4X ? Very low speeds do not essentially generate better CDs. Yes, very high speeds
can result in poor burns.

I have been burning iso images to CD, at least 50 to 100 so far with speed set at 'AUTO' or 'MAX" in Infrarecorder in Windows XP and K3B in Ubuntu. CDs burn at about 20X speed and I have not had any problem with a single one yet. And my CD writer is pretty old now.

Bad burning can be due to dirty/defective CD drives or bad media. But I guess that the main reasons
are either corrupt iso files (when torrents are not used), or the 'burn image' command is not used.

If I burn CD/DVDs at a high speed it messes up sometimes. A slow speed has never messed up a CD/DVD for me. :)

---

### Post by Frak on 2007-10-20
1) Burn to CD-R, not CD-RW, there will be much less corruption rate
2) Upgrade a month before/after the release to avoid the rush. Fixes will be downloaded while using Beta or RC.
3) Use entire disk means use entire Hard Disk, not use entire CD-R <- Not kidding, I've seen threads about this
4) Ubuntu is not Windows - Nuff said
5) When upgrading, and speed is slow, goto System->Administration->Software Sources->Mirror->Other->Select Best Server
This will help speed up downloads and spread out the load.

---

### Post by viper on 2007-10-20
As mentioned earlier always wait 2 weeks to a month to upgrade, alot of the bugs should be ironed out by then... and backup prior to any upgrade or fresh install.

---

### Post by bungnati on 2007-10-21
Some people have experienced a "Unable to start the settings manager 'gnome-settings-daemon'" error after upgrade. Solve this by re-installing gnome under Synaptic Package Manager.

---

### Post by Perfect Storm on 2007-10-21
Updated.
fixed some typos.
added some links.

I'll be back for to do more....but for now I'm going to enjoy my sunday :)

---

### Post by grewolf on 2007-10-21
[QUOTE=**9) Have seperated partitions.**
[size=1]A good idea is to have / (root), /home and /boot[/size]
[[size=1]Read more...[/size]](https://help.ubuntu.com/community/HowtoPartition)[/QUOTE]

Why should we seperate the partitions like this?  why is it important to have a boot and a home partition

---

### Post by Perfect Storm on 2007-10-21
If you want to upgrade or clean install, you can still have all your personal stuff and settings if you separating them (/home), the /boot separation is a good idea if you dual/triple boot.

---

### Post by Craigus on 2007-10-21
Thanks, AI. Just a comment:

> e) Intel cards - clumbsyness and/or slow Desktop respond.
install : libgl1-mesa-dri

I found that this was already installed and the latest version on my Intel 82845 based system after a clean install (and I still have crappy scrolling performance :( )

---

### Post by flamingsole on 2007-10-21
> **Artificial Intelligence said:**
> If you want to upgrade or clean install, you can still have all your personal stuff and settings if you separating them (/home), the /boot separation is a good idea if you dual/triple boot.

This will be my first upgrade, as Feisty was my first Linux experience. Does that mean the installation does not have to overwrite the /home or /boot partitions? Thanks.

---

### Post by HokeyFry on 2007-10-22
i have xubuntu feisty installed, and yes, i have modified a few things. but its taken two months to get this laptop the way i want it. what is the danger of upgrading over a clean install?

i have compiz-fusion installed, and xgl, i know gutsy handles xgl a bit differently than in feisty, so i thought it worth mentioning i had it.

---

### Post by Lord_Dicranius on 2007-10-22
> This will be my first upgrade, as Feisty was my first Linux experience. Does that mean the installation does not have to overwrite the /home or /boot partitions? Thanks.
Quick answer: no.  If you need more detail or have further questions, I'd start a new thread.

> i have xubuntu feisty installed, and yes, i have modified a few things. but its taken two months to get this laptop the way i want it. what is the danger of upgrading over a clean install?

i have compiz-fusion installed, and xgl, i know gutsy handles xgl a bit differently than in feisty, so i thought it worth mentioning i had it.
The dangers of upgrading vs a clean install have been discussed quite extensively in other threads in the "Absolute Beginner Talk" forum.  I'd either 1) use the search tool to see if others had their issues resolved, or 2) start your own thread :)

---

### Post by tempusfugit on 2007-10-22
I tryed upgrade my feisty to gutsy in my terminal and through graphical interface but failed both.
this is the error i got:

Error during update
A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry.
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 302 Found

Somebody knows ho to solve this problem?:confused:

edit: my internet is working fine btw

---

### Post by Lord_Dicranius on 2007-10-22
> **tempusfugit said:**
> I tryed upgrade my feisty to gutsy in my terminal and through graphical interface but failed both.
this is the error i got:

Error during update
A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry.
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 302 Found

Somebody knows ho to solve this problem?:confused:

edit: my internet is working fine btw
Create a new thread, por favor.  You won't get much of a response in this thread as this is an advise only thread.  *hint* your issue has been talked about in a few threads in the Absolute Beginner Talk forum, search for it :)

---

### Post by sugarland2k on 2007-10-22
I got though the 7.10 upgrade with Ubuntu and Kubuntu.  It did take some time and several cycles of using apt and as root!  I got familar with dpkg --configure -a but Automatix "goodies" caused some problems.  Had to rebuild my xorg the first cycle... 

But it works!  Hang in there guys!

---

### Post by Frak on 2007-10-22
> **tempusfugit said:**
> I tryed upgrade my feisty to gutsy in my terminal and through graphical interface but failed both.
this is the error i got:

Error during update
A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry.
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 302 Found

Somebody knows ho to solve this problem?:confused:

edit: my internet is working fine btw
Medibuntu's URL has changed.

run
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by tempusfugit on 2007-10-22
Thanks man, im gonna do that after the upgrade, it is upgrading now, i did this:

ain Gnome Menu -> System -> Administration -> Software Sources -> Third Party Software tab -> Untick anything starting [http://medibuntu](http://medibuntu)

hope the upgrade will do its job now.

---

### Post by riverwall on 2007-10-22
I installed succesfully Ubuntu v7.1 but when I wanted to use special effects my video card scratched.
I have a: e-geforce 7300 GT, ddr2 512 Mb PCI-e
 I can't get the drivers. The question is: where to get it?
I found something in this page: [http://www.nvidia.com/object/linux_display_ia32_1.0-8774.html](http://www.nvidia.com/object/linux_display_ia32_1.0-8774.html)
here are some drivers for nvidia cards, I ignore if are good for my card. Please help me.

Thank you all.
Manuel

---

### Post by Frak on 2007-10-22
> **riverwall said:**
> I installed succesfully Ubuntu v7.1 but when I wanted to use special effects my video card scratched.
I have a: e-geforce 7300 GT, ddr2 512 Mb PCI-e
 I can't get the drivers. The question is: where to get it?
I found something in this page: [http://www.nvidia.com/object/linux_display_ia32_1.0-8774.html](http://www.nvidia.com/object/linux_display_ia32_1.0-8774.html)
here are some drivers for nvidia cards, I ignore if are good for my card. Please help me.

Thank you all.
Manuel
Goto System -> Administration -> Restricted Drivers Manager

---

### Post by FlipJones on 2007-10-23
Quick question...
Im a first time Linux user and I still want a dual-boot "security blanket" as it were...

When would I set this up...?

Also, how do I perform manual drive partitions, as the "partition wizard" didn't work when I attempted to install Feisty.

Thanks,

This is my first post, Im glad to see an OS with such a great online community!

---

### Post by Paulmd on 2007-10-23
> **Artificial Intelligence said:**
> [b][color=red]So you want to install/upgrade to the latest version of Ubuntu?

Here's some good advice before proceeding;[/color][/b]

<SNIP>

**4) Download the torrent .iso of Gutsy.**
[size=1]The .iso file will less likely be corrupted than FTP/HTTP download. 
Also it will spare the Ubuntu servers a great deal.[/size]
[[size=1]Read more...[/size]](https://help.ubuntu.com/community/BitTorrent)



Why, exactly would a torrent be less often corrupted than ftp or http? I trust you're not just making that part up to lake the load off Canonical's severs, but I would like to know more.

---

### Post by ckamc on 2007-10-23
Downloaded 7.10 DVD off the official tracker.

MD5 says its corrupt, but when I have utorrent do a hash check it comes up as 100% even tho MD5 does not match up with the one listed on site.

Any Suggestions or alternative minor to check ubuntu-7.10-dvd-i386.iso.torrent with?

```
md5 hash
b5d9aaa45af862b4c804530734216a15

trackers md5 hash
62ece44d0be7ea93ce546f11b8f7abaa44f47da5
```

[B]Edit 

[/B]Disregard my previous post, checked the hash with Azureus which comes up with the same hash as listed on the tracker, I have no idea what winmd5checksum came up with.

---

### Post by AliL on 2007-10-23
> **Paulmd said:**
> Why, exactly would a torrent be less often corrupted than ftp or http? I trust you're not just making that part up to lake the load off Canonical's severs, but I would like to know more.

I believe it's because most torrent programs have an inbuillt piece verification system so if a piece is downloaded and it has a different checksum (as defined in the .torrent file) then it is discarded and re-downloaded.

When downloading directly off the server there is no such security measure and if there is a slight hiccough in the internet connection between you and the server then a byte (or maybe a few more) will be missed therefore resulting in a corrupted download.

It's true that this is just as likely to happen when downloading from a torrent but as the pieces are smaller you only have to re-download a very small portion of the file to fix the corruption. This therefore can save a LOT of time and eases the load on servers as it is individuals who are powering the download.

---

### Post by Frak on 2007-10-23
> **Paulmd said:**
> Why, exactly would a torrent be less often corrupted than ftp or http? I trust you're not just making that part up to lake the load off Canonical's severs, but I would like to know more.
99% of the time, files downloaded using torrents are downloaded in small peices, not only are smaller peices easier to handle, but they contain less entropy to ruin the file overall.

md5sum of the peices help also.

---

### Post by leexgx on 2007-10-23
> The 82% club :popcorn: 
Updates not finding any updates ,
Source error when at 82%,
add/remove not working , 
PLEASE do the below before makeing an new thread (goto the bottem part Software Sources and do that if all ready installed)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/154095](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/154095) if any one who is can change that status can you please set that bug as med or high, as its an bug that should not be apart of the Live CD but it so so we have to work with it untill thay bring an update out for it (New live CD is the only fix)

Recommend Do not connect internet when Installing Or Upgradeing the set up mite or will fail at 82% when connected to the internet, on an fresh install not much of an problem but if your doing an upgrade it mite trash your setup if your online when doing upgrade

Make sure you removed the Network or internet or router cable From your pc before you even turn the PC on as ubuntu does not mark the cable has not pluged in some times and setup mite fail as it keeps looking for repositories online (downloads about 9MB) but Can fail some times and takes the Setup program out with it as well 

once you have performed an upgrade or an fresh install or have all ready installed ubuntu do this (as you get an error avout repositories or sources do the below

> goto System > Admin > software sources

1 Tick all boxs apart form source code (do not think norm users need that)
2 Pick your Download From server location (as it picks main server by default click on search if you cant see one for you)
3 Goto updates and tick the first 2 options (top ones, other 2 is Up to you but should read up first)
4 [recommended but Optional] change the auto up date check to [Download all updates in background] (assuming you do not have an hard disk that is very small its an better option so your ready to install when you are ready just means you do not need to have to wait for them to download)

I do not recommend auto install with out confirmation Option as it may not wait for all updates to be install when shuting down the pc, as it make brake your box

---

### Post by angliski on 2007-10-24
I currently run 3 computers via a wireless network. My daughter's computer has windows, (so enough said) My main machine has a wired netgear router attached and my laptop is wireless. Recently, my main machine showed me an upgrade to gutsy which I did and I have had no problems. Also, my remote printing from my laptop to the main machine has suddenly started working.i have spent months trying to achieve this to no avail. 

So I am pretty happy with gutsy. However, even when I force a search through update manager, my laptop does not find the upgrade to gutsy. I have downloaded the iso image and burned it to CD, but am reluctant to install, in case I wipe out my current data and screw up the windows partition which is also on the laptop and which I use very rarely when ubuntu won't do certain tasks.

Any ideas how I can get the upgrade or how I can install from CD without either screwing up the windows partition or losing all my settings in Feisty.

Cheers

Steve

---

### Post by leexgx on 2007-10-24
plsease read my Last post above yours and that fix it

---

### Post by gopkid06 on 2007-10-25
thanks for checklist. can i use a sata hdd for installing ubuntu ?????

---

### Post by machavillain on 2007-10-25
> 
4) Download the torrent .iso of Gutsy.

Can you provide a link as to where to find the torrent? 
Thanks.

---

### Post by Perfect Storm on 2007-10-25
link added.

---

### Post by MozartlovesUbun2 on 2007-10-25
[B]9) Have seperated partitions.
A good idea is to have / (root), /home and /boot[/B]

PLEASE teach us how :-)

thanks :KS

i managed to get feisty root and home on seperate partitions, so whats the correct way to have **boot** on a seperate partition too?

also i have windows on a seperate partition for games

also somehow my 11GB root is full and giving me severe problems, i thought 11 GB would be enough bu t guessed wrong, it even locked me out once as it became full to the brim and i had to find some cleaning scripts, for a newbie this is disastrous  this should not happen, ubuntu should address this problem, so now i dont know how bigmy root should be

hash: 06DA2A9FC67D404E26B967377DD04293D92EBF74 i will be using the alternative cd for a clean install over feisty, so how big should my root be? and shall i make my swap smaller it is hardly ever used i think

---

### Post by tweistein on 2007-10-26
hello in here - I'm new to linux and have problems getting sound on my Zepto 3215 notebook with ubuntu gutsy. Have been trying various solutions from sites around, including  upgrading alsa-drivers, but after installing alsa-drivers in terminal i get this message ( in terminal)..." WARNING!!! The mixer channels for the ALSA driver are muted by default!!!"
In gui system - properties - sound i get message "cannot connect to sound server" when testing sound. I'm on the verge of giving up...

---

### Post by Perfect Storm on 2007-10-26
MozartlovesUbun2: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by ubunter1 on 2007-10-26
do i need to install(or can i?) extra repositories after installing gutsy?,i noticed the programs for offer is fairly minimal in the add/remove programs menu and i cant find nicotine.?

---

### Post by ubunter1 on 2007-10-26
do i need to install(or can i?) extra repositories after installing gutsy?,i noticed the programs for offer is fairly minimal in the add/remove programs menu and i cant find nicotine.?

opps double post,sorry.

---

### Post by Frak on 2007-10-26
You can still add extra repositories.

---

### Post by ubunter1 on 2007-10-27
any tips to do this or a how to?.thanks.

---

### Post by Frak on 2007-10-27
Goto System -> Administration -> Software Sources -> Then add the apropriate repositories.

---

### Post by northicert on 2007-10-28
This note may help someone upgrading to Gutsy 7.10.  It helped me. [http://osnovice.blogspot.com/2007/10/slow-internet-connection-in-ubuntu.html](http://osnovice.blogspot.com/2007/10/slow-internet-connection-in-ubuntu.html)  It tells you to make a change in Firefox, about:config.

---

### Post by abhilash82 on 2007-10-29
I have upgraded to gutsy and everything seems to be fine other than the compiz fusion that is part of the same. My window borders disappear when I try to enable it. Do I have to install any window decorator package for this. I was able to use compiz with my earlier installation with Feisty.

---

### Post by sethviloria on 2007-10-30
hi everyone..
been using ubuntu for 2 months now. started with Feisty then on to Gutsy.

Here's what I did:
Made 3 partitions on my HDD, 1 partition for system,swap, and storage.

Mounted my storage partition as home and whenever i tried diff distro, i always format my system partition and delete everything except my docs on /home partition.

Partitioning did help me:
1. Preserve my files (from micro$oot OS) and
2. Encounter less probs with configs.. (always started out with default ubuntu config :D)
3. Test tweaks i read abt in [http://ubuntusoftware.info/Howto_tweak_ubuntu_ultimate.html](http://ubuntusoftware.info/Howto_tweak_ubuntu_ultimate.html)
Done it all by reading the forums.

Nice ppl here.. :-)

---

### Post by sethviloria on 2007-10-30
...and ext3 doesnt fragment. c00l features
no viruses, writes on ntfs, runs win32 progs, endless posibilities..

yes, i crashed it a few times using sysv-rc-conf but its all for the best in the end.
cheers :D

-seth

---

### Post by peterjohn on 2007-10-31
Hi,

Everyone says to wait like a month after a new version is released, well I just wanted to know like how I would find out about any bug fixes and when you think I should try out gutsy

thanks

-peter

---

### Post by fivesmellydragons on 2007-11-01
I just tried Gutsy yesterday and I really like it. It downloaded easy, through a torrent file, was quick to install, just like Feisty, and I didn't have to go through a lot of fixes to get everything up and running like in Feisty. Feisty was and still is much easier than Windows, but Gutsy already had everything that I wanted. I had to install my printer/scanner, but that was really it.

---

### Post by gg234 on 2007-11-02
if you are looking for upgrade tutorial with screenshots take a look at[ this nice guide]("http://www.ubuntugeek.com/upgrade-ubuntu-704-feisty-fawn-to-ubuntu-710-gutsy-gibbon.html")

---

### Post by jhenager on 2007-11-03
I live on the edge. When I saw upgrade available, I went for it.
Dapper>Edgy>Feisty>Gutsy all upgrades. Only small problems, like gdesklets quit working (uninstall, delete .gdesklets folder, reinstall), and OpenOffice didn't like it (uninstall, reinstall).
C'mon, scaredy cats!!! If you lived thru Windows, what's a few more chances to take?
:)

But if the data is important, you can't have too many backups....

---

### Post by TA BOSS on 2007-11-04
So - I replaced a broken hard drive on my old Compaq PC desktop.  I used a hard drive from an external hard drive.  Then I got this Ubuntu disk from a friend of mine.  The OS seems to only load from the DVD drive but does not give me any option to place it on the hard drive.  This is apparently too simple of a problem because I can't find the answer online and my friend doesn't know why there is no option to install it either.  Can anyone help?

Thanks

---

### Post by silkstone on 2007-11-05
When Ubuntu has loaded from the CD, there should be a desktop 'Install' icon giving you the option to do a full install.

---

### Post by Rafadagaffer on 2007-11-08
I would like to install Gusty but I tried the live cd and it wouldn't load due to my graphics card. I know I can download the alternate cd and install that way but will I be able to run gutsy from gnome or will I have to get drivers using the command line version ?

If I upgrade from within 7.04 will I see the same problems? Ive got my desktop the way I like it now, I don't want to lose that but still want to upgrade. Time to go do a backup I think

---

### Post by Aqonis on 2007-11-08
Approx. how big should the /boot /root partitions be?

---

### Post by nooby on 2007-11-11
I'm trying out wubi version of kubuntu. Do I have to join that forum and do I have to register again there? Could I use same username as here? 

kubuntu seems to not have a email client and no firefox? 


I failed to edit my first entry as a kubuntu user. Should I activate java or something? 

How?

---

### Post by overdrank on 2007-11-11
> **nooby said:**
> I'm trying out wubi version of kubuntu. Do I have to join that forum and do I have to register again there? Could I use same username as here? 

kubuntu seems to not have a email client and no firefox? 


I failed to edit my first entry as a kubuntu user. Should I activate java or something? 

How?

HI and Konqueror is the web browser in KDE. You can use these forums as alot of users use KDE desktop environment here. As for email you may find some good info here.
[http://www.kde.org/documentation/](http://www.kde.org/documentation/)
You will need to install java and other restricted formats here is a good link
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
Good luck and hope this helps. :KS

---

### Post by Frak on 2007-11-11
> **nooby said:**
> I'm trying out wubi version of kubuntu. Do I have to join that forum and do I have to register again there? Could I use same username as here? 

kubuntu seems to not have a email client and no firefox? 


I failed to edit my first entry as a kubuntu user. Should I activate java or something? 

How?
KMail is the default email, and Konqueror is the default browser.

---

### Post by Bruce M. on 2007-11-14
> **Paulmd said:**
> Why, exactly would a torrent be less often corrupted than ftp or http? I trust you're not just making that part up to lake the load off Canonical's severs, but I would like to know more.

Check out the thread I started, because I want to upgrade  too:
[URL="http://ubuntuforums.org/showthread.php?t=606989"]
BitTorrent: Advantages/Disadvantages[/URL]

It was an eye-opener for me.  But to give you a short answer:  No, nothing is "made up", it will relieve Ubuntu's servers.

Here is one of the greatest advantages: (Taken from the thread)

> **Credit to: rsambuca:** One thing I just wanted to mention that I haven't seen here. Another benefit of using torrents is that the hash of each piece of the torrent is checked as you download it, so you are more likely to get an uncorrupted file than by regular http downloading. If a piece fails the hash check, it is chucked out immediately and re-downloaded from somewhere else.

If you have a slow connection, it *might* take a little longer, but the chance of having to re-download do to a corrupt file is greatly reduced.

Have a nice day.

---

### Post by Bruce M. on 2007-11-14
> **Artificial Intelligence said:**
> [b][color=red]So you want to install/upgrade to the latest version of Ubuntu?

Here's some good advice before proceeding;[/color][/b]

**3) Go for Clean install instead of upgrade.**
[size=1]No matter which OS or distro, an upgrade may be a hazardous process, especially if you have non-official libs/apps installed or if you have heavy modified your OS.
If you kept to the official sources there should be no problem upgrading.[/size]

If I do a clean install, I loose every program I have installed that is NOT a default.  Or config changes (like changing my default file browser to Thunar).

I'm using System>Administration>Home User Backup weekly.  But wouldn't Home User Restore overwrite some of Gutsy's system files somehow?

For what it is worth here is what I have in Synaptic:

All
Local/main
Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)/main
Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)/restricted
ar.archive.ubuntu.com/main
ar.archive.ubuntu.com/multiverse
ar.archive.ubuntu.com/restricted
ar.archive.ubuntu.com/universe
archive.ubuntu.com/multiverse
archive.ubuntu.com/universe
debian.websterwood.com/main
packages.medibuntu.org/main
packages.medibuntu.org/universe
security.ubuntu.com/main
security.ubuntu.com/multiverse
security.ubuntu.com/universe
--------------
debian.websterwood.com/main - has no files installed.  I didn't like the Webshot program and deleted it.

Or, am I fairly safe to *upgrade*?

---

### Post by zaprenki on 2007-11-14
Hi there...
I am currently using ubuntu 7.04 at my "main" pc, and just loving it. I 've also installed 7.04 on my laptop and upgraded to 7.10 to check it out. No problems so far, so I was wondering if it's time to upgrade my "main" pc to 7.10 too. Is it a good time, or should I wait some more, in case more bugs come out? Using 7.10 on my laptop so far didn't bring up any kind of problems whatsoever...

---

### Post by 504harry on 2007-11-14
> **dptxp said:**
> Is there any specific reason why I see a lot of advice on burning CDs at very low speeds,
as low as 4X ? Very low speeds do not essentially generate better CDs. Yes, very high speeds
can result in poor burns.

I have been burning iso images to CD, at least 50 to 100 so far with speed set at 'AUTO' or 'MAX" in Infrarecorder in Windows XP and K3B in Ubuntu. CDs burn at about 20X speed and I have not had any problem with a single one yet. And my CD writer is pretty old now.

Bad burning can be due to dirty/defective CD drives or bad media. But I guess that the main reasons
are either corrupt iso files (when torrents are not used), or the 'burn image' command is not used.

Hi, 
I guess it stems from a natural instinct that. . . .  follows the mechanical equivalent of paint-spraying - the faster you do it the thinner the coat . . . (this then requires more coats, for a good job). I'm not convinced that this is the same as burning a CD since the laser-power can be ramped-up.
.
 I tend to agree that allowing the computer to set the burn-speed is "probably best" - since it isn't in the software-developer's interest to produce dead CD's.  If you check "verify" then I presume it does just that - it certainly more than doubles the time to finish buring a CD.  Under Nero ( OK it's Win ), it seems to do a reasonable job, although the creation of ISO/images ( or whatever) I find VERY confusing.

---

### Post by michaelpagz on 2007-11-17
Hi Guys! I'm trying to upgrade to 7.10, but every time i try to upgrade through my update manager. I hit a wall every time with these three alerts at which point it shuts down the upgrade manager!


Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_amd64.deb) 403 Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_amd64.deb) 403 Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_amd64.deb) 403 Forbidden

what can I do to fix this? I'm sort of a newcomer to linux and ubuntu... i am running 7.04!
thank you very much and please help.
mike

---

### Post by Frak on 2007-11-17
> **michaelpagz said:**
> Hi Guys! I'm trying to upgrade to 7.10, but every time i try to upgrade through my update manager. I hit a wall every time with these three alerts at which point it shuts down the upgrade manager!


Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_amd64.deb) 403 Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_amd64.deb) 403 Forbidden
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_amd64.deb) 403 Forbidden

what can I do to fix this? I'm sort of a newcomer to linux and ubuntu... i am running 7.04!
thank you very much and please help.
mike
Everybody is having that error, just wait until it is resolved.

---

### Post by michaelpagz on 2007-11-17
alright! that works. thank you.

---

### Post by ugm6hr on 2007-11-18
> **Artificial Intelligence said:**
> 
**f) Slow bootup?**
[size=1]This might be the problem + solution - [[size=1]this thread[/size]](http://ubuntuforums.org/showthread.php?t=580903).[/size]


This is actually a much more elegant solution:
[http://ubuntuforums.org/showthread.php?t=581075](http://ubuntuforums.org/showthread.php?t=581075)
Specifically - reply 2: [http://ubuntuforums.org/showpost.php?p=3568252&postcount=2](http://ubuntuforums.org/showpost.php?p=3568252&postcount=2)

---

### Post by bsmith1051 on 2007-11-20
All I've read so far is the first 2 pages so please forgive me if this has already been said.
1. The initial post is very well written and organized, thank you!
2. The initial post seems more like an Super CYA method of fresh install, and has no real advice about how to safely upgrade.
3. Aren't there a lot of gotchas to backing-up and 'restoring' your /home directory?

I just posted a suggested FAQ in the "Install/Upgrade" sub-forum, something very similar (but simpler) than this one.  Call me crazy but I never thought to look in the Absolute Beginners sub-forum for upgrade advice...

---

### Post by king2007 on 2007-11-20
as an absolute beginner can i throw in that i have had windows vista ultimate installed february this year. now reading a lot about Linux and Ubuntu seems to me quite something different and promising ;
downloading the .iso-image and burning it on a cd one realizes this ubuntu-system needs it's own section or part of a
hard disk. what vista càn do is shrink it's own partition so i guessed some 40 Gb would be enough for Ubuntu. The format however was done in NTFS which unfortunately is not used by Ubuntu.... So the next problem was how to re-format the new space. Luckily on the Ubuntu CD one can click a Partition Manager, called Gpart. Search and you'll find it. Formatting than to Ext3 was very quickly done. Trying to install Ubuntu from the CD onto the new partition was not easy. How about mounting point ? Never heard of. Searching forums did not quite specify this small problem.
Searching online - during installing mind you - with the fabulous Firefox gets you to using a slash "/" for mounting point and Swap for a small part of the new partition for a swap-file. Having passed to step 5 or 6 of 7 Ubuntu finalizes the install. Upon restarting there is a new screen showing Ubuntu (by grub) and the Windows-installer - choose quickly. A whole new screen very different than from the CD shows and some 81 updates !! to be downloaded and installed. Strangely enough nothing wrong with my ethernet-card and speedtouch-modem which work without any problem. What is a problem is my password. Restarting Windows normally activates my NumLock. Not having sighted the green light showing on or off i start keying in my password in letters and numbers. Rightfully so it is not accepted by Ubuntu ? That is what I am going to solve now and also try to find out what the relation is between Ubuntu and roasted coffee and all the marvellous avatars flying around and brewmasters and hidden beancounts.....

---

### Post by boyle508 on 2007-11-27
Hi I upgraded from 7.04 to 7.10 and lost my internet connection spent a week trying to get it back.Then tried a clean install of 7.10 same problem again.
When booting up next time I changed back to an earlier version and got my internet connection back.
And I was looking through the synaptic manager updates and checking them against what was on my computer, and noticed that it was a generic version for the update and not the 
i386 version. So I marked the 7.10 i386 version for updating and now I running 7.10 with no problems with my internet connection.
through it may help :)

---

### Post by FlipJones on 2007-11-27
Generic Version???

---

### Post by Bruce M. on 2007-11-27
> **FlipJones said:**
> Generic Version???

Yup... mine is the same:

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=615f0c8f-d90d-4910-8361-8b43750446a2 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=615f0c8f-d90d-4910-8361-8b43750446a2 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		M$ 2000 Crashes
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---------------
Now I'm curious as to why?  I'm sure I downloaded the i386 version.
I had almost forgotten that I still have M$ in there,

---

### Post by RSrealo on 2007-12-08
I am using 7.04 and I am loving it. After installing Gutsy I had hard time (Lagging and hogging sys) playing my online Java game. 

7.04 is the perfect OS for me atm :) for my Hp laptop and Pavilion desktop.

---

### Post by Jeandré on 2007-12-12
Is it possible to download an iso with all the new security updates (effectively 7.12), or download all the new security updates and then easily install them from a USB drive or CD? I don't have a fast connection at home, but have access to a fast connection elsewhere.

---

### Post by slikwill on 2007-12-13
Item 9 advises to create partitions,which sounds good, and I followed the link to the ubuntu documentation.  There it tells me:"Open the Gnome Partition Editor from the System Administration menu.", but under my 7.04 System Administration the Gnome Partition editor does not exist.  Please advise.
 PROBLEM SOLVED!!
I did a search under add/remove applications and found and installed it.  I guess the answer for me is if I don't find a capability instlled, look ubder applications and packages for it.  By the way, what is the difference between an application and a package?

---

### Post by ugm6hr on 2007-12-14
> **Jeandré said:**
> Is it possible to download an iso with all the new security updates (effectively 7.12), or download all the new security updates and then easily install them from a USB drive or CD? I don't have a fast connection at home, but have access to a fast connection elsewhere.

After installing - try this to locate and download all the updates:
[http://ubuntuforums.org/showthread.php?t=572819](http://ubuntuforums.org/showthread.php?t=572819)

---

### Post by Lord_Dicranius on 2007-12-14
> **slikwill said:**
> By the way, what is the difference between an application and a package?
They're basically the same thing.  An application, for example, Firefox.  The package is the .deb file (or .rpm, or others, depending on the operating system) that holds all the source code and installation instructions to install the application.

---

### Post by applelover on 2007-12-17
:KSstep by step to  rip DVD and convert Video to iPod at the under link , I hope it can help someone .

---

### Post by KoolBeans on 2008-01-05
I am new to Linux. Tired of the problems in Winblows. Since I am new there is a learning curve.

When I say new, I mean, tried livecd for two days third day installed on my comp. No previous experience with linux.

I would like to see in Absolute Beginners:
A. Installation
   A1. Clean install - step by step, maybe even screen shots.
   A2. Install with partition: A.K.A. Dual boot O.S.
B. Initial steps after you install Ubuntu
   B1. Nescesary maintenance and setup
   B2. Updating
   B3. Restricted formats
   B4. Things to check to make sure of propper operation. Video, Audio, Plugins, Programs...

Something like this is what I would have expected in a sticky. 

A sticky should be limited to posts by Admins, Mods, and certified experienced users. This would create a channel of trusted information that would reduce frustration on first timers not familiar with programming structure and language. Posting to sub threads can be done by those seeking help.

The Topics structure seems a little confusing on the menu page. By looking at it I don't feel I can find what I need by topic and sub topic.

Currently videos on the web sometimes work sometimes don't. Can't download the Macro flash player via add/remove. Unsure how to install the Adobe version. I am not sure how much of these probs are related to my ATI radeon. 
I don't have sound right now, not sure how to fix that.

I really need an ABC Guide.

Post #34 would like to see this as a sticky.
Post #49 would like to see this step by step; 3 partitions? What are the benefits and features of this? What are the drawbacks of this? What is microboot?

(I have a Toshiba Satalite A215 7422, Win Vista Premium, Ati video, 160gbhd)-incase someone can point. Using Ubuntu Studio.

---

### Post by onryou on 2008-01-17
Also fairly new to linux. Wasn't sure if I should make a post or not so sorry if this is in the wrong place.I downloaded and burned the Gutsy 64bit Live CD. I verified the burn and it said everything checked out. When I booted up with the CD I got the startup screen just fine but when I try to choose Check CD for defects or Install/Boot from CD it loads the kernal and then restarts the computer. I tried removing quiet and changing to nosplash in options however it difficult to see where it restarted since it sort of flashes by. Could the CD be faulty? My specs:

Gigabyte GA-P35C-DS3R
8800GTS 640MB

---

### Post by ugm6hr on 2008-01-18
> **onryou said:**
> Also fairly new to linux. Wasn't sure if I should make a post or not so sorry if this is in the wrong place.I downloaded and burned the Gutsy 64bit Live CD. I verified the burn and it said everything checked out. When I booted up with the CD I got the startup screen just fine but when I try to choose Check CD for defects or Install/Boot from CD it loads the kernal and then restarts the computer. I tried removing quiet and changing to nosplash in options however it difficult to see where it restarted since it sort of flashes by. Could the CD be faulty? My specs:

Gigabyte GA-P35C-DS3R
8800GTS 640MB

Always hard to know what the problem is in this situation.  Have you tried the "safe graphics mode"?

Presumably you do have a 64-bit processor?  My advice is to stick with the 32-bit version (which will work with 64-bit processors as well) if you are new to Linux, because things are just a bit trickier with 64-bit at the moment.

It could be the CD - people generally recommend burning at a slow speed.  Can you try it in another computer?

Also - some people can only install with the Alternate CD....

PS: I would recommend starting a new thread with your own problems, just because these how-to threads tend to meander a bit.

---

### Post by louaym on 2008-02-14
KoolBeans requested ABC guide; 
I have found this documentation is very much what you are asking for; take a look

[https://help.ubuntu.com/7.04/installation-guide/i386/](https://help.ubuntu.com/7.04/installation-guide/i386/)

---

### Post by bsmith1051 on 2008-02-15
That official install guide is too long.  If it's got the specific details I've been looking for, I couldn't find them.

Having too much detail can be just as 'bad' as too little.  It really is an art, finding the right balance.  And, of course, not everyone wants or needs the same level of detail.  Still, for instance, this official guide starts off with 4 or 5 pages of background on Canonical and Debian, like that has anything to do with figuring out how to install Ubuntu...

---

### Post by Sonic Alpha on 2008-02-15
Hi there,

Just need to ask a quick question...

I currently have version 6.06 of Ubuntu installed, and plan to upgrade to the latest version. When I go to do a clean install, how do I go about it?

Is it just a matter of popping the CD in, and letting the installer format the existing Linux partition?

Apologies if this has already been answered.

---

### Post by Kilz on 2008-02-18
> **Sonic Alpha said:**
> Hi there,

Just need to ask a quick question...

I currently have version 6.06 of Ubuntu installed, and plan to upgrade to the latest version. When I go to do a clean install, how do I go about it?

Is it just a matter of popping the CD in, and letting the installer format the existing Linux partition?

Apologies if this has already been answered.

More or less yes.

---

### Post by bsmith1051 on 2008-02-18
> **Sonic Alpha said:**
> I currently have version 6.06 of Ubuntu installed, and plan to upgrade to the latest version. When I go to do a clean install, how do I go about it?
Ideally you'll get a new hard drive and then clean-install onto that.  Not only does this avoid any attempt at upgrading but it also gives you an excuse to get a bigger faster more-reliable drive!

FYI - You do *NOT* want to upgrade from more than 1 release 'behind' (like your 6.06),
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by sarojgupta on 2008-02-27
Hi, I need some help. I've managed to install ububtu studio 7.10 dual booting with win xp. The xp boots up fine but em having problem booting ububtu studio 7.10. It boots up about 80% and then freezes. Can anyone help PLEASE!

---

### Post by bsmith1051 on 2008-02-28
> **sarojgupta said:**
> having problem booting ububtu studio 7.10. It boots up about 80% and then freezes. Can anyone help PLEASE!
Please start a new thread with your question.  You'll get a LOT more responses than you will hijacking this more general thread.

---

### Post by garry_garrett on 2008-03-20
Uh, I think you're missing a step between 8 & 9, and that would be how to install Ubuntu itself.  I selected the install/upgrade option, but it seems to just boot off of the cdrom and take me to a prompt that says

(initramfs)

Now what?  I see a bunch of unix commands listed, but none of them jump out at me as anything that would install Ubuntu off of the cdrom onto my hard disk.

---

