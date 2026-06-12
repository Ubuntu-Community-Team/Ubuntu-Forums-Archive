---
title: "Uninstall Vista"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by The Populist on 2007-10-06
I've been running Ubuntu for over a month now, and I haven't used Vista one time. I just bought this machine, a low end Presario with AMD 64 and 512 megs of RAM. It's too slow to run games in Vista, so I just don't need it anymore. 

I installed the dual boot Ubuntu/Vista, and now I want to uninstall Vista completely. There's no sense in that bloatware using most of my hard drive space if I don't use it. Can someone direct me to where I uninstall Vista from a dual boot Vista/Ubuntu set-up?

...

---

### Post by rfruth on 2007-10-06
To completely uninstall reinstall & use the* entire * hard disk for Ubuntu or if thats too much the gparted utility can be used ...

---

### Post by Niniel on 2007-10-06
Yes, just start the partitioning tool and delete the Windows partition. Then extend your Linux partition to take up all of the hd.

---

### Post by FrozenFlame22 on 2007-10-07
Be sure to backup all your data first!

If your Vista partition is first on the disk, which is usually the case, then you'll need to just reinstall Ubuntu and use the entire drive. You can't extend partitions to earlier sections of the drive, just later sections.

I'm pretty new to Ubuntu myself, so YMMV.

---

### Post by The Populist on 2007-10-07
Ok, how do I access the partition in Ubuntu? If I can, I'll just max out the Ubuntu settings and keep Vista in a small art of the Hard drive. I dont want to re-install but if I have to I will.

...

---

### Post by LaRoza on 2007-10-07
> **The Populist said:**
> Ok, how do I access the partition in Ubuntu? If I can, I'll just max out the Ubuntu settings and keep Vista in a small art of the Hard drive. I dont want to re-install but if I have to I will.

...

It will be best to erase the partition with GParted, or with a live disk. Ubuntu has the software on the live disk, but I recommend using the GParted Live CD. 

You can make that partition a new one, for storage, I recommend just reformatting as EXT3 if you do that. However, I would just reinstall everything after making a backup of all my data and settings. If you remember what sofware you have, you can just copy the files in your home directory, press Ctrl+h first, to a disk or flash drive and transfer them back after the reinstall. It will take some time, but things will be easier after with  a more logical partition layout.

---

### Post by The Populist on 2007-10-07
What if I went back to the Vista side and adjusted the partition there? Also, I think I maxed out the partition available to Ubuntu. My hard drive is small 120 gig, so I need all the space I can get.

..

---

### Post by TeaSwigger on 2007-10-07
Won't let ya. Can't change a partition that's in use.

If you just see no point to having the Vista on there, the easiest way is to use an app in Linux called GParted. Find which partition (section) of the drive Vista is sitting on, note that number (like sda1 or whatever). Unmount the Vista partition if it happens to be mounted already, so you can change it. Then delete just that partition. Reformat it using ext3 file system, call it whatever you want and set it to mount where you want. You could use it for backup space, or for a certain game, or whatever you like.

For best results and being able to set up partitions any way you want, you'd have to just start with a fresh new install of Ubuntu.

Typing this from a 256mb PC with 30gb hd (Kubuntu installed with Fluxbox as window manager) so I'd be glad for your 512mb / 120gb hehe 

Either way, congrats for making the effort to avoid just taking whatever Microsoft doles out at you and enjoy your computer, your way :)

---

### Post by The Populist on 2007-10-07
Ok, if I do a complete re-install of Ubuntu, what do I lose? Would I lose saved Openoffice documents? How about Firefox?

...

---

### Post by Sef on 2007-10-07
> Ok, if I do a complete re-install of Ubuntu, what do I lose? Would I lose saved Openoffice documents? How about Firefox?

Yes and Yes, unless you have them on a separate partition.   **Back up** your data first.

---

### Post by lightstream on 2007-10-07
> **The Populist said:**
> Ok, if I do a complete re-install of Ubuntu, what do I lose? Would I lose saved Openoffice documents? How about Firefox?

...

You seem to have decided you might as well keep Windows - in which case you won't need to reinstall (your Windows is almost certainly on the first partition because I assume it came with just Windows installed & you put Ubuntu on later)

Just run GParted from Ubuntu, and resize your Windows partition down to as small as you want it. Then stretch your Ubuntu partition. You may need to move your swap partition, but I would have thought it would be after the Ubuntu one in which case it wouldn't pose a problem.

It may take some time (eg 4 hours!) to stretch your Ubuntu partition, depending on how big it currently is.

However, I did just this procedure myself when I realised I didn't want Windows to have as much space as I'd at first given it, and it worked fine.

Edit: oh, and upgrade from Vista to XP - it will definitely run much better on your system's limited resources. I wouldn't recommend getting a torrent for it, as that would be free and Microsoft are in need of as much money as they can get if Paul Allen is to be able to refurbish his Octopus yacht adequately this year

---

### Post by HokeyFry on 2007-10-07
if you do a complete reinstall of ubuntu, yes you will lose anything you dont back up. a way to combat this is to make your base system / on one partition, and your /home folder on another. 

this way if you screw up your current distro, you can still reinstall without losing anything in the /home folder.

