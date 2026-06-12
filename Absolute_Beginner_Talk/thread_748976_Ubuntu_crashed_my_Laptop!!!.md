---
title: "Ubuntu crashed my Laptop!!!"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by novelidea on 2008-04-08
I have (did have!) a nice Thinkpad T40 with Windows XP Pro installed on it. Had the machine for a couple of months and it was wonderful.
So, I decided to try Ubuntu 7, got the download, burnt it to disk, ran it. I played about with it from the disk for a few days, then decided to install it onto the hard drive - I followed all the instructions to the letter. 
Then I got and error when I reset - Grub loading, please wait ...Error 18

I read up on this and found nothing helpful - Now my PC is dead - No Windows XP and no Ubuntu 7 !!!

I read more on the net and someone said try to get the Windows OS back by using the original Windows CD and try the R Console - but all I got was an error, drive cannot be accessed. It's like my drive is NOT THERE!!

Everything I have tried has got me knowhere. I can't even try to re-install Windows XP cause it says it Can't Access my Hard Drive!  

Can Anyone Help?  Please remember- I am new to this stuff.

---

### Post by keypox on 2008-04-08
LOL take a deep breath your computer is fine well sorta... Did you check in the bios and see if your HD is being recoginized?  
It sounds like your HD might have stopped working... You can prob just reinstall windows and have no problems.  But your HD might be dead in that case you should take it back or RMA it.

---

### Post by riven0 on 2008-04-08
Very weird. Can the Ubuntu LiveCD access your hard drive? The reason I'm asking is because if Windows can't access it, then most likely there is something wrong with your hard drive. It's quite a coincidence that it conked out after you installed Ubuntu, but it's possible your hard drive was on the way out and installing a new operating system on it pushed it over the edge.

---

### Post by spiderbatdad on 2008-04-08
I have run ubuntu on a T-40 and T-30 for several years, and it runs as if it was custom tailored to machines. I can't imagine why you are have this issue. 
You say you have tried the xp cd, but have you tried booting from the ubuntu live cd?
Can you get into system bios? Is cd selected as the first source to boot from?

---

### Post by novelidea on 2008-04-08
Ok, couple of points - 
   I do not see my hard drive in BIOS, but I never did, yet it always worked fine until now
   I do have access to the hard drive though. I can run Ubuntu from the Live CD and I can read and write files to the hard drive with no problems, and I can even see all my Window files including my Desktop files, music files and more.
   Keypox said to re-install Windows - Well, I was thinking about it, but I can't do that either. Recovery Console just gives me an error and says it cannot access the drive, and when I tried to re-install completely, it says it cannot access hard drive, yet it does show it's size and everything.  Also, What does RMA it mean?
   Someone said to me the the MBR could be corrupted in some way and to fix it. I tried this, but it did not help. I tried Powersuite 2007 to give me access to the hard drive and to try and fix the MBR this way, but it could not access the drive.
   
   I am at a loss.

I really don't want to change the drive, I'm new to this and opening up the laptop to install a new drive scares the hell out of me. lol

  Anyone?

---

### Post by tgalati4 on 2008-04-08
If you don't have a back up of important data from both the Windows and Ubuntu partitions, now is the time to grab some new flash drives and start recovering data.  Once you have made your backups then we can try a few things to repair the MBR and/or the partition table to recover your GRUB.

There are several tutorials on the forums for restoring GRUB, but you need backups if your disk is failing.  I presume your drive is 3 years old?

---

