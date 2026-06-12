---
title: "Does dual booting slow performance?"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by -Ghost9- on 2007-06-13
The last time I dual booted, I noticed that when I loaded windows it actually took a few seconds longer to load. Does dual booting slow the performance of my system?

---

### Post by pardesi on 2007-06-13
depends on your system specs...it does consume some RAM but then if you have it in GB's or some big MB's(>=512 MB)  then i think u won't feel that much of a difference

---

### Post by -Ghost9- on 2007-06-13
> **pardesi said:**
> depends on your system specs...it does consume some RAM but then if you have it in GB's or some big MB's(>=512 MB)  then i think u won't feel that much of a difference

hmm. so it could hurt the performance of programs and games.... hmm. I have 2 gigs, but it was noticeable that it loaded slower. Maybe I just need to use a separate hard drive, but then I'm not sure how to switch back and forth between them easily.

---

### Post by starcraft.man on 2007-06-13
> **pardesi said:**
> depends on your system specs...it does consume some RAM but then if you have it in GB's or some big MB's(>=512 MB)  then i think u won't feel that much of a difference

Uh, No...

Dual booting involves installing two separate (key word) OSes to your drive. You boot them separately, when your in Linux, Windows is consuming 0 resources as its inactive (vice versa). If you are running a Virtual machine in one to access the other, that will consume the exact (maybe a lil more) resources as the machine your Virtualizing.

If you dual boot, theres no reason to see a slow down (when active). I have a dual (soon to be triple boot) and its as fast as when I started with just XP. That said, I have seen Windows slow down on the boot up over time (and in running overall). That is simply a property of Windows I am afraid and I can't say anything in particular causes it, its probably a combination of the registry for slowdown when booted up and a few other things.

---

### Post by pardesi on 2007-06-13
i have 1 gig but couldn't find that much of a diiference...i don't have any games,themes,....:)

---

### Post by pardesi on 2007-06-13
> **starcraft.man said:**
> Uh, No...

Dual booting involves installing two separate (key word) OSes to your drive. You boot them separately, when your in Linux, Windows is consuming 0 resources as its inactive (vice versa). If you are running a Virtual machine in one to access the other, that will consume the exact (maybe a lil more) resources as the machine your Virtualizing.

If you dual boot, theres no reason to see a slow down. I have a dual (soon to be triple boot) and its as fast as when I started with just XP.

