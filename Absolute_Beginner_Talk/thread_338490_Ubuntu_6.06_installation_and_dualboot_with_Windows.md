---
title: "Ubuntu 6.06 installation and dualboot with Windows"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by Nemoo on 2007-01-14
Hello ubuntu community!

I have always used Windows as OS, but I've also been thinking of using a Linux OS for some time. When i discovered ubuntu I thought, that it would be a good Linux OS for me, since I'm new. Here are my computer specs, in case you need them to answer the following questions. Tell me if you need more info.

Dell Dimension 9150 Pentium D 915 Dual Core Processor (2.80GHz, 800MHz fs, 2x2MB cache)
1024MB Dual Channel DDR2 533MHz (2x512) Memory
250GB 7200rpm SATA Hard Drive
256MB Nvidia GeForce 7300LE TurboCache graphics card
Windows XP SP2 Home

I think that this ubuntu i right for me:

ubuntu-6.06.1-desktop-i386.iso
Desktop CD of ubuntu 6.06.1 LTS

I have downloaded InfraRecorder, so I can burn ubuntu to a CD. I have also downloaded winMD5Sum, so I can verify the ISO's hash. I haven't downloaded ubuntu yet, because I would like to know if I do things right. My Plan is to download the above version of ubuntu, verify the hash with winMD5Sum, and then burn it to a CD with InfraRecorder, as explained [here]("https://help.ubuntu.com/community/HowToMD5SUM") and [here]("https://help.ubuntu.com/community/BurningIsoHowto"). After I have burned the CD, I would let the CD be in the drive and then restart the computer. Then it should start to install ubuntu. If it doesn't would restart the computer, and press F12, so I could choose to start the computer from the CD, and then I could begin the installation. 

Please tell me if I'm right about all this.

To installation I was thinking of using [this tutorial]("http://www.psychocats.net/ubuntu/installing"). I would first only use Live CD version, until I find out if it is something for me. When I get to the "Prepare Disk Space", as shown in the tutorial, I would choose the first option. Then I don't have to do all that mount thing, right? After I have completed the installation I shall take out the CD and restart the computer. Then the computer will start and I can choose whether I want to start Windows or ubuntu. 

Again, please tell me if I'm right or wrong.

If anything goes wrong, it will not affect Windows. If I (for some reason) decide not to use ubuntu, I can uninstall it, and everything will be as before.

Am I right or wrong about this?


Thank you in advance!
I hope you can help me, with getting a good start on using Linux and ubuntu.

---

### Post by housam on 2007-01-14
You've choosed the right version of ubuntu ( Dapper 6.06.1 LTS is the most stable release of ubuntu).
You can also order a live CD from shipit in the ubuntu site its free.

I prefer to manage the partitioning manually to put every thing under control. You have to keep windows in a separate partition and create another 3 partitions for ubuntu.
Using the the partitioning tool Gparted ( you can download it or use the version on the CD) you can create the following partitions as an examples:
- 10 - 15G ext3 ( / ) for root
- 1G swap ( useless if more than 1G , you may not use it ever if you have 1G RAM or  more.)
- 10-15 Gb is ext3 for /home
After creating the partitions you can follow the tutorial for installation. 

Good luck

---

### Post by Nemoo on 2007-01-14
In the tutorial it says:

*This first option is ideal for users who want to set up a dual-boot (where you can choose whether you want to use Windows or Ubuntu each time you boot up your computer) but know very little about setting one up*

I think that sounded like something for me, because i want dual-boot, and I don't know how to setup partition. 

And if anyone could confirm all the other things, I've been asking for, it would be nice.

---

### Post by mikewhatever on 2007-01-14
I suggest to take some time and read the following guide: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) It is a lot more then a dual boot tutorial. 

The installation of another OS if not always a simply thing. There is no guarantee, that things won't get wrong. If they do, there is a chance you may loose some or all of your data. The best strategy is to backup anything important, and have MBR fixing disk (CD or floppy) ready.

Good luck. :-D

---

### Post by Nemoo on 2007-01-14
When I went to the website you linked to, it said it was a guide for the Alternate version. I'm looking for something about the Desktop version. The Alternate version sounds more advanced to me.

I guess I have to live with that things can go wrong, when I install a new OS, but if everyhing works as its suppose to am I then doing things right?

---

### Post by housam on 2007-01-15
Doing the partitioning manually will not affect your intention of having a dual boot. it is something to just control your partitions. In both cases you'll have a dual boot as long as you keep windows in a separate partition. Do a backup in a DVD or CD's to restore if something went wrong. In most cases the installation went perfect without any problems.
You just have to read a little about it .

---

### Post by allix on 2007-01-15
> **Nemoo said:**
> When I went to the website you linked to, it said it was a guide for the Alternate version. I'm looking for something about the Desktop version. The Alternate version sounds more advanced to me.


Here is a guide for the desktop version.
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by Nemoo on 2007-01-15
Thanks for the link allix. It helped, because i thought I had to install, no matter what. But apparently, you can just run it from the CD.

---

### Post by xpod on 2007-01-15
Another great site to help with the basics

[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

Anyhting you dont understand is only a question away on here
Good luck nemoo

EDIT:yup.....make sure you try everything from the live cd for a while first....just to be sure it`s for you!

---

### Post by sailor2001 on 2007-01-15
if you decide to dual boot. defrag your windows first. You have plenty ram so you shouldn't have any trouble...desktop install is quite easy if you have burnt your iso at a slow speed (x-4) and not as a data file...automatic install will set-up your partitions and you do have a choice on size and will also install your grub, swap partition.  By default, ubuntu will boot first unless you change that later.....

---

### Post by Nemoo on 2007-01-15
How do I defrag Windows, and what does it do?

Is it hard or easy to setup dualboot?

---

### Post by mikewhatever on 2007-01-15
To defragment in Windows go to Start->Accessories->System Utilities and look for defragmenter. It will consolidate your files and make it easier to resize Windows partition when installing Ubuntu. 
Setting up dual boot is neither hard nor easy. It's kind of scary untill after you are done. The bright side is, you have very good guides to help.

---

### Post by ubromtoo on 2007-01-15
This is my first post, hoping someone can help me.

  A few days ago I installed the 6.06 desktop version from a disk, and the installation

looked like it had gone well: when I removed the disc and booted up Ubuntu, it was 

fine, as far as a brand new user such as I could tell after a brief look-around.

   However, when I tried to boot up Windows, a screen came up that said 

  "file read error" or similar words. I tried several times, then tried to do a default 

system restore, but got the same "file reading error" screen.

   It was necessary to use the System Restore discs and do a Destructive restore,

which wiped the whole hard disc clean.      Any ideas?  thank you .

---

### Post by ubromtoo on 2007-01-21
well, looks like I killed this thread stone dead......but  GOOD NEWS !!!!!!!!!!!!!!!!!!!!

  once again I installed Ubuntu, using the same disc as before, thinking that perhaps

  a friend could give me some help this time, but for some reason , this time it all 

worked O.K., and the dual-boot situation is just fine !!??!! 

        This seems peculiar to me, but then again, all's well that ends well !!

next, I'll be using this forum to find help in getting my e-mail going....but that's 

another thread :)     :D

---

### Post by ubromtoo on 2007-01-24
My second post has one serious omission: after the dual-boot was achieved, I

  then booted up Ubuntu and was prompted to download lots of updates- in fact,

  91 updates altogether.

       That must explain why Windows is now easy to boot up, and why the 

   dual-boot installation is now working just fine.  :confused:  :)    :guitar:

---