### Post by KLR650 on 2008-04-08
As far as recovering the data goes, you might want to try Puppy Linux.  (If you have access to another computer to download and burn the iso) [http://puppylinux.com/]("http://puppylinux.com/")  

You can run it as a live-cd, but it runs totally in ram meaning that you can remove the live cd after it has loaded and use the optical drive on your laptop to backup to CD's or DVD's

Good luck repairing the MBR or reinstalling

---

### Post by 6gt on 2008-04-08
Hi.. If i got it right, ur harddisk is still intact
only problem is ur xp is not loading
so just re-install xp.. the problem is it wont work as ordinary pcs.. so, goto bios and change SATA from AHCI to Compatibility..
now install xp n it vl b fine..

---

### Post by Tomatz on 2008-04-08
Download this:

[http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

Burn it to disk **as an iso**

Boot your computer with it and it will enable you to boot at least xp, probably ubuntu and reinstall grub (the bootloader) which i expect you need to.

---

### Post by Delkster on 2008-04-08
> **novelidea said:**
> Keypox said to re-install Windows - Well, I was thinking about it, but I can't do that either. Recovery Console just gives me an error and says it cannot access the drive
Does that happen if you try something like [fixmbr](http://pcsupport.about.com/od/termsf/p/fixmbr.htm)? If you can get that working, you could probably get the bootloader (GRUB) replaced with the Windows bootloader, allowing you to at least boot Windows.

> Also, What does RMA it mean?
[http://en.wikipedia.org/wiki/Return_merchandise_authorization](http://en.wikipedia.org/wiki/Return_merchandise_authorization), but it doesn't sound to me like the disk itself is necessarily physically defective, so I wouldn't do that just yet.

Apart from a simple bootloader issue, it might also be a problem with the partition table, particularly if installers etc. that have previously been able to see the partitions are no longer able to do so.

Since the Ubuntu live CD can apparently see your disk and its partitions fine, let's try to get things working from there (if fixmbr or something doesn't bring back Windows booting -- I'd try that first if possible).

---

### Post by mbadawi23 on 2008-04-08
I work with IBM/Lenovo computers everyday at work and I know it pretty well specially because I am a programmer who uses both environments Linux and Windows.

First of all you know that linux-based distros use a different file system than WinXP (NFS Vs NTFS or FAT32) so unless you explicitly partition your hard drive to keep NTFS partetions intact it is wiping all your hard drive in the process. Which is part of your problem I assume. Another assumption that I'm making is that you did NOT install ubuntu to use the WinXP boot loader instead.

Now, all IBM computers ship with a hidden partition for rescue and recover or the "ThinkVantage" feature. which is very irritating when you try using your computer as if you own it :S. Any ways, in order for the Rescue and Recovery feature to work.

I think you may be able to restore your factory settings by following these steps:
     1. At  BIOS startup hit "Enter" to interrupt normal startup.
     2. then hit "Enter" again to pause the timer that counts 10 seconds and resumes normal startup.
     3. Review your selection then hit "F11" to enter the Rescue and Recovery mode "ThinkVantage Technologies".
     4. After that you want to restore original factory settings.
     5. Sorry about your lost data.

---

### Post by Tomatz on 2008-04-08
> **mbadawi23 said:**
> I work with IBM/Lenovo computers everyday at work and I know it pretty well specially because I am a programmer who uses both environments Linux and Windows.

First of all you know that linux-based distros use a different file system than WinXP (NFS Vs NTFS or FAT32) so unless you explicitly partition your hard drive to keep NTFS partetions intact it is wiping all your hard drive in the process. Which is part of your problem I assume. Another assumption that I'm making is that you did NOT install ubuntu to use the WinXP boot loader instead.

Now, all IBM computers ship with a hidden partition for rescue and recover or the "ThinkVantage" feature. which is very irritating when you try using your computer as if you own it :S. Any ways, in order for the Rescue and Recovery feature to work.

I think you may be able to restore your factory settings by following these steps:
     1. At  BIOS startup hit "Enter" to interrupt normal startup.
     2. then hit "Enter" again to pause the timer that counts 10 seconds and resumes normal startup.
     3. Review your selection then hit "F11" to enter the Rescue and Recovery mode "ThinkVantage Technologies".
     4. After that you want to restore original factory settings.
     5. Sorry about your lost data.

???

Madness :confused:

---

### Post by 6gt on 2008-04-08
> **Tomatz said:**
> ???

Madness :confused:

goto bios and change SATA from AHCI to Compatibility..
now install xp..

i had done it earlier guys..

---

### Post by novelidea on 2008-04-08
> **6gt said:**
> Hi.. If i got it right, ur harddisk is still intact
only problem is ur xp is not loading
so just re-install xp.. the problem is it wont work as ordinary pcs.. so, goto bios and change SATA from AHCI to Compatibility..
now install xp n it vl b fine..

I have no access to my hard drive from the Bios, other than the boot sequence. It is not a SATA either.

---

### Post by novelidea on 2008-04-08
> **6gt said:**
> Hi.. If i got it right, ur harddisk is still intact
only problem is ur xp is not loading
so just re-install xp.. the problem is it wont work as ordinary pcs.. so, goto bios and change SATA from AHCI to Compatibility..
now install xp n it vl b fine..

I cannot re-install Windows because when I try, the Windows XP OS disk cannot access my hard drive except to tell me the current size of it. Recovery Console (r) just says nothing and does nothing, like the drive wasn't even there.

I have backed up all me data though, by using a USB stick and using Ubuntu Live CD. I just can't access the hard drive through any Windows Program.

---

### Post by 6gt on 2008-04-08
since u hav taken bakup, have u tried deleting all drives and creating partitions once again? i hd  done it once wen norton ghost messed up my partition table

---

### Post by novelidea on 2008-04-08
> **6gt said:**
> since u hav taken bakup, have u tried deleting all drives and creating partitions once again? i hd  done it once wen norton ghost messed up my partition table

Yes, I think this is going to be my next step. Any advice on what program to use to do this?

---

### Post by Tomatz on 2008-04-08
Reformat your disc to FAT with this:

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

Just burn it to disc and boot the disc ;)

---

### Post by novelidea on 2008-04-08
> **Tomatz said:**
> Reformat your disc to FAT with this:

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

Just burn it to disc and boot the disc ;)


I have tried using gparted but no luck. It says my partitions are locked or something. No idea what that means.

---

### Post by 6gt on 2008-04-08
u can use ur ubuntu live cd itself.. it provides an option to choose partitons manually while installing

1.start ubuntu usin live cd
2.click install
3.choose manual partition when the setup prompts guided/manual
4.delete partitons, create new(fat) ones and save it
5.quit ubuntu installation, put xp cd and install

---

### Post by Tomatz on 2008-04-08
> **novelidea said:**
> I have tried using gparted but no luck. It says my partitions are locked or something. No idea what that means.

This usually means that the drive is mounted. Could you not unmount?

---

### Post by novelidea on 2008-04-08
> **Tomatz said:**
> This usually means that the drive is mounted. Could you not unmount?

I have no idea what that means or how to do it. lol

---

### Post by novelidea on 2008-04-08
> **6gt said:**
> u can use ur ubuntu live cd itself.. it provides an option to choose partitons manually while installing

1.start ubuntu usin live cd
2.click install
3.choose manual partition when the setup prompts guided/manual
4.delete partitons, create new(fat) ones and save it
5.quit ubuntu installation, put xp cd and install

I am going to try this now. cheers.

---

### Post by Tomatz on 2008-04-08
In gparted you should be able to **r-click on the drive/partition** then select **unmount**. Then you should be able to format ;)

You will need to unmount **ALL** partitions.

---

### Post by stchman on 2008-04-08
> **novelidea said:**
> I have (did have!) a nice Thinkpad T40 with Windows XP Pro installed on it. Had the machine for a couple of months and it was wonderful.
So, I decided to try Ubuntu 7, got the download, burnt it to disk, ran it. I played about with it from the disk for a few days, then decided to install it onto the hard drive - I followed all the instructions to the letter. 
Then I got and error when I reset - Grub loading, please wait ...Error 18

I read up on this and found nothing helpful - Now my PC is dead - No Windows XP and no Ubuntu 7 !!!

I read more on the net and someone said try to get the Windows OS back by using the original Windows CD and try the R Console - but all I got was an error, drive cannot be accessed. It's like my drive is NOT THERE!!

Everything I have tried has got me knowhere. I can't even try to re-install Windows XP cause it says it Can't Access my Hard Drive!  

Can Anyone Help?  Please remember- I am new to this stuff.

Sounds like your hdd crashed.  Ubuntu does not cause hardware failures if your are curious.  I have installed Ubuntu on about 7 different PCs and no hardware failures.

---

### Post by novelidea on 2008-04-08
Thanks for the info my friends!
One more thing - I heard that I could boot to the Recovery Mode in Ubuntu, and I have tried to find it, but I don't see it anywhere. Can anyone direct me?

---

### Post by 6gt on 2008-04-09
Ah.. recovery mode in linux is a command driven process like dos(isn't it?), no use unless u know it well

---

### Post by novelidea on 2008-04-10
Ok. I now have a working PC!   Xp and Ubuntu are working perfectly. I thank everyone who helped.
What I did to fix it was this:
Deleted all Partitions EXCEPT the one XP was on.
I then made another 10Gig Partition and re-installed Ubuntu onto it.
I then reset the PC and was shown the Boot Screen and I had a choice to Boot Ubuntu or Windows XP Pro.
I chose XP Pro and it worked, then after 10 minutes I reset the PC again and chose Ubuntu this time.
That also worked Perfectly - except for about a 4 minute delay before it finally boots up - not sure why the delay but it works, so I'm very happy.

Now I'm trying to get my Wireless Network to work (no success so far) - oh what fun!

Thanks to everyone again.

---

