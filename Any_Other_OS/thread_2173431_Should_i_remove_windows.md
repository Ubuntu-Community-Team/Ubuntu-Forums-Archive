---
title: "Should i remove windows?"
date: 2013-09-09
forum: Any Other OS
---

### Post by josh17 on 2013-09-09
I have ubuntu 12.04 right now and i love it, i havent used windows since i got it and its kinda just taking up space on my harddrive. However i kinda want to keep it on incase something happens to my ubuntu. What do you guys think i should do?

---

### Post by David D. on 2013-09-09
If you don't need the space taken up by Windows right now, I would keep it for a while.  I dual booted for a number of years.

You can always remove Windows and recover the space for Ubuntu at any time you actually need the space.

---

### Post by josh17 on 2013-09-09
> **David D. said:**
> If you don't need the space taken up by Windows right now, I would keep it for a while.  I dual booted for a number of years.

You can always remove Windows and recover the space for Ubuntu at any time you actually need the space.


Thats actually the reason im asking, i DO need to space taken up by windows. but if something messes up in ubuntu i wont know how to fix it...although i suppose i could put ubuntu on a flashdrive then reset it if i need to..

---

### Post by sammiev on 2013-09-09
You paid for Windows so you might as well keep it. Never know, one day you may just need it. :)
sammiev

---

### Post by josh17 on 2013-09-09
it came with the computer but i dont use it...

---

### Post by monkeybrain20122 on 2013-09-09
Get rid of it. Why do you keep it as it takes up space and you are not using it anyway? Crapware comes with the computer too and most people don't have an issue removing them. Windows is crapware. :)
In case you need to use it for one or two things I would set up a VM.

---

### Post by Habitual on 2013-09-09
Toss a coin.

---

