---
title: "Ubuntu / Windows XP Dual boot"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by Comike14 on 2007-06-01
Super newb here, but I heard Ubuntu has one of the best online communities.  :popcorn:

So here's the deal.  I installed Ubuntu last week, and I really love it.  I can't get over how plug & play it seems to be with all my hardware (except for my x1800xt ATI, but I got that junk all figured out), and how smoothly it runs.  But I paid good money for XP Pro about a year ago, plus my girlfriend is used to the Windows setup.  I know I can probably customize everything in Ubuntu to practically mirror how things look and feel in XP, but I don't want to take that route--I prefer to have plenty of things different.

Thusly, I want to set up a dual boot.  I had installed a version of Suse back in college which had a nifty little partitioner on the disc, which made dual-boot with Windows a breeze.  But Ubuntu, as awesome as it is so far, doesn't seem to have this functionality.  So, here's what I've got:

1. Ubuntu OS disc
2. Windows XP Pro disc
3. Windows 98 disc with *fdisk*

And here's my plan:

1. Wipe current Ubtunu install away and set up primary DOS partition, 50/50
2. Install Ubuntu in one partition.
3. Install Windows in the other partition.

So I guess my question is this:  When/if I get these two OS's installed, will I have a choice as to which one to boot into?  Does anyone have suggestions on a different partitioning program, other than fdisk, which will give me some kind of menu option?  Has anyone possibly actually done a dual boot like this before and, if so, how do you like it?

Thanks mucho.

---

### Post by drowner on 2007-06-01
You are entirely wrong about ubuntu not having that functionality. It does. It will happily partition your drive.

I assume you don't wish to install BOTH windows versions? One is more than enough, generally ;)

Load windows first, then install ubuntu.

You will indeed get to choose which OS you can use.

[http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)

Is good to read first

[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone) <- if you have the 'alternate' cd

[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing) <-- if you have the LiveCD.

---

### Post by Sparkster185 on 2007-06-01
If you're already planning on wiping off Ubuntu completely, it will be quite simple.

First, install XP and let it re-format your entire HD.

Second, install Ubuntu, but make sure you manually edit the partition table during the install.  You will need to re-size your NTFS partition (the XP one) to make room for your Linux ones.

Once that's done, create your / , swap, and /home partitions.

When you install Ubuntu, it will automatically install a bootloader (GRUB) that will prompt you at boot time to pick which OS you want to use.

---

### Post by uputer on 2007-06-01
> **Comike14 said:**
> 

And here's my plan:

1. Wipe current Ubtunu install away and set up primary DOS partition, 50/50
2. Install Ubuntu in one partition.
3. Install Windows in the other partition.

So I guess my question is this:  When/if I get these two OS's installed, will I have a choice as to which one to boot into?  Does anyone have suggestions on a different partitioning program, other than fdisk, which will give me some kind of menu option?  Has anyone possibly actually done a dual boot like this before and, if so, how do you like it?

Thanks mucho.
Try this page:

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

I am curious what other Ubuntu users think of it.   It looks really good and useful to me.   I had it recommended to me so I am passing it along.

---

### Post by Comike14 on 2007-06-01
Excellent!  Thanks for the advice.  I'll work on this through the weekend and post the results.  So, from the input here, I'll:

1. Wipe Ubuntu clean by deleting all partitions.
2. Install Windows normally, allowing it to format the whole drive NTFS.
3. Install Ubuntu and manually create partitions when prompted.

I'll also check out that tutorial, uputer.  Thanks again!

---

### Post by ConsummateK on 2007-06-01
If you're looking to start from scratch I would recommend these steps:

1. Get DBAN, it's a low level reformat utility that will give you a completely fresh drive. 
2. Install windows using the entire drive as one big partition
3. Defrag
4. Boot to the LiveCD of your choice and use the automatic partition resizer to take Windows down to whatever you want, let Ubuntu do the rest.

EDIT: Looks like i'm a little late. :p If you do have any problems deleting the partitions refer to the DBAN tool above. Good luck. :)

---

### Post by Sparkster185 on 2007-06-01
You really shouldn't have problems with it.  On my first Ubuntu install, I was able to successfully re-size my NTFS partition and install Ubuntu with ease.

