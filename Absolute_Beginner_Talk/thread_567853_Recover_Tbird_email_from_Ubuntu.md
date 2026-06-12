---
title: "Recover Tbird email from Ubuntu ?"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by gimpguy2000 on 2007-10-05
Hi all, 

My situation is as follows, the grub screwed everything up on my pc and I have lost 3 operating systems due to this. I can access the ubuntu drive and Windowsxp drive and now have a drive that is empty. 

All I want to do is "possibly" take my Thunderbird emails and settings and if I reinstall ubuntu, apply them to a new install so I don't lose them. I have no idea how so help would be appreciated. 


Paul

---

### Post by yabbadabbadont on 2007-10-05
Backup your ~/.mozilla-thunderbird directory and then restore it on the new install.

---

### Post by TeaSwigger on 2007-10-05
GRUB issue, losses of operating systems: it'd really help if you could provide a whole lot more detail. What you did, what happened etc "step by step." May well be worth looking into. It simply may not be detecting them or have some installation problem, which can be fixed with no losses of data or anything.

TBird email: If you can access the relevant user folder (your "home" folder, at /home/your-ID ) all you'll need will be located in a hidden folder named .thunderbird or .mozilla-thunderbird. Copy out everything in there and you can set up a new TBird install, even on another operating system or reinstall if desired, with your emails etc intact.

---

### Post by gimpguy2000 on 2007-10-05
> **TeaSwigger said:**
> GRUB issue, losses of operating systems: it'd really help if you could provide a whole lot more detail. What you did, what happened etc "step by step." May well be worth looking into. It simply may not be detecting them or have some installation problem, which can be fixed with no losses of data or anything.

TBird email: If you can access the relevant user folder (your "home" folder, at /home/your-ID ) all you'll need will be located in a hidden folder named .thunderbird or .mozilla-thunderbird. Copy out everything in there and you can set up a new TBird install, even on another operating system or reinstall if desired, with your emails etc intact.


Hi , thanks. It's not that I don't want to offer up info, but I posted in the install&upgrade already trying to figure this out. To be honesty, the absolute beginner talk you get answers but other areas, forget it. So while I don't get usually more than one answer, it would still be a double post if I did that here you understand, else I would. :(   

I will give this a try in order to backup my tbird install then and post back. 

Thanks and to yabbadabbadont as well. 

Paul

---

### Post by gimpguy2000 on 2007-10-05
Well, I changed permissions, found all files needed but stil it won't copy some needed files and the hiddens have nothing in them at all. I assume this is bad. So I copied what I could and I guess what makes it makes it. If not, then it's simply lost. It stinks to have the whole OS in front of you and not be able to do anything with it, lol. 

Thanks,

Paul

---

### Post by philinux on 2007-10-05
Using the live cd and terminal use gksudo nautilus. Ignore the terminla error message its a know bug. Hope it gets fixed in gutsy. Enable view hidden files. Now with a root file browser you will be able to hopefully backup your home folder.

I've just been through all this following a HD fault. My sysyem is back again with all my program settings from the home folder.

I have now got home on a separate partition.

---

### Post by gimpguy2000 on 2007-10-05
> **philinux said:**
> Using the live cd and terminal use gksudo nautilus. Ignore the terminla error message its a know bug. Hope it gets fixed in gutsy. Enable view hidden files. Now with a root file browser you will be able to hopefully backup your home folder.

I've just been through all this following a HD fault. My sysyem is back again with all my program settings from the home folder.

I have now got home on a separate partition.

Thanks for the info. I got Windows up and running at least. I had to delete the grub in Ubuntu using live CD, then I was able to get Windows xp disk to boot for mbr fix. It wouldn't prior.  Since I am not getting help elsewhere I may as well at least explain my issue..

I wanted to install PCLOS over Fedora7. I have 3 drives, 

hda >windowsxp pro>80gig wd

hdb>nothing now 80gig maxtor

hdc>Ubuntu somewhere >120 gig wd

What happened was, when I tried installing PCLOS, it stopped everything from booting and all I got was a GRUB_ and couldn't do anything with it.  There were no signs of life at all, Windowsxp disk wouldn't boot, said insert media , no os found, yadda yadda. So the only thing that would boot is Ubuntu live or knoppix. Oddly enough, Knoppix would not allow me access to even write to my usb thumb drive. Very strange for knoppix. 