### Post by RavenLX on 2013-09-09
Set it up in a VM as monkeybrain20122 suggested and then get yourself an Ubuntu Live CD and/or "System Rescue CD" from [http://www.sysresccd.org/SystemRescueCd_Homepage](http://www.sysresccd.org/SystemRescueCd_Homepage) . Then when you have all that done and can boot using the Rescue CD (try it first and be sure you can still access your files). Then remove Windows. This way you have what you need in case Ubuntu locks you out. 

Also try to use a partition manager to move your /home to it's own partition. This way if your Ubuntu goes bad, you can always reinstall and not affect your data. And be sure to make periodic and frequent backups of your data just in case.

Maybe if you're adventurous, after making the restore CD, backup all your data and then wipe your drive completely and install Ubuntu fresh but be sure to make /home on a separate partition. Then you'll be all set.

---

### Post by coldraven on 2013-09-10
Make a Windows restore disc before you remove it. You'll have to search for how to do it because I cannot remember how.
Later when you have removed Windows you could create a virtual Windows machine running under Ubuntu.
It is a handy resource, I run a 3D modelling program called Sketchup in a XP virtual machine. I don't think that it would run using Wine.
Also useful if you ever need Internet Explorer for testing a web-site.

---

### Post by josh17 on 2013-09-10
Ok so it's settled that I'll remove windows, but I don't think I'll create a restore disk for it. I already put the ubuntu .ISO on a flash drive (I'm not sure if that works, but I don't have a CD) now I just need to figure out how to remove windows. Anyone know?

---

### Post by buzzingrobot on 2013-09-10
You should be able to use  a partition manager, e.g., gparted, to remove the Windows partition and and create a new Linux partition. There's a "Create New Partition" option that will  do just that on the selected partition. 

If you go that route, you'll need to add the partition to /etc/fstab so it's seen and mounted at boot.

You might also be able to simply expand a current Linux partition to use the space previously taken by the Windows partition.

---

### Post by varunendra on 2013-09-10
> **josh17 said:**
> Ok so it's settled that I'll remove windows, but I don't think I'll create a restore disk for it.

DVDs don't cost much, and tools like Clonezilla don't cost much time. But Windows costs both a lot. I'd say, at least create a backup image of windows partition(s) using clonezilla, split @ default 2GB size archives, and write them to a couple of DVDs it takes, keep them safe just in case. If all the user data is moved and garbage removed, the compressed image shouldn't exceed 3-4 DVDs (if win 7, 1-2 if XP).

Unless you are super sure Ubuntu/Linux will be able to fulfill all your needs and you are already comfortable enough with it, you never know if you may need windows again, even if temporarily.

---

### Post by josh17 on 2013-09-10
> **varunendra said:**
> DVDs don't cost much, and tools like Clonezilla don't cost much time. But Windows costs both a lot. I'd say, at least create a backup image of windows partition(s) using clonezilla, split @ default 2GB size archives, and write them to a couple of DVDs it takes, keep them safe just in case. If all the user data is moved and garbage removed, the compressed image shouldn't exceed 3-4 DVDs (if win 7, 1-2 if XP).

Unless you are super sure Ubuntu/Linux will be able to fulfill all your needs and you are already comfortable enough with it, you never know if you may need windows again, even if temporarily.
Well so far I've felt no need to return to windows. Plus I dont feel like windows is so good that I should spend hours putting it on  a disk. If I never need windows I'll probably use my brothers laptop. So I think I'll delete windows.

---

### Post by josh17 on 2013-09-10
I'm going to use OS unninstaller but that will also erase ubuntu, how do i backup my ubuntu data so that when i install ubuntu via my flashdrive i can have all my downloads?

---

### Post by varunendra on 2013-09-10
> **josh17 said:**
> Well **so far** I've felt no need to return to windows. Plus I dont feel like windows is so good that I should spend hours putting it on  a disk. If I never need windows I'll probably use my brothers laptop. So I think I'll delete windows.
Nice to know you trust Ubuntu this much and are already comfortable enough. It's your time vs your property, and finally your decision. However, "so far.." is the key word. ;)

> **josh17 said:**
> I'm going to use OS unninstaller but that will also erase ubuntu, how do i backup my ubuntu data so that when i install ubuntu via my flashdrive i can have all my downloads?

I haven't used it, but from what I have read about it, it should remove only the OS that you choose from its scanned list. Means, your Ubuntu installation should be untouched.

Alternatively, you can do what *buzzingrobot* suggested. It is simple enough and quite straightforward (assuming you are booting from Grub menu) :

Boot Ubuntu Live > Run Gparted > delete the partition that holds windows > recreate a new Linux partition (ext4 is recommended) in the space created by deleting the win partition.

After that, reboot the computer and you'll get the grub menu again (because it does not know yet that windows has been removed). Just boot into Ubuntu and run -
```
sudo update-grub
```
..and the windows entry will be removed from grub menu. And that's all to it.

In both options, you don't need to backup your Ubuntu installation, however, it is always recommended to back up the data in an external drive before doing any kind of partition manipulation. Just in case something goes wrong accidentally..

If you really feel the need to backup the installation and/or the downloaded packages as well, take a look at clonezilla for full partition imaging, or AptOnCD for only packages' backup.

AptOnCD creates a CD/DVD image from packages downloaded with Ubuntu Software Center or apt-get or Synaptic. You can later use this CD/DVD as an offline software source for the exactly same version of Ubuntu installation on any machine. It is available in default repositories.

Clonezilla comes as a Live CD and you will have to download it separately.

Let us know if you need help with any of the above or have questions. I'm sure others will have similar advice and can also help with what I suggested.

---

### Post by josh17 on 2013-09-10
I'm going to bakup ubuntu and then burn ubuntu onto a disk. After that im going to format my harddrive so it's completely wiped, then ill install ubuntu and live happily ever after.

---

### Post by monkeybrain20122 on 2013-09-11
> **josh17 said:**
> I'm going to use OS unninstaller but that will also erase ubuntu, how do i backup my ubuntu data so that when i install ubuntu via my flashdrive i can have all my downloads?

It may be a little late, but if you have an external harddrive it is easy to do this.  You can clone your Ubuntu partition(or partitions if you have a seprate /home) with fsarchiver, save the backup in the external drive, which doesn't have to be very big, just big enough to store the backup, the file is probably rather small because it is compressed and that since you are out of space the original is probably not very big either. Then wipe Windows and format the drive to ext4, then retsore the image from the external drive to your internal drive and it will save everything. In my case my external drive has already another Linix installed so it is formatted in ext4 already. In general I think you don't need to format it this way, but check the documentations.

Install fsarchiver in Ubuntu

```
sudo apt-get install fsarchiver
```


[http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart)

Keep in mind that if you are cloning the same Ubuntu that you are running fsarchiver on you have to use the two options "-a" and "-A",

so if you want to clone /dev/sda2  you would need to run something like
```

sudo fsarchiver -a  -A  -j2 -v savefs  /path/to/backup/folder/ububackup.fsa /dev/sda2
```

Edited: Oops, it seems that you do need to run fasrchiver from a live usb in order to restore the image. I forgot that because l have multiple Linux distos on different drivers and partitions so I am used to running fasrachiver to clone partition A and save to partition B and then restore from B to C etc without thinking..

---

### Post by Mephisto Pheles on 2013-09-13
Keep it.

Clean it up (use CCleaner and let it remove all Windows updates installers, a couple of gigabytes easily, run diskclean and have it remove all system restore points and other stuff, you can even turn off the pagefile, another couple of gigabytes available), so you get free space, toss out / uninstall all the programs and delete all the data you don't need anymore, make it as minimal as you can, defragment it and then resize the partition to a minumum and leave it. The space you freed up will be available to you to use. Format it as Ext4 or NTFS.

 I minimized my XP to 6 GB. And I'm keeping it. 'Till the day I die :) Reminding me where I came from :P And glad I got out in time.

