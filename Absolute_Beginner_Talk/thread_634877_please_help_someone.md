---
title: "please help someone"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by rwltrz4 on 2007-12-08
ok i have tried 3 times to install ubuntu and nothing, I did something wron because osx didnt even accept it and greyed it out in osx disc utility wouldnt mount, finally went back into live cd to partition manager and deleted it.so please someone "EASY TO UNDERSTAND" instructions  for a total newbie to linux, i dont understand why linux is so hard to install, there has to be an easier way.

I have an intel imac, I went into my disc utility and simply stretched the parttion table graphic and created 30 gig new prtition for linux, leaving 260 gig for osx, at any time i can stretch this smaller or bigger in osx, new feature in leopard literally took me 2 secs to partition, so I have the space all is ready for a wrld of linux, I have the live cd ready to go.

what do i do when i get into the live cd desktop and then click on the install icon, what is next..this is where i cant figure things out

I love how linux looks, works, is customize friendly, the free programs, but man is everythng gonna be this hard to use ubuntu?

---

### Post by Sef on 2007-12-08
1) Did you [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") the download?

2) Did you burn the cd at 4x or less? (Faster may casue corruption.)

3) Did you burn the download as an iso?

3) Did you check the disk for errors?  (Go down the Live CD menu to check disk or something similar.)

---

### Post by skymera on 2007-12-08
or you can order freee CD's from ShipIt.
i order 3 CD's and also burn one, becuase the one i burn, i always lose >_<

plus i like the free stcikers :)

follow the above and should all work 100%

---

### Post by rwltrz4 on 2007-12-08
the cd is fine, been using it for like 2 weeks.

---

### Post by adam_kimber on 2007-12-08
I am assuming that you are using the Intel (Mac Version) of the Ubuntu live/installation CD

If that is the case then Ubuntu is careful not to disturb existing partitions as if they are moved sometimes the OS installed will not work afterwards. Note that I have never installed OSX nor Vista but I have installed Ubuntu  and Windows in its various forms several times and I can say the latest version of the Ubuntu installer that runs from the live CD is totally awesome and is easier than XP. 

Anyway try this page [FAQ for Intel Macs]("http://ubuntuforums.org/showthread.php?t=493393") and especially these instructions [Mac Installation]("https://help.ubuntu.com/community/MacBook"). Not sure if this is relevant but this is a post about Santa Rosa MacBooks [Walthrough for Santa Rosa MacBooks]("http://ubuntuforums.org/showthread.php?t=633931")

If this fails try searching through the [Mac Intel Users subforum]("http://ubuntuforums.org/forumdisplay.php?f=211") as usually if someone is experiencing a problem someone else has previosuly experienced it.

---

### Post by laidback on 2007-12-08
I'm not at all familiar with imac pcs but on the more usual set up you do exactly as you have descibed; run the live CD and then click install. You should now get a wizard that takes you through the installation process. If this is not happening I think it would be useful to check;-

That Ubuntu runs on your hardware, others in this forum will know far more about that than I do...search for imac
That your live CD isn't faulty. This seems hard to check. If you downloaded it was the m5check_sum correct etc. Does it really work on your pc? have you tried a few apps etc. Has it detected all your hardware correctly, hard drive in particular.

I'm running out of ideas now, but please be assured that Ubuntu is as great as you imagine.

And welcome to the world of Linux/Ubuntu.

---

### Post by rwltrz4 on 2007-12-08
again I dont think it is the cd....  it loads runs fine on live cd my problem is understanding the complex menu, which do you pick for install:

guided? scsi? manual? then what do you select for install, on my osx i have 2 partitions now but when i go to linux install menu there are a few items, then asks about a booter or something,

then it stopped loading after 20 minutes sayin not enough room for /target, exited out went back into osx and saw a partition called linuxswap it was 300 meg or something but was grayed out not mounting basically useless, restarted live cd and then was able to delete it in there, exit out back into osx and it was gone.

what i am looking for simply is the install menu instructions, the cd is fine, and the cd I have is the amd64 version which is what it says on site to download, have been using it for like 2 weeks now just checking things out on the cd, no issues.

---

### Post by rwltrz4 on 2007-12-08
> **laidback said:**
> I'm not at all familiar with imac pcs but on the more usual set up you do exactly as you have descibed; run the live CD and then click install. You should now get a wizard that takes you through the installation process. If this is not happening I think it would be useful to check;-

That Ubuntu runs on your hardware, others in this forum will know far more about that than I do...search for imac
That your live CD isn't faulty. This seems hard to check. If you downloaded it was the m5check_sum correct etc. Does it really work on your pc? have you tried a few apps etc. Has it detected all your hardware correctly, hard drive in particular.

I'm running out of ideas now, but please be assured that Ubuntu is as great as you imagine.

And welcome to the world of Linux/Ubuntu.

yes it works fine on cd have used many apps..gimp,firefox, etc, notices hard drive, files, network, not the cd i am sure of that.

yes it takes your through a wizard but i dont know what to click there is no help button which explains, all i want t o do is install ubuntu on a second partition.

---

### Post by laidback on 2007-12-08
OK, will reply again tomorrow...too late now...rather tired.

---

### Post by thelatinist on 2007-12-08
> **rwltrz4 said:**
> again I dont think it is the cd....  it loads runs fine on live cd my problem is understanding the complex menu, which do you pick for install: guided? scsi? manual? then what do you select for install...

Choose 'manual' on the "Prepare disk space" screen.  Choose the partition you want to install in (make sure it is not your OSX partition!). Or alternately delete the new partition you created in OSX before you try to install and choose the option to install in the largest free space.

Ubuntu/Linux is great, but do be prepared for a bit of a learning curve moving from OSX. This is not a particularly complex menu...

---

### Post by laidback on 2007-12-10
Sorry for delay...

Shortly after you choose install from the Live CD you get asked whether you want to use the entire disc, largest partition or do a manual install. As mentioned above I reckon you need the manual install. Select the area on the disc that you had previously allocated for Ubuntu. Make sure that you create at least a root (/) partition and a swap partition (/swap). That is the minimum, I've been using this set up for some time and find it fine. Once you get more experience you can alter it to a more complicated set of partitions, e.g. add a /home partition. There are plenty of posts on the forum about the pros and cons of various configuratiions, but for now go with something simple. Ubuntu install will probably format these partitions now and then begin the actual install of Ubuntu. 
You're likely to find that it wants to add a Grub boot menu to your system, you get a question about where to put it, cannot remember exactly what it says but it's about whether you want it added to your MBR or ?... I've always chosen the MBR option, not sure what the pros and cons are of this. On a dual boot system you get a menu at boot up (Grub menu) that allows you to select which OS to boot into, Ubuntu or your other one. 

Trust this helps a little.

I use a caddy system which allows me to swap hdds in about 20 secs, so I preserve originals if I'm messing with another OS. I find it very handy and reassuring to know that my working copy of 7.04 isn't being messed up as I try to install 7.10 or Suse or Fedora etc.

---

