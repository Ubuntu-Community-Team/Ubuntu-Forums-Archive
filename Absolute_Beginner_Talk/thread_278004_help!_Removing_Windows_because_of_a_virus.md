---
title: "help! Removing Windows because of a virus"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by lee101 on 2006-10-15
do any of u bright sparks here no how to remove windows via ubuntu, i have a virus on windows, when i select windows from the grub menu windows restarts my computer straight away. does anyone no if this is possible? 

please help

---

### Post by taurus on 2006-10-15
You can format your Windows partition in Ubuntu and remove the entry for Windows from /boot/grub/menu.lst!  Is that what you are looking for?

---

### Post by NeoLithium on 2006-10-15
You may want to wait for a couple of other suggestions; but from what I can gather (I've never had the problem myself) is that you can run the live CD for ubuntu; and use GParted to remove the windows partition; getting rid of the Virus (Windows - Sorry, just had to) and the problem it was having.

---

### Post by lee101 on 2006-10-15
ye taurus i suppose if i reformat the windows partition that will help,

but now the question is how do i do that?

thanks 4 the commment

---

### Post by taurus on 2006-10-15
What partition is your Windows on and do you want to format it and use it with Ubuntu as a storage--ext3?

---

### Post by ReaderRat on 2006-10-15
> **lee101 said:**
> do any of u bright sparks here no how to remove windows via ubuntu, i have a virus on windows, when i select windows from the grub menu windows restarts my computer straight away. does anyone no if this is possible?
What, exactly do you want to do? 1) Run **only** Ubuntu(:-D ), 2) **Dual-boot** Ubuntu & Windoze(:twisted: ),

---

### Post by lee101 on 2006-10-15
taurus its hda2

---

### Post by lee101 on 2006-10-15
readerrat yes i want to run windows and ubuntu

---

### Post by taurus on 2006-10-15
> **lee101 said:**
> readerrat yes i want to run windows and ubuntu

If you want to reinstall Windows on that partition, /dev/hda2, again, then just insert Windows XP CD into the drive and boot from it.  Make sure you point it to /dev/hda2 and it will format it as NTFS for you.  No need to remove and format the partition first before you reinstall Windows XP!

---

### Post by Melodie on 2006-10-15
To format anything, please consider using Gparted as a live CD. The advantage is first, your partitions will be umounted, which is more secure. Second, the actual live CD version is very, very good. Do visit the site and [take a look at the screenshots]("http://gparted.sourceforge.net/livecd.php"), it should not seem too difficult for you to use it. (In your case, format will start with deleting the partition, then you can apply any format to your convenience).

Else, if you'd like to try recover your Windows partition, I'm not an expert, so you might consider what's following as something to try at no risk :
Do mount your windows partition in a folder under /mnt, then go [to this website]("http://www.virustotal.com/en/indexf.html") and have a scan on the Windows partition folders.
Then, see if something's detected, and if possible to know where in the system.

Else and last, do configure a firewall on your systems (on Linux too, as Windows viruses can't harm, but trojans and spyware can).
:-|

---

### Post by lee101 on 2006-10-15
thanks to all who posted big help much appreciated:)

---

### Post by anaconda on 2006-10-15
isn't there any files that you want to save in from your windows partition?

You can do that quite safely from ubuntu.. windows viruses dont affect ubuntu in any way..
or you could just install antivirus to ubuntu, and scan your windows partition from ubuntu.. First you would need to eneble ntfs read/write support so that you would be able to make changes to your windows partition..

---

