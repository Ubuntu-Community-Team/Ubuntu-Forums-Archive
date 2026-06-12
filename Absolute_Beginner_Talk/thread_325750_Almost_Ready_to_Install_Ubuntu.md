---
title: "Almost Ready to Install Ubuntu"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by S.D.K. on 2006-12-26
Hello.
For the last few months I've been wanting to try out linux. After talking to few people and read somethings on the net Ubuntu seem like the right one for me.
I tried the Live CD (6.06) and it worked on my computer, detected my printer and internet connection so I shouldn't have many problems.

What I intend to do is have my computer Dual Boot with Window Xp on my C drive and Ubuntu on my spare F drive. I read the (slightly confusing) articles and post here and found a excellent Video tutorial to guide me.

What I am asking for how should I partition that drive? Right now it is FAT32 93 GB drive.

---

### Post by MrKlean on 2006-12-26
I would let Ubuntu format it for you. It will put all the partitions you need. I think Ubuntu could write to it cause it's a fat32, but let Ubuntu do it's thing.  Unless your a gamer, you might find yourself switching to Ubuntu all the time.  There is some learning involved, but I found the help here great, and fun ; )
Enjoy !

---

### Post by S.D.K. on 2006-12-26
Thanks MrKlean.
But how much space should I allot to each partion?

---

### Post by gn2 on 2006-12-26
I would strongly suggest you try this: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by lyceum on 2006-12-26
That depends on what you are wanting to do. Ubuntu will need 2-5 gigs, then the rest.... is up to you. If you want to use your home folder as your main folder location for your files, I would give yourself 10 gigs or more. Maybe leave the rest as a swap partition? But again, it all depends on what you want to do.

---

### Post by S.D.K. on 2006-12-26
Well, am finally using Ubuntu.
The Installation process was quite painless.

Works wells.
I installed it as using the link gn2 posted which was very helpful.
However after I pluged in my XP drive to make sure it was okay and restating to go back on Ubuntu I get this error

/bin/sh: can't access tty; job control turned off.

I used the search function and from what I gather is that Ubuntu is trying to load up by searching  the first Drive which is my Windows one.

What can I type in on the command prompt to make Ubuntu load the proper drive without having to open my computer again and rearrage the drive connection.

---

### Post by lyceum on 2006-12-26
If you did not have XP plugged in Ubuntu would not know to set up the thing that lets you pick your OS at startup. (Yes, thing is a technical term :)) You may want to re-install with XP plugged in. Just BACK UP FIRST!!! (sorry to raise my voice, that part is important!)

---

### Post by esaym on 2006-12-26
For my dual boot I installed windows first on a 4gb primary partition (you can only have 4 primary partitions) .  Then with the rest of the free space I made one giant extended partition. Out of that extended partition I made a small 2gb ntfs logical partition for windows.  Then I put the ubuntu cd in and installed it to another 5gb logical partition and then rest of the space I partitioned for /home.

---

