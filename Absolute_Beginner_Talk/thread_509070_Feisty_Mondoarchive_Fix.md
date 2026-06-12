---
title: "Feisty Mondoarchive Fix?"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by ityro on 2007-07-25
Hello,

Is anyone aware of rumors that the Feisty/Mondoarchive problem will be resolved prior to the release of Gutsy?

Thanks for your time.

---

### Post by whitefort on 2007-07-25
I haven't heard the rumour, but would be delighted if it were true.

Personally I haven't been able to get Mondo to work since I switched from Dapper. and this has severely limited my use of Ubuntu - I had to switch my main machine from Feisty back to Dapper so I could get my updates going again.

From posts in the Mondo mailing list, I know that the Mondo developer has created 'unofficial' Ubuntu versions (which I also couldn't get to work)), and that he has stated several times that he would welcome input from Ubuntu developers to get things working again.

Mondo has saved my skin so often in the past that I won't use any system that's incompatible with it.

---

### Post by ityro on 2007-07-29
Hello Whitefort,

Just a note to let you know you are not being ignored. Right after I posted my question I decided to create a new partition to use with PartImage which I have never gotten to work. I used GParted (not properly I suspect) and was rewarded with a message "Grub loading stage1.5 Error 17" on my restsrt.

To make a long story short I wasted both XP and Ununtu. While trying to restore both systems I have been palgued with frequent power outages and then even got sick for a day.

Just taking a break to thank you for your response. I know from the Forums you are also a Mondo fan and I will now take your advice and wait for Mondo to return.



Dual-boot XP/Ubuntu 7.04 on a HP/Compaq nx9010 notebook 
w/40GB HDD and Iomega 80GB usb HDD. ATI Display: PCI Bridge 
[GP 340M] Radeon IGP 330M/340M/350M RS200/RS200M AGP Bridge 
[IGP 340M].

---

### Post by paker on 2007-08-02
Last night I used mondo to make an archive dvd and a boot cd. Do you mean they are not going to save me when my computer crashes? I am also using Feisty.

How do I verify whether or not they are going to work? Thanks.

---

### Post by whitefort on 2007-08-02
Hi, Paker.

Maybe you'll be luckier than the rest of us - if you are, I'd love to hear about it.

But yes, you can test your backup disk.  You just need to boot from it.
(If it won't boot, it didn't work).

When it boots, you'll get a few options - either a screen of text, or a graphic interface.

If it's a screen of text, you just need to type 'compare' and hit enter.  If it's the graphic interface, select the compare button.

In either case, it will start trying to compare the files on your machine against the ones on the backup disk.  There won't be a 100% match, ever.  Temp files and stuff change too often, and aren't important to the backup.  You may also have changed some files yourself since making the backup...  anyway, at the end of the process, you 'll get a list of non-matching files.  If there aren't too many, and they're all temp stuff, then the backup probably worked.

At present, people seem to have a wide variety of Mondo errors with Feisty - for some it won't boot, etc.  In my case, it does t the backup perfectly, but when I try to compare, it won't recognise my hard drive and therefore claims to find no matching files at all.

Good luck - but I have to say that if mondo works for you, you'll be almost unique among feisty users!
(and I'll be really envious)

---

### Post by ityro on 2007-08-02
Paker,

Whitefort  already answered your question and if you read between the lines you want to run the "compare" right after the backup to keep confusing messages to a minimum. 

 Also Whiteford is correct in waiting for Mondo/Feisty problem to be resolved.

Best of luck.

---

### Post by paker on 2007-08-02
I am glad I ran compare. Results are astounding. 94761 files didn't match the backup. 87785 significant differences were found. I freshly installed Feistry, Automatix, all codecs, updates only  2 days ago. Thanks.

I will have to give up on mondo and try partimage. If you have working knowledge, please help me.

---

### Post by ityro on 2007-08-02
paker,

If you ran MondoArchive before the Freshinstall and ran the "compare" option after the Freshinstall
I would think the results are normal.

Do another MondoArchive and run the "compare" option immediately after.

I can't help you with Partimage. My attempts to run Partimage have failed.

Lotsa Luck.

---

### Post by paker on 2007-08-02
I liked the menu driven Mondo Rescue much and did second attempt. I removed mondo/mindi (the 3 packages) using synaptic, and downloaded the same 3 deb files (of the most recent version)  from MondoRescue.org and installed them using "sudo dpkg -i *.deb" as in the other thread. Ran mondoarchive and made boot cd and dvd #1.

Rebooted from the cd and compared from dvd #1. 56 files didn't match backup, and 19 significant differences as follows:

home/rust/.bash_history
home/rust/.gconfd/saved_state
home/rust/.gconf/apps/nautilus/%gconf.xml
home/rust/.gconf/apps/nautilus/preferences/%gconf.xml
lib/modules/2.6.20-16-generic/volatile/nvidia_new.ko
lib/modules/2.6.20-16-generic/volatile/fcdslusba.ko
lib/modules/2.6.20-16-generic/volatile/fcpci.ko
lib/modules/2.6.20-16-generic/volatile/fcusb.ko
lib/modules/2.6.20-16-generic/volatile/fgkrx.ko
lib/modules/2.6.20-16-generic/volatile/fxusb.ko
lib/modules/2.6.20-16-generic/volatile/nvidia.ko
lib/modules/2.6.20-16-generic/volatile/nvidia_legacy.ko
lib/modules/2.6.20-16-generic/volatile/ath_hal.ko
lib/modules/2.6.20-16-generic/volatile/fcdsl.ko
lib/modules/2.6.20-16-generic/volatile/fcdsl2.ko
lib/modules/2.6.20-16-generic/volatile/fcdslsl.ko
lib/modules/2.6.20-16-generic/volatile/fcdslslusb.ko
lib/modules/2.6.20-16-generic/volatile/fcdslusb.ko
lib/modules/2.6.20-16-generic/volatile/fcdslusb2.ko


What are the significances of these files? Do I have a chance to restore from the boot CD and archive DVD? Thanks.


PS: To answer your question, 94761 different files were the outcome of "sudo mondoarchive" 2 days after fresh install of Feisty. There shouldn't be that many differences.

---

### Post by ityro on 2007-08-02
Paker,

I am certainly not an expert witn a total of 8 months using Linux but I would not rely on it.  Maybe someone else will disagree and provide a workaround?

---

### Post by paker on 2007-08-03
This is a reply I got from a member of this forum.

> **dannyboy79 said:**
> you would be able to successfully restore your system even if the program is reporting these as different. The first ones in your home directory are only a bash history (like a log file) and some preference type stuff. THen all the rest are the modules that get loaded to volatile when you boot up your system. You'll be fine!

Based on this statement, we can say that the deb files in MondoRescue.org work in Feisty.

---

### Post by click4851 on 2007-08-03
fruitfull searching....I just installed Mondo/mindi on my desktop, tested mindi last night and I do get a bootable CD, now for the Mondo portion, I may try to back up just my /home partion first just to see if thats successful.

---

### Post by ityro on 2007-08-03
Dannyboy79 and paker,

Thank you for the vote of confidence for Mondo and thank you for telling me.

---

### Post by paker on 2007-08-04
I tried "nuke" and "restore". It didn't work. "Compare" was okay, but there was a problem with partitioning and formatting hard disk during restoration process. I am giving up on MondoRescue.

---

### Post by ityro on 2007-08-04
paker,

Sorry you had so much trouble but don't give up, just wait. The problem will be corrected.

---