### Post by ReaderRat on 2006-10-15
These may help:
ReInstalling Windows & Recovering Ubuntu
          [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

EDIT: In any case, if you reinstall both Windoze and Ubuntu, Install Windoze first.

---

### Post by Neobuntu on 2006-10-15
For me. My goal and order would be as follows:

Scan the Win partition while in Kubuntu. Verify no mal-ware (that can be seen!). 

Retrieve the small amount of data that you can't live without; on to a flash drive.

Unless you're invested in lock-in Windows apps that you do not have CD's or time to reinstall (NOT a problem with Kubuntu), Make sure you have a SCANNED firewall app available before going back online, and for the Windows version you wish to install/dual boot.

Do a clean install (DO NOT BUY NEWER WINDOWS OS CRAP FOR THIS PLEASE. IT'S a SCAM.) and this way, is the ONLY way (for sure) to know you started clean. 

You would only need Windows for comparison purposes and highly speciaized OLD programs. Any effort needed to switch (usually minimal) to an open program alternative reaps great rewards, forever. Even if something like Quicken is hard to get away from with it's NON-standard, ever changing (lock-in) data files, you will be glad you moved. Some even run Quicken with WINE in (k)ubuntu but it's a technical and stop gap measure. It works good enough and like it's native. Check version compatibility first.

Then you could also do a upgrade or fresh install of Kubuntu (or what ever you prefer.) It's less hassle to keep Windows first on your drive, with a dual boot.   

The bottom line is, one saves massive time, when they don't have Windows at all, but I like to compare it on exact same hardware and see it in all it's unsecure glory.

You see, one is best served with kubuntu. It saves time but a new user may forget what time wasting problems Windows has. So one only observes this AFTER using both a while. A new user just can't have experience before the actual experience. They may come away, working around a device problem while using Kubuntu and conclude that Windows 98 had no such actual or remembered trial. People expect perfection but don't seem to apply the same standard to Windows. Only experience, shows Kubuntu is far CLOSEST (overall) to perfection and no complex massive system is perfect. Dual boot and newbie thus go together. 

I think a new Kubuntu user will be happier, at first, with the ability and no-risk "dual boot" install. If a device doesn't work on either system, you know it may not be software at all. 

Dual boot may seem like a waste of time but it's really just a few seconds to boot and a lot of simplicity. Run native apps in their native OS and do it with full device support. You may find, you don't need to boot Windows much anyway. With todays hard drive space costs. Why not? KISS. Unless you are in development or look for server sharing, simplify your life.

P.S. No matter how many old computers I get to install open software on, I always want to see Kubuntu and XP pro , compared on THE BEST AND FASTEST ONE. Have you ever installed XP? What a time killer! If you're concerned about time AFTER a free CD live Kubuntu run and then AFTER an EASY dual boot install, then go only Kubuntu; if you want your time back.

---

### Post by JayTee on 2006-10-15
> **taurus said:**
> If you want to reinstall Windows on that partition, /dev/hda2, again, then just insert Windows XP CD into the drive and boot from it.  Make sure you point it to /dev/hda2 and it will format it as NTFS for you.  No need to remove and format the partition first before you reinstall Windows XP!
Actually, if his Windows system is infected (don't they come shrink wrapped that way? Just kidding!) and he can't remove the virus any other way it might be better if he does delete the original partition and then create a new one and install fresh. Installing over the original Windows install won't guarantee the virus is killed in the process but in the case of 98% of the viruses out there repartitioning will.

---

### Post by Neobuntu on 2006-10-15
Hey, love the Firefly class Serenity BTW. "We aim to MISSBEHAVE!"

Yes you are correct. If done poorly, a "clean" install will have to be done over again. 

If you check for root kits, wipe the MBR and reformat the partition and/or let the verified installer CD FORMAT the partition, chances are slim, that you will retain a virus. It would have to come from saved, corrupted and reinstalled files (another reason to just go with free open source Kubuntu.).

Bottom line is, be careful. If you do not format the drive, you probably would retain mal-ware. I've seen it, trying to aviod a clean install. You can't. Not and be sure.

This is why I say pre-installed is not the great divider people suggest. Preaching to the choir; as I may be, Windows "pre-installed" is a joke and the Kubuntu installer CD is far easier than install (or reinstalling) Windows. Saves time too, by FAR! 

So what we need is a good device approved system bundle, at a lower cost and made ready to take a Kubuntu CD. 20 minutes later and your're done. It sure is better than beating back all the crap that comes on a Windows pre-installed system.

It'a a better world!

---