Just a recommendation, I would create three linux partitions.  One for / (I allocated 20-30GB, which seems like overkill now that I've been using it for months and have only used 5-6GB), one for swap (I make mine 1G) and the rest for /home.

By creating /home a separate partition, you can re-install your OS without touching your user data.  All of your documents, music, pictures and even application settings will be preserved if you have to re-install.

Good luck and enjoy,

-Sparkster

---

### Post by Comike14 on 2007-06-01
> **ConsummateK said:**
> If you're looking to start from scratch I would recommend these steps:

1. Get DBAN, it's a low level reformat utility that will give you a completely fresh drive. 
2. Install windows using the entire drive as one big partition
3. Defrag
4. Boot to the LiveCD of your choice and use the automatic partition resizer to take Windows down to whatever you want, let Ubuntu do the rest.

EDIT: Looks like i'm a little late. :p If you do have any problems deleting the partitions refer to the DBAN tool above. Good luck. :)

Actually I may do this from the start.  I have fdisk on the Windows 98 CD (the only reason I *have* a Windows 98 CD), but all it really does is delete partitions--doesn't give me a fresh drive.  I take it DBAN is a free utility I can just burn before I get started.  Thanks!

---

### Post by DrMega on 2007-06-01
> **Comike14 said:**
> Excellent!  Thanks for the advice.  I'll work on this through the weekend and post the results.  So, from the input here, I'll:

1. Wipe Ubuntu clean by deleting all partitions.
2. Install Windows normally, allowing it to format the whole drive NTFS.
3. Install Ubuntu and manually create partitions when prompted.

I'll also check out that tutorial, uputer.  Thanks again!

If you install Windows first, then boot Ubuntu from the Live CD and choose to install, then it will suggest a partition size and it is as simple as sliding a slider to share the disk space out as you want it.

You said you were going for 50/50. One thing to keep in mind is that it is easier for Ubuntu to read a Windows partition than it is to get Windows to read a Linux partition, which maybe the reason that the installer by default recommends about 25% of you disk to go to Linux.

---

### Post by northicert on 2007-06-01
comike14,
     Was Win XP on your compute first and now you can't use it after the Feisty install?

---

### Post by ConsummateK on 2007-06-01
> **Comike14 said:**
> Actually I may do this from the start.  I have fdisk on the Windows 98 CD (the only reason I *have* a Windows 98 CD), but all it really does is delete partitions--doesn't give me a fresh drive.  I take it DBAN is a free utility I can just burn before I get started.  Thanks!

Yes indeed. You can nab it right here --->  [http://dban.sourceforge.net/](http://dban.sourceforge.net/)

Fair warning, I have a 250GB drive and this utility takes about 5 hours to run. It's a little slow but extremely thorough.

---

### Post by hank hill on 2007-06-01
I had alot of problems with ubuntu live cd installer .When it was thru ,i could not boot to windows.I used the alternate ubuntu cd for the textbase installer.
If you have a winxp pro install cd  you can do it this way ,it worked like a charm for me ,just watch this 14 minute video.

[http://video.google.com/videoplay?docid=-6104490811311898236]("http://video.google.com/videoplay?docid=-6104490811311898236")

you might have to view it using xp, as i'm using ubuntu amd64 &haven't got flash to work yet.It doesn't play for me on ubuntu  ,yet! 
Ihope this helps ,i think it is a really easy way for us newbs to get win /ubuntu dual boot working ,but it only works for a fresh install....

---

### Post by uputer on 2007-06-01
> **Comike14 said:**
> Excellent!  Thanks for the advice.  I'll work on this through the weekend and post the results.  So, from the input here, I'll:

1. Wipe Ubuntu clean by deleting all partitions.
2. Install Windows normally, allowing it to format the whole drive NTFS.
3. Install Ubuntu and manually create partitions when prompted.

I'll also check out that tutorial, uputer.  Thanks again!
No problem!   The good thing about that utility is you don't have to start over if you didn't want to.   But, if you are starting from scratch anyway, it is ideal as you can learn how to use it and if you make a mistake, it won't matter yet.   You don't have to tread carefully so it's a perfect situation for learning.   I receive help when doing major partition work so I'm in the same boat.   

I will use this method and I also recommend the GAG boot manager.   I already use it on my current computer.    It's not pretty but it does the job and works well. 

[http://gag.sourceforge.net/](http://gag.sourceforge.net/)

It's a good combination, imho.

---

### Post by Comike14 on 2007-06-01
> **northicert said:**
> comike14,
     Was Win XP on your compute first and now you can't use it after the Feisty install?

No, I actually deleted the partitions before I tried installing Ubuntu, so I was basically starting from a clean system.  I got the Ubuntu CD burned from a friend before I checked these forums, so when I googled "Ubuntu Windows dual boot" I got a lot of older information telling me it was pretty hard to do.  :)

---

### Post by northicert on 2007-06-01
Ok..  I'd like to install Feisty but I don't want my MBR messed up.

---

### Post by ElEdwards on 2007-06-01
I just completed setting up my laptop to dual boot and it was really quite simple.  Windows was the most time-consuming portion of the process.  I really needed to reinstall Windows anyway, so.....

1- backed up my docs, etc. to a cd.
2- I used my Windows XP Home installation cd to delete all partitions from my drive (40-gig) and then create a 20-gig partition for Windows
3- Spent EONS installing Windows XP, going to Windows Update, downloading service updates, rebooting, going back, getting more updates, rebooting, going back..... well, you get my drift.....
4- Installed the Windows apps I need.
This took about 4 hours....

THEN.....

5- booted my Ubuntu 7.04 cd and clicked Install on the desktop.
6- let it select the unused 20-gigs on my hard drive, which it formatted without any barking.
7- Ubuntu found every bit of hardware on my laptop, including my Linksys wireless card, the built-in sound card and built-in modem.  (This is the first Linux distro that has really worked for me!)
8- I rebooted, GRUB displayed the menu selection, I let Ubuntu start up again and then downloaded & installed the 44 updates it found.
....and in less than an hour (compared to the 4 hours for Windows), everything was done!  It was a total breeze! :)

I can boot to either Ubuntu or Windows without any problems whatsoever.... and I can readily look at and edit the files on my Windows partition from Ubuntu, as well.

If I hadn't really needed those Windows apps, Ubuntu would have had my entire 40-gig hard drive to live on ;)

---

### Post by Tautoa on 2007-06-01
> **Comike14 said:**
> Has anyone possibly actually done a dual boot like this before and, if so, how do you like it?

I have a setup that sounds similar to what you're trying to achieve. It's working out great for me :)
I used the XP install disc to wipe all of the partitions from my 3 hard drives, and then made a 15GB NTFS partition on the master hard drive (its better to install XP on the first partition of the master hard drive, it doesnt seem to like being elsewhere).
After the XP install was finished, I booted the Ubuntu LiveCD, and used the partitioner to make a 15GB Ext3 partition for Ubuntu (mounted at /),  a 60GB Ext3 partition for my files (mounted at /home), a 1GB swap partition on the second hard drive, and a 20GB Ext3 partition for Windows Program Files.
There are a couple more partitions, but they're probably not relevant to anyone but me :)
By installing Ubuntu after XP, you end up with GRUB on the MBR, which should recognise your Windows partition automatically.

I've also integrated Ubuntu and XP in other ways, which you (or anyone else who is dual-booting) might be interested in. For example, I made a separate Program Files partition formatted with Ext3 so that I can use Wine to run Windows programs easily, if I need to do something, but don't want to reboot into Windows. Also, my Ubuntu and Windows desktop are one and the same... i.e. if i put a file on my Desktop in Ubuntu, and reboot into Windows, the file will be on my Windows desktop.

I'm intending to write a more detailed explanation of it all on my blog (see my sig), rather than post it all here, because it gets kinda complicated (registry editing and stuff). If you're interested in integrating XP and Ubuntu as much as possible, check my blog around mid-June (I've got exams until then - not much time for blogging). Good luck! :D

---

### Post by Comike14 on 2007-06-01
Tautoa, that actually sounds awesome--especially the bit about having integrated desktops...  I may need to look into that.  :)

---

### Post by Comike14 on 2007-06-03
Just a follow-up, here's what I ended up doing:

1. Downloaded and used DBAN.
2. Installed Windows XP.
3. Installed Feisty.
4. Installed GAG Graphical Boot program.

Something went strange with the GAG--it ended up unable to find the boot sector of the Feisty, so I uninstalled GAG and decided to use the boot chooser inherent on my BIOS.  Upon reboot, it automatically booted XP and I had no choice.  I think what happened was GAG installed itself over the boot sector that Linux used.  So, all I did was reformat again, reinstalled XP, reinstalled Feisty, and didn't put GAG on again.  Works perfectly.

Thanks everyone, all the input was very helpful.  Even the GAG was awesome--I just need to manually have it use something other than the first disc sector.  :D

---

### Post by oilchangeguy on 2007-06-03
you're making this a LOT harder than it has to be. simply install xp, install ubuntu and allow it to use the largest available free space. volia, you've got a dual boot machine.
and read this:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Comike14 on 2007-06-03
Thanks oil, that's actually pretty much what I ended up doing.  :)

---

