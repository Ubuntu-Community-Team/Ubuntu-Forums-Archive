---
title: "New User"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by harley87 on 2008-02-06
Hi There. I have just installed Ubuntu onto my laptop replacing Vista. When selecting the partioning options it only gave me the option of partioning all of my HD. I can now no longer get into my Vista account. Would this have anything to do with that? I wish to retrieve files from my VIsta account and place them onto Ubuntu. Is there any way I can now do this?

Thanks.

Andrew.

---

### Post by Nythain on 2008-02-06
oh mate, i hate to tell you this, but if it only gave you the option "partition entire hard drive" and you selected that... there's a pretty good chance Vista, your files, and anything else that was on that hard drive before ubuntu, is now gone.

basically, what it did, was nuke any partitions on the hard drive to free up the entire hard drive, then create its own partitions, and format them accordingly.

hopefully this isnt the case, but thats what it sounds like

---

### Post by mister_pink on 2008-02-06
I'm afraid if you selected that option then it will have done just that - used all the hard disk. There won't be any of vista or your files left. You should always backup important things before doing something as major as installing an OS on your computer. Sorry, but unless you have a recent backup I don't suppose theres much you can do.

---

### Post by jaytek13 on 2008-02-06
If you chose the option to use the entire disk, there really won't be an effective way to retrieve those files, unfortunately. There is always the option of using a product that restores deleted files, but as you installed over Vista the chances of that working are pretty slim.

There are 2 options during install.. use the entire disk, or make room for the ubuntu partition, for which the latter would have simply resized the Vista partition, leaving Vista and the files alone, while installing Ubuntu on remaining space... But there's no way to turn this back after having formatted the entire disk with Ubuntu.

---

### Post by kbless7 on 2008-02-06
If you put vista back on, you need to use its partioning software thats built in to create a "large continuous space." That way you don't delete all of the files again.

---

### Post by seventhc on 2008-02-06
That isn't the only option it gives you, there is an option for manual or guided use remaining free space. By default it is set to use the entire drive and you're supposed to change it. If you didn't change it, then vista is gone. :(
to be certain, open a terminal and put this in:
```
sudo fdisk -l
``` If you see a partition with NTFS then vista is still there, if not...sadly it is gone.

---

### Post by harley87 on 2008-02-06
Ok thanks. I didn't really have any majorly important files, mainly just music and the like, which will be a pain to recover but ah well! Anything else like programs and such like can be re-installed. Another quick question though. Trying to install Skype and I'm getting the message - Error: Dependency is not satisfiable: libqt4-core. Any Suggestions? Also what are the alternatives to MSN Messenger, so I can keep my contact lists etc? Or are there ways of being able to download it on Ubuntu?

---

### Post by brettg102 on 2008-02-06
I'd suggest GAIM (Pidgin) for your messenger needs. It should recover your MSN buddies no problem, as well as other messenger services.

---

### Post by jaytek13 on 2008-02-06
> **harley87 said:**
> Ok thanks. I didn't really have any majorly important files, mainly just music and the like, which will be a pain to recover but ah well! Anything else like programs and such like can be re-installed. Another quick question though. Trying to install Skype and I'm getting the message - Error: Dependency is not satisfiable: libqt4-core. Any Suggestions? Also what are the alternatives to MSN Messenger, so I can keep my contact lists etc? Or are there ways of being able to download it on Ubuntu?

Most people prefer either amsn or kopete for msn messenger replacement, but you can also use pidgin (but the other 2 are generally regarded as having the closest feature set to msn messenger). 

As far as libqt4-core is concerned, you should be able to 
```
sudo apt-get install libqt4-core
```

from the command line and that will satisfy that dependency.

---

### Post by SOULRiDER on 2008-02-06
> **brettg102 said:**
> I'd suggest GAIM for your messenger needs. It should recover your MSN buddies no problem, as well as other messenger services.