Seriously I use windows only to run Perfectdisk once a month to keep my NTFS partitions defragmented and some other maintenance things.
And it's nice to have something to fall back on if the sh*t hits the fan.

---

### Post by monkeybrain20122 on 2013-09-13
> **Mephisto Pheles said:**
> Keep it.

Seriously I use windows only to run Perfectdisk once a month to keep my NTFS partitions defragmented and some other maintenance things.
And it's nice to have something to fall back on if the sh*t hits the fan.

There are many different Linux distros to fallback to should Ubuntu fail (and there are multiple supported releases for Ubuntu and all distros at any given time, doubt that all of them would fail simultaneously). I wouldn't even recommend Windows as a fallback option. Now if there are specific Windows programs OP needs that is a different story, --which is not the case,--but still you can use Wine or failing that, Virtualbox instead of dualbooting ( I multi-boot several Linuxes but I will never give Windows its own partion wasting space and the time to maintain it for no reason). 

I never hear people  advising Windows users to install Linux in a second partition as a fallback in case sh**t hits the fan in Windows (which happens often enough), Why do we sound as though we have no confidence in Linux? :)

---

### Post by ZoiaGuyver on 2013-09-13
If you have no use for Windows even a really out of the way use, then get rid of it. 

The choice then is which way to go about the distribution. Now this is me personally, I keep one Ubuntu partition that always has the latest LTS release. Then another partition that is the up-to-date release which I use daily. A lot of people say they don't see the point in it, but to me, having maybe a 40g or so partition set aside that is there in case the sh*t does hit the fan with an LTS release that is normally always 100% reliable means I always have a way to get to my data one way or the other (they both use the same /home drive just two different user accounts).

That's what works for me. You will probably find that after installing Ubuntu and getting to enjoy it you will want to try other distros, You could if you keep the windows partition but replace the OS, add and remove distros as you want, without having a worry of it touching your stable install.

---

### Post by matehussilvapb on 2013-09-13
you are right, if windows is useless (you dont use apps just for windows) just keep ubuntu on flash drive for security, it works. ubuntu is rarely a headache for you, different from windows.

---

### Post by monkeybrain20122 on 2013-09-13
> **ZoiaGuyver said:**
> If you have no use for Windows even a really out of the way use, then get rid of it. 

The choice then is which way to go about the distribution. Now this is me personally, I keep one Ubuntu partition that always has the latest LTS release. Then another partition that is the up-to-date release which I use daily. A lot of people say they don't see the point in it, but to me, having maybe a 40g or so partition set aside that is there in case the sh*t does hit the fan with an LTS release that is normally always 100% reliable means I always have a way to get to my data one way or the other (they both use the same /home drive just two different user accounts).
.

I installed the LTS on an external hard drive and keep it up to date. I can boot from it on my own or other computers when I am travelling. If for some reasons I need to replace the non LTS on my main computer I can just clone it and move it over. I got a 500G external hard drive costs for about $50 (it would probably be cheaper in other places). I use it for multiple tested OSes (other than Ubuntu LTS) and for backing up data.

---

### Post by ZoiaGuyver on 2013-09-13
Yeah I use the same with my main system (or well it has external drives), my desktop on the other hand is also the family machine, so having anything external on that for me is suicide (my nephews are a mini demolitions team). If anything can be pulled out easily it normally ends up in someones mouth or thrown around like a rag doll. Hence I keep as much as I can internal :D

---