So anyway, I couldn't make a cd of super grub fix since I only have one drive and that was running my OS. I have no floppy either, took it out for hard drive room. Plus this old pc won't boot to USB anyway. Another thing, my menu.list looks just fine when I could read it in gui mode from live cd. I couldn't view it using sudo command or with any text editor, as if it didn't exist but did at the same time. 

So finally as mentioned, I deleted menu.list, and grub as well as I could and this finally allowed Windows to boot from CD, do an mbr, went back in and replaced the grub and such with a backup from USB and the rest is history. However, I still don't have Ubuntu showing any signs of booting. See, I do back up my info but have to use DVD currently until I can get Ubuntu to even recognize my network shared disk on my son's pc. So I don't have a recent else i'd go through MANY dvds. 

So that's where I stand right now. I cant attempt to backup the home folder as you stated and then reinstall. It may be my only option.

---

### Post by philinux on 2007-10-05
With the live cd can you browse all the drives and see whats there especially hdc?. You could back up your home to hda or hdb.

---

### Post by gimpguy2000 on 2007-10-05
> **philinux said:**
> With the live cd can you browse all the drives and see whats there especially hdc?. You could back up your home to hda or hdb.


Yep, I can browse them using Ubuntu live. I figured instead of installing another OS to leave one drive open for all backups like I used to do, made things much easier. So this would be on the same path then. Problem is, what do I format the empty drive as , ext3 I assume? Then I should be able to save the home folder to it, correct?

TX

Paul

---

### Post by philinux on 2007-10-05
If your going to use it as extra storage from ubuntu the ext3. If you want to use it as a common drive then fat32 I suppose. Depends what you want to use it for.

---

### Post by gimpguy2000 on 2007-10-05
> **philinux said:**
> If your going to use it as extra storage from ubuntu the ext3. If you want to use it as a common drive then fat32 I suppose. Depends what you want to use it for.

It seems this will work. I did create and ext 3 and wrote to it. I wish it could have windows access and Ubuntu but as Windows is too stupid to read anything and if I put it as ntfs I lose permissions to write obviously. I eventually want to share this drive on the network. 

  I tried super grub after being in Windows as I was able to get it to disk and boot from it.  I read over all the options and tried just about everything but it has done nothing to fix the grub at all. I can boot to Ubuntu using the disk and that's about it. I don't know much about the grub but saw it stated it was one of the easiest booting files and such, well I would argue that. If Linux wants users to migrate, there have to be some grub changes, or at least more user friendly as well as get along with it's own kind "other linux OSs. " 

My main issues with Grub have been, not being able to remove it, it stopping the system from booting to anything, not sharing with other Linux OS's unless you go through modifying it which if new users want to experience more than one linux os, they could be easily turned away I think, repairing is a nightmare, even thought I have used every technique I can think of, even super grub , nothing has come close to allowing me to boot from Ubuntu on it's own or have a choice of which. Right now, only windows. These are not just Ubuntu issues, I had issues with grub in the past. 

That said, I am going to simply have to reinstall and then migrate my home folder if it works. We'll see. 

Thanks again,

Paul

---

### Post by gimpguy2000 on 2007-10-05
I just reinstalled Ubuntu completely, fine, I unpacked or installed, whatever it's called, my backup into my current install, fine. Then I copied my home folder items, not whole home folder as I gave up on that, too much anyway and didn't want to screw up the system. Come to find, it didn't matter anyway, same thing happened as the last time I restored from backup in command mode, Ubuntu WONT boot. It gets to the Ubuntu loading screen and freezes. So as always, I'd have to just start from scratch YET again and wasted another number of DVDs for backups that won't work anyway. 

This is the last Ubuntu or Linux install I'm doing,  I am not trying any others. If I reinstall and try yet again to run my backup and it won't work, I give up and admit defeat and will crawl back to Windows. I think 6 months of dedication to trying nothing but linux was a fair amount of time and if I still can't do some basic operations without the system going down, forget it. 


Paul

---

### Post by TeaSwigger on 2007-10-05
Video or hard drive, that's what comes to mind. I know this may not fit but I'm just trying to help...