GAIM is ancient. Its now called pidgin. [http://pidgin.im](http://pidgin.im)

Its is in the repos, although now the latetst version. You can get the packages of the latest version on [http://getdeb.net](http://getdeb.net)

---

### Post by crjackson on 2008-02-06
> **harley87 said:**
> Ok thanks. I didn't really have any majorly important files, mainly just music and the like, which will be a pain to recover but ah well! Anything else like programs and such like can be re-installed. Another quick question though. Trying to install Skype and I'm getting the message - Error: Dependency is not satisfiable: libqt4-core. Any Suggestions? Also what are the alternatives to MSN Messenger, so I can keep my contact lists etc? Or are there ways of being able to download it on Ubuntu?

For Skype try this:   [http://www.skype.com/go/getskype-linux-ubuntu](http://www.skype.com/go/getskype-linux-ubuntu)

For MSN try this:    [http://www.getdeb.net/download/1978/0](http://www.getdeb.net/download/1978/0)

---

### Post by seventhc on 2008-02-06
amsn will support web cams, pidgin won't. I generally use pidgin for yahoo, if cam support is needed I'll open kopete and for msn I always use amsn.

---

### Post by harley87 on 2008-02-06
Ok thanks for all the help guys! I'm new to all of this so I really appreciate it. Doing a course in Computing and had never experienced Linux until last September, but even now after the problems I've already had, partly through my own fault, I prefer it to Vista.

harley@harley-laptop:~$ sudo apt-get install libqt4-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libqt4-core
harley@harley-laptop:~$ 

Tried the above command to get skype to work with no luck. Any help?

---

### Post by jaytek13 on 2008-02-06
> **harley87 said:**
> Ok thanks for all the help guys! I'm new to all of this so I really appreciate it. Doing a course in Computing and had never experienced Linux until last September, but even now after the problems I've already had, partly through my own fault, I prefer it to Vista.

harley@harley-laptop:~$ sudo apt-get install libqt4-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libqt4-core
harley@harley-laptop:~$ 

Tried the above command to get skype to work with no luck. Any help?

Hm... You can search for the package in Synaptic (System->Administration->Package Manager) I think

---

### Post by lswest on 2008-02-06
i believe you need to enable the other package resources through system-->administration-->software sources, and check all the boxes other than the CD-ROM on the ubuntu software tab (the tab it opens on).  Then try reinstalling skype

---

### Post by harley87 on 2008-02-06
Have tried the above suggestions for Skype, the libqt4-core file does not appear in the Package manager list. Is there anywhere I can download it from?

---

### Post by brettg102 on 2008-02-06
[http://www.cyberciti.biz/faq/linux-ubuntu-skype-download-installation/]("http://www.cyberciti.biz/faq/linux-ubuntu-skype-download-installation/")

^Maybe try that? I'm not sure how you're going about installing skype, because as always, it seems there's hundreds of different ways to do so, but that seems like a good walkthrough...

I too have had dependency nightmares, good luck!

---

### Post by jaytek13 on 2008-02-06
Skype is also available from the medibuntu repository. If you do

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

and then
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

and then
```
sudo apt-get update
```

and then you should be able to do 
```
sudo apt-get install skype
```

---

### Post by seventhc on 2008-02-06
I only used skype a few times long ago, but is it anything like 'ekiga'? If so, thats installed already...*Applications>Internet>Ekiga Softphone.* I don't use it, but i remember with skype I used it for chat and for calls...I'm not sure if ekiga does both or not, but it might be worth looking at.

---

### Post by harley87 on 2008-02-07
Found this link [http://packages.debian.org/sid/libqt4-core](http://packages.debian.org/sid/libqt4-core) and was just wondering whether I could download one of these to obtain the libqt4-core package. If so which one?

---

### Post by seventhc on 2008-02-07
If you are on a regular 32 bit computer use this [http://packages.debian.org/sid/i386/libqt4-core/download](http://packages.debian.org/sid/i386/libqt4-core/download)
or here is a direct link to the deb file
[http://http.us.debian.org/debian/pool/main/q/qt4-x11/libqt4-core_4.3.3-2_i386.deb](http://http.us.debian.org/debian/pool/main/q/qt4-x11/libqt4-core_4.3.3-2_i386.deb)

---

### Post by harley87 on 2008-02-07
Thanks. Downloaded the file and now it is saying that another dependency is not satisfiable to run the installer, libc6 this time.

---

### Post by harley87 on 2008-02-07
Is there anyway I can re-install Windows onto my laptop?

---

### Post by jan quark on 2008-02-07
hello harley 

welcome to ubuntu 
yea partitioning can be a nasty thing, especially without a back-up
so rule nr. 1
do a backup now

the rest can  be fixed , feel free to ask your questions here, this is an amazing place, where people really rush to post answers to your questions

---

### Post by jan quark on 2008-02-07
well you can always make a dual-boot system with vista and ubuntu

the easiest way to do this is to install vista on your pc first, create an additional blank partition for ubuntu and install ubuntu on this free partition using the partition option install on the largest continuous free space (or something like that)

see these guides for creating a dual- boot system
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

---

### Post by harley87 on 2008-02-07
I don't have a Vista software CD and don't want to have the hassle of wasting money buying one, so is there anyway I can restore Vista onto my system?

---

### Post by harley87 on 2008-02-07
If I were to uninstall Ubuntu would it revert back to Vista? Or because I partitioned all the HD does that mean if I uninstall I will have no operating system?

---

### Post by seventhc on 2008-02-07
No, it will be a blank hard drive. Sorry
Why do you want to switch back, everyone here will try to help you as best they can.

---

### Post by harley87 on 2008-02-07
I don't particularly want to switch back. Ideally I want to get VIsta back and partition the HD but I'm not going to be able to do that without forking out lots of money am i?

---

### Post by seventhc on 2008-02-07
I'm not sure what type of computer you have but sometimes they contain a partition for recovery. Of course ubuntu may have wiped it but I would still check.  You never posted the output of the command
```
sudo fdisk -l
```
There may be a recovery partition.
What do you see when you run that command in the terminal?

---

### Post by harley87 on 2008-02-07
The output for that command is:

harley@harley-laptop:~$ sudo fdisk -l
[sudo] password for harley:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x99d00136

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11787    94679046   83  Linux
/dev/sda2           11788       12161     3004155    5  Extended
/dev/sda5           11788       12161     3004123+  82  Linux swap / Solaris

---

### Post by seventhc on 2008-02-07
:( It's gone :(
But I think the more you use Ubuntu you might find that it is much better, it is more stable more secure and more reliable. There are thousands of free software packages available, help is right around the corner. In fact I know of no other community as helpful as this one not to mention the speed that you get replies.

I know it's a big change and Ubuntu might not be for everyone, but it is worth trying. I really love it, you can also have different desktop environments so you're not just stuck with the gnome desktop if it doesn't suit you. KDE is probably more colorful and you might like that better, but there are a lot of differnt ones you can install side by side and choose which you want at the login screen. No seperate partitions needed.

I would give it a try though, even though it is different than windows you can pretty much do whatever you want with it once you know how. Learning is fun and remember you didn't know how to use Windows either the first time you got behind a computer. ;)

---

### Post by harley87 on 2008-02-07
:) thanks for the help. I am more than willing to stick with Ubuntu, I have no real gripes that can't be solved atm. I know that it is much better than what Windows has to offer but would still like to have the option of Windows on my laptop. My own stupid fault really for not partitioning properly but whats done is done i suppose. If I got an XP/Vista installation CD which I could do as I am registered with MSDN academic alliance due to my University course so can obtain that free, would I be able to boot up windows from the state that my system is in right now?

---

### Post by seventhc on 2008-02-07
You would have to create a partition for windows, but thats easy enough. IMO it is best to install windows first then install ubuntu b/c ubuntu will automatically detect windows and create a dual boot menu for you. If you install windows after ubuntu, then you will have to mess around with grub.
But either way you choose, people will be here to help. :)

---

### Post by harley87 on 2008-02-07
:) thank you. I may just have to do it that way then. Is there any walkthrough guides that I could follow when putting Windows back on?

---