### Post by WebJoel on 2006-12-26
> **S.D.K. said:**
> Hello.
For the last few months I've been wanting to try out linux. After talking to few people and read somethings on the net Ubuntu seem like the right one for me.
....What I intend to do is have my computer Dual Boot with Window Xp on my C drive and Ubuntu on my spare F drive.....
 I have *exactly* the same situtation (except my 2nd HDD is "E:\", not "F:\"), -not that I can offer any assist at this time, but am closely watching your thread (and mine as well!) for further happenings and thoughts/advice, -before I take the big plunge. (Sorry to hijack your thread, -just wanted to introduce myself again) :D

---

### Post by S.D.K. on 2006-12-26
Well, I just came back from work.
So I guess I should reinstall Ubuntu on my spare drive now.
Not much of a hassle, as I took all my data out of my F drive before I installed Ubuntu on it.
[Funny story, I spent 10 minutes trying to find the command line prompt on Ubuntu before I found out it was the "Terminal" program.]

Well going to reinstall Ubuntu while the XP drive is still connected, wish me luck.

BTW, anyone knows how easyUbuntu works?:-k

---

### Post by S.D.K. on 2006-12-26
Alright, I can use Ubuntu again!
...now I just have to figure out what I'm going to do with it, lol.
(after doing the neccassery updates)

Okay, I reinstalled Ubuntu using the 6.06 live disc again and use the default setting when it ask me about partitoning and stuff. 
Triple check to make sure that it installed on my F drive and not my C (XP) drive.

Once I reset my computer,  I went into the BIOS boot option and tried to boot from my Ubuntu drive.

On the Grub menu I tried to load Ubuntu. 
That didn't work..
I tired all the options but I keep getting the same error

root (hd1,0)
Filesystem type unknown, partition type 0X7
Kernal /boot/vmlinuz-2.6.15-26-386 root=/dev/hdb1 ro quset splash
Error 17: Cannot mount selected partition

After panicing again, I restated and selected my Windows Drive to make sure I could still boot from there.

Strangly, I though, I was back on the Grub menu. I selected the XP option and check that Ubuntu had not intalled on my Windows drive. 
It didn't, thank God.

Restarted my computer and selected the Windows drive from my BIOS boot option again.
Select Ubuntu from the Grub menu....

And now I'm using Ubuntu again! Did the Update thing and now I'm typing this message on firefox using Ubunut on my F drive.

A few bumps along the road but overall it was a ride that I could manage without me have to break my computer apart.

Thanks for your help guys.

---

### Post by riven0 on 2006-12-26
Great! :mrgreen: Now you'll probably want [easyUbuntu]("http://www.ubuntuforums.org/showthread.php?t=84742") to install all the necessary codecs. Good luck. :KS

---

### Post by S.D.K. on 2006-12-26
Thanks riven0.
Alas, I have no idea on how to get easyUbuntu working.
The instruction on the website left me scratch my head as following the instructions did...nothing.
Maybe I'm not as computer literate as I though.

---

### Post by riven0 on 2006-12-26
Alright, first click on [this link]("http://easyubuntu.freecontrib.org/files/easyubuntu_latest.deb") to download it. 

Then go to the terminal: **Applications** >> **Accessories** >>** Terminal**.

Copy and paste this in:
> 
wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -

Now, go to where you saved the file and double-click on it. Then click **Install Package** and it will guide you through the rest.

Tell us if you have problems.

---

### Post by S.D.K. on 2006-12-26
Alright got EasyUbuntu to open up.

I get these errors:

W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_multiverse_binary-i386_Packages)

It tells me that I can't install packages and to fix errors first.

---

### Post by riven0 on 2006-12-26
Okay, can you post your sources.list? Open the terminal and copy and paste this:

> cat /etc/apt/sources.list

Then paste the results here and we'll see what we can do.

---

### Post by S.D.K. on 2006-12-26
"cat /etc/apt/sources.list" yielded this:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by riven0 on 2006-12-26
So let's try this:

First, in the terminal again, let's make a backup copy:

> sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup

Now, let's edit the file:

> sudo gedit /etc/apt/sources.list

This should bring up gedit with your sources list. Now delete everything there and paste this instead:
> 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

Save it, close it, and you should return to the terminal. Now copy and paste this, (do this **twice**,  - if there are any errors apt should correct them):

> sudo apt-get update

Then:

> sudo apt-get upgrade

Then try easyUbuntu once more and see if it works.

---

### Post by S.D.K. on 2006-12-27
Thank you riven0 for the help
However I get this error now:

[http://us.archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)

---

### Post by riven0 on 2006-12-27
Hmm, strange...:-k 

Okay, one more time! :D 

> 
sudo gedit /etc/apt/sources.list

Now, once again, delete everything and paste this in, (don't worry about making a backup since we did that before):

> ## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main 

Now, again run **sudo apt-get update** at least twice, and then **sudo apt-get upgrade**. See if it results in any errors.

---

### Post by S.D.K. on 2006-12-27
riven0  you are awesome!
It is now downloading the packages instead of giving me error messages.
You have my thanks.

[BTW can any mods/Admins rename my thread into "Installing Ubuntu to dual boot with Xp on 2nd HDD and easyUbuntu problems"?]

---

### Post by riven0 on 2006-12-27
Alright! :KS All thanks to [psychocats]("http://www.psychocats.net/ubuntu/sources"). :mrgreen:

---

### Post by gn2 on 2006-12-27
> **S.D.K. said:**
> Well, am finally using Ubuntu.
The Installation process was quite painless.

Works wells.
I installed it as using the link gn2 posted which was very helpful.
However after I pluged in my XP drive to make sure it was okay and restating to go back on Ubuntu I get this error

/bin/sh: can't access tty; job control turned off.

I used the search function and from what I gather is that Ubuntu is trying to load up by searching  the first Drive which is my Windows one.

What can I type in on the command prompt to make Ubuntu load the proper drive without having to open my computer again and rearrage the drive connection.

Did you install Ubuntu while connected to the master?

Needs to installed  while connected to the connector it will be "living" on. i.e. slave.

My method doesn't work for everyone, but be aware of the need to read up on Grub editing for the future if Grub has been installed to the Windows drive MBR.

Enjoy Ubuntu it's ace. As is any Linux distro that works for you....

---