One possibility is that the hard drive is faulty and failing, have you tested it? The manufacterer of the hard drive may provide a free utility with which you can confirm the integrity of your hard drive. If it's having problems, Windows won't be safe either (and you're that much less likely to get warning before unrecoverable failure).

If the problem you are having is that it starts to boot to that loading screen then just stalls there forever, a very likely cause is that your video card or video configuration is preventing it from booting right, or is sometimes preventing a boot. Reinstalling isn't a way to fix that; in Linux, a failed boot doesn't usually mean a reinstall is in order; just fix the boot issue, possibly just editing one line in a system text file, and all the rest is still just fine, no need to lose any files or risk losing them. 

If this sounds like what's happening to you. To troubleshoot if it is a video problem do the following.

When you see the boot screen - where you choose what to boot to - pick the main Linux choice and press "e" (for edit). This will allow you to safely and easily edit the boot commands for this one time just to test it. What you want to do is to add an item to the end of the boot command which will turn off the graphical booting screen. If it goes ahead and boots without the graphical booting screen then it's only a video setting problem. Okay after pressing "e" you'll be presented with the list of boot lines for that item, the main linux you want to boot. Pick the long line. Go to the end of that line. Remove the "quiet splash" words and put in "nosplash." When done just press "b" (for boot). You should be off and running the boot, with loads of text scrolling by. And more loads of text. Thank goodness we don't have to enter everything by hand anymore, take a moment to smile at how far things advanced for us. 

Anyway, it should continue fairly smoothly until it goes black for a moment, then it goes graphical and the cursor comes up and X loads and the log in screen. If this stalls forever and the log in screen won't come up, the video settings are wrong. You can still fix it without touching the rest of the system, I just don't happen to know how yet, someone else can help there. If it does go ahead and you're all logged in and everything's running ok, open the file /boot/grub/menu.lst with admin rights. Find the same line you edited at the boot screen and change it to the same thing that worked, replacing splash with nosplash. This will make the edit permanent so you can boot each time safely, until you find the solution.

---

### Post by gimpguy2000 on 2007-10-06
> **TeaSwigger said:**
> This will make the edit permanent so you can boot each time safely, until you find the solution.

Thanks for the tip, much appreciated. I have tried Ubuntu on two different hard drives and just got the 120 gig a bit ago and have loaded other OSs as well and they work fine. As well, Ubuntu works fine, it's only if I try to restore a backup I made using the command line backup native to Ubuntu. Same with the video, all runs smooth until I try a backup restore. 

This is  a fresh install right now and no problems but I know if I try and restore my settings and installs and files what is going to happen. This happened before too. I got the backup method off of Ubuntu here somewhere in the forum. 

The restore sequence is this.. tar xvpfz backup.tgz -C /   which works but I also get an error with every time.  Then of course I can't boot.  This has happened on early installs and currently too. 

As long as I don't try to mash older files with my new system, all works well, it's when I try any sort of restore I get issues. I wish there was a sure fire way to restore information but seems not. If I knew how to make a simple script for installing some codecs, java, or the pain in the rear lexmark driver, among others, it may not be so bad, but I get tired of downloaing 182 updates after every install since I can't restore anything. I downloaded a new iso too and still I get 182 updates, I thought they would be included but not. 

Heeeyyy, I know installing updates should come first, however, I assumed by restoring by using the above method would put the updates in as I backed up after updates were done so I did so before installing updates, could this be an issue? 

Thanks,

Paul

---

### Post by gimpguy2000 on 2007-10-06
After reading through the backup thread , I noticed others have the same issues using that backup so I think i'm going with something else from now on. 

Cheers,

Paul

---

### Post by TeaSwigger on 2007-10-06
Sorry to hear it's such a problem Paul. Although I'm quite a ways from being an expert about restoring, yes I can say that restoring like that on a system that isn't identical absolutely could cause all kinds of trouble. Even if it was identical I, personally, would be wary of that method on any kind of system. No good reason; honestly I've never tried a massive backup. I only back up unique or important personal files using say, Keep (a limited but easy backup utility for KDE, being as I use Kubuntu). It's just my own feeling that if there's a catastrophic problem to make me have to use backups in the first place, I'd rather install anew and then just copy in my personal files. That way there's no problems lurking or issues with mismatched anything. Same way with Linux or Windows. Just don't have that much confidence in any home computer technology to do much more in the way of back up yet. It's all so complex and fragile. That's just me though. Good luck to you.

---