---

### Post by HokeyFry on 2007-10-07
oh, and DONT USE LINUX TOOLS TO RESIZE A VISTA PARTITION. IT WILL MAKE YOUR VISTA INSTALL UNBOOTABLE


i went thru hell with this. just to make it simple use the tool that comes with vista. i dont remember what its called but im sure someone here knows or you can also search for how to resize a vista partition in windows.

---

### Post by The Populist on 2007-10-07
Can someone direct me to info about going into Vista and adjusting the partition? I think I'm going to hold off on the complete uninstall. Not because I care about Vista, but I need my settings. Could someone tell me how to back up my Ubuntu settings?

...

---

### Post by dptxp on 2007-10-07
Defragment the Windows Partition first from Windows.
Next, using Gparted, resize it (from start).
Format the free space in EXT3 to make it a data partition.
Mount the partition in Ubuntu.

---

### Post by lightstream on 2007-10-07
> **The Populist said:**
> Can someone direct me to info about going into Vista and adjusting the partition?
Yes, [google can]("http://www.google.com/search?q=Vista+adjusting+partition")! (I must say I'm impressed that this very thread is already listed in those Google results...)

---

### Post by The Populist on 2007-10-07
Ok, I found Gparted in the synaptic package manager. I applied it, now where do I access it from?

...

---

### Post by HokeyFry on 2007-10-07
dont use gparted to change an NTFS partition if it is Vista, unless gparted or anything else has been updated in the past few weeks to accomodate the NTFS update. Using Linux tools in this case killed my ability to boot vista

[http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista/](http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista/)

---

### Post by The Populist on 2007-10-09
Thanks for all the info people. I have decided to kick Vista off my computer. So I am going for a fresh install of Ubuntu. All I need to know how to do is back up my settings. 

...

---

### Post by dondad on 2007-10-09
> **The Populist said:**
> Thanks for all the info people. I have decided to kick Vista off my computer. So I am going for a fresh install of Ubuntu. All I need to know how to do is back up my settings. 

...


You might want to think about keeping the old Vista partition, but reformat it as ext3 and moving your /home to that partition. It is a lot better to have /home on a separate partition because you can reinstall ubuntu without losing your data.

---

### Post by The Populist on 2007-10-09
I appreciate that suggestion but I just have no idea what stuff that is.

Maybe it's just me, but I am picking up a few condescending posts on this thread. Lightstream suggested I google this information. Topical info is great, but I have only managed to install Ubuntu and a 64 bit flash player, by locating exact, detailed instructions, and following those instructions to the letter. I have found the information and technical solutions on this forum.

So again I appreciate any and all suggestions, but detailed instructions on where to find these applications and implement them would be more helpful.

...

---

### Post by Irihapeti on 2007-10-09
For resizing partitions from within Vista, have a look at [http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista/](http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista/)

If what they suggest doesn't work, you might like to look at this
[http://vistarewired.com/2007/04/07/how-to-work-with-partitions-in-windows-vista-xp-when-disk-management-doesnt-work/](http://vistarewired.com/2007/04/07/how-to-work-with-partitions-in-windows-vista-xp-when-disk-management-doesnt-work/)

I have used the first method successfully. I can't vouch for the second. I also have used Gparted; I lost no data nor the ability to boot, but Vista did do a chkdsk and then rebooted itself. It seems that some people have used Gparted on Vista successfully and others haven't. It certainly pays to back up your data first, and it's probably a good idea to download Super Grub Disk and have it on hand for emergencies.

Edit: here's another useful link: [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) He has a lot of useful information on dual boot, Super Grub Disk and other things.

---

### Post by Paqman on 2007-10-09
> **The Populist said:**
> Thanks for all the info people. I have decided to kick Vista off my computer. So I am going for a fresh install of Ubuntu. All I need to know how to do is back up my settings. 

...

Best thing you can do is create a separate partition for your /home, like dondad said.

[Here's a guide](http://www.psychocats.net/ubuntu/separatehome)

/home contains all your preferences and settings. It's also a good place to store your data.

Then when you do your fresh install of Ubuntu, delete the Vista partition, format your / partition, and _do not format your new /home_ partition. When Ubuntu is installed it'll use all the preferences and settings from /home.

So you can see what a wonderful thing a seperate /home is :)

---

### Post by The Populist on 2007-10-10
Well, I did it. I got the Ubuntu disk up in Vista, and chose a full install, with no partition. Thanks for the comments everyone. Now I've got to search for a 64 bit flash solution.

...

---

### Post by booyip on 2007-10-22
I have a similar requirement, but with a triple-boot x86 PC.  I installed XP first, then Vista, then Ubuntu.  So when booting, I get GRUB boot menu first, then VISTA boot menu.  

Now I have seen the error of my ways, and want to delete Vista completely, and have just Ubuntu/XP dual boot.  I'm happy to use gparted to create a new EXT3 partition to wipe out Vista (and create dedicated /home partition), but want to make sure I can still boot XP.  Is there anything more I need to do to make sure this works ok?  Should I just modify GRUB first to add in the XP boot option?  Any other hurdles to be aware of?

---