i had serious practically observed misconceptions:(

---

### Post by starcraft.man on 2007-06-13
> **pardesi said:**
> i had serious practically observed misconceptions:(

It's ok, I make mistakes too (lots in fact) :p.

---

### Post by EdThaSlayer on 2007-06-13
My Windows boots up as fast as usual. Probably because I don't use it that much and have a nifty app called CCleaner that gets rid of the buildup of "fat" and "cholesterol" in the Windows registry and C:/ drive.

---

### Post by Pink Splat on 2007-06-13
I personally have not felt my system slow down since I have had Ubuntu/XP in dual boot. I also don't see how it would slow it down, as said above you are only using one part of the hard drive at a time, not both. 

Maybe the partition file type may slow or speed up the booting process. Windows XP uses NTFS (New Technology File System) while Ubuntu uses ext3 or ext2. From what I've read NTFS and ext3 are about the same in speed/performance - I could be wrong here, its not good to trust internet sources. The file systems on your hard drive could be causing your slow down, especially if you are running FAT on your Windows partition with more than a 10gig HD and 96MB or less cache ([http://deadline.3x.ro/adsense/ntfs_vs_fat32.html](http://deadline.3x.ro/adsense/ntfs_vs_fat32.html)).

If any of this info is wrong, please correct me.

---

### Post by earobinson on 2007-06-13
the only thing that might have been done is that when you installed ubuntu you resized your windows partition and that might have caused fragmentation, try defraging!

---

### Post by shae on 2007-06-13
Dual-booting will slightly change how long from powerbutton to OS, but in terms of actual speed it will not be affected.  This is because to boot to windows, you have to select it in GRUB which loads the XP boot loader then boots XP.  This however does not add much time.

If you think the actual install is slower, then it may be.  If you resized the partition of XP when setting up ubuntu, then their might be a problem.  You should run check-disk and defrag your hard drive.  You should also make sure you have a paging file or are using SwapFS in windows.  I hope this helps.

---

### Post by rsambuca on 2007-06-13
The only way I could see dual-booting affecting your Windows performance is if you have partitioned your drive and not left enough space on the Windows NTFS partition.  Windows definitely starts to act 'funny' if it doesn't have extra disk space for some reason.  Perhaps there could be possibly be a slowdown on bootup if you have the ext2-ifs driver installed in XP, but I doubt it.  I currently have 6 OS's installed and haven't seen a slowdown in Windows at all.  In fact, since I use it so rarely now, when I do use it, it runs fairly quickly since I haven't had the usual slowdown that comes with usage in XP.

---

### Post by pardesi on 2007-06-13
> **rsambuca said:**
>   I currently have 6 OS's installed

:-({|=:mrgreen:\\:D/

---

### Post by HotShotDJ on 2007-06-13
Once booted there is no performance hit as long as you've got a large enough partition -- but thats true whether or not you dual-boot.

I HAVE seen it take a little longer for Windows to boot up after installing a second OS.  It had to do with Windows trying to figure out the non-Windows partitions.  If this is a problem for you, you can set up GRUB to hide the non-Windows partitions from Windows.  You'll have to google for the method, since I have no idea the exact syntax.... something like "Hide (0,2)" or some-such.

---

### Post by starcraft.man on 2007-06-13
> **rsambuca said:**
> Windows definitely starts to act 'funny' if it doesn't have extra disk space for some reason.  

This is very true. I forgot about that. It's actually worse on the Mac. If you don't have lots of extra GBs it really comes to a crawl. I saw it happen on a friends a while ago. It was one of the only times I saw super bad performance out of a Mac on OSX (and there was nothing else wrong with his Comp, he just had been downloading and almost topped his drive out with only 2-3 GBs left). Leo Laporte a podcaster (you should know him from tWiT) also reported this issue in one of his mac podcasts to my knowledge.

---

### Post by Inxsible on 2007-06-13
Ever since I installed Ubuntu, I have not had the need to log in to Windows Vista. So I dont really see any hit on my Vista performance ;)
 
But now, I am thinking the 25GB I left for Windows Data is way too much and I might cut it by 10 GB and give it to my root or my home partition ;)

---

### Post by smartsaah on 2007-06-13
> **starcraft.man said:**
> Uh, No...

Dual booting involves installing two separate (key word) OSes to your drive. You boot them separately, when your in Linux, Windows is consuming 0 resources as its inactive (vice versa). If you are running a Virtual machine in one to access the other, that will consume the exact (maybe a lil more) resources as the machine your Virtualizing.

If you dual boot, theres no reason to see a slow down (when active). I have a dual (soon to be triple boot) and its as fast as when I started with just XP. That said, I have seen Windows slow down on the boot up over time (and in running overall). That is simply a property of Windows I am afraid and I can't say anything in particular causes it, its probably a combination of the registry for slowdown when booted up and a few other things.

I totally agree with starcraft. I am using 512mb dual boot machine with XP and 7.04 loaded in it.  My PC's performance didn't differ even in the slightest manner. If yours has been affected, then there might be some other issue involved...:)

---

### Post by phr0ze on 2007-06-13
It's all coincidence or your mind playing tricks on you. Dual booting does not hurt your performance.

---

### Post by Tyke91 on 2007-06-13
the amazing speed of ubuntu is making windows look slower 	\\:D/

---

### Post by starcraft.man on 2007-06-13
> **Tyke91 said:**
> the amazing speed of ubuntu is making windows look slower 	\\:D/

LOL! Aye, it can do that very easily. I mean just pick a mid range/average pc and try running GNOME/Beryl and Vista/Aero on them both and you'll see a difference.

Windows may just have come to the point where they have so much legacy baggage and other closed/poor code that its a serious detriment unless you've got a top of the line PC. Anyway, poor performance of Vista is another matter. Topic has been answered we should stop posting. I will just repeat it in big bold letters.

Dual booting **_DOESN'T_** slow the PC.

---

### Post by -Ghost9- on 2007-06-13
> **HotShotDJ said:**
> Once booted there is no performance hit as long as you've got a large enough partition -- but thats true whether or not you dual-boot.

I HAVE seen it take a little longer for Windows to boot up after installing a second OS.  It had to do with Windows trying to figure out the non-Windows partitions.  If this is a problem for you, you can set up GRUB to hide the non-Windows partitions from Windows.  You'll have to google for the method, since I have no idea the exact syntax.... something like "Hide (0,2)" or some-such.

this sounds like the most likely thing occurring. It is not in my head thank you very much. I can tell the difference but I didn't really measure the performance beyond the boot. Basically I notice that the start bar and icons take a few seconds longer to appear once windows has started. A blue will be in it's place. As if it's still searching for something. And it will happen consistently on start up.  I never see that when just xp is installed. I think I may look into the quoted suggestion. I'm on an 80 gig raptor drive if that makes any difference.

---

