---
title: "burning gparted from .rar"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by wallacek on 2006-11-23
Hi all, 
need to resize partitions on HDD.  I have d/l'ed Gparted, it's in winrar format.  properties are listed as an .iso, though.  I want to burn to cd as .iso image then run.  When I extract files, there is 'GPARTED' no file extension, 22.5 MB. then there is the "ISOLINUX" folder, within which is boot.cat, boot.msg, initrd.gz, isolinux.bin, isolinux.cfg, linux, and splash.lss.

Shall I just burn the .iso image from the intial folder (which shows as a winrar icon though it displays a .iso file extension) or do I burn to CD the extracted files? 

Not sure which to do, but I need to get this done in order to open up more room on my XP partition (as that's the one I use for both video editing and 3D modeling software.) The partition that uses Ubuntu is huge; I should have sized them differently when i set up the dual boot, now need to go fix it. 

thanks, 
karinne
thanks

---

### Post by ajgreeny on 2006-11-23
Did you download it in windows or ubuntu?  In any cade you should go to this link to download the iso of the latest version and burn that as an image to a CD.
[http://downloads.sourceforge.net/gparted/gparted-livecd-0.3.1-1.iso?modtime=1158064629&big_mirror=0](http://downloads.sourceforge.net/gparted/gparted-livecd-0.3.1-1.iso?modtime=1158064629&big_mirror=0)

It may be exactly the same .iso file you could extract from your winrar file but to be safe just check it first.

---

### Post by Bartender on 2006-11-23
OK, I've seen this a few times recently.  Several people were trying to figure out how to unrar their Ubuntu .iso's.  The problem turned out to be the settings in Winrar; it was set up to handle .iso's.
Go into Winrar and tell it to stop taking over your .iso files.  After doing that you might have to reboot, and/or copy the GParted download to another folder, in order to get it out of Winrar prison.

---

### Post by wallacek on 2006-11-23
thanks, Bartender.  Looking into WinRar, I see two possible ways to do this. 
1) (which i believe is the correct thing to do): 

winrar->settings->integration, *uncheck* .iso, therefore it will no longer associate .iso files with winrar.  (.iso was previously checked.)

2)tools->convert archives ->check .iso -> ok. (.iso is now unchecked.)

I am assuming 1) is the correct thing to do. If I do 2), will it dissassociate the current .iso Gparted from the winrar format? 

I didn't have this trouble with ubuntu livecd. That was also in a .rar file, and I burned the cd image and ubie loaded and installed with no problems at all. I've now wasted a few CD's on this issue, and really don't want to waste any more...apparently i need step by step directions. I am currently in WinXP while fixing this (as my fave CD burner, CDBurnerXP Pro, is here.)

any advice on the downloading, installation, burning, and/or use of Gparted would be greatly appreciated. Thanks, 

karinne

---

### Post by ReaderRat on 2006-11-24
First off, download from this site: [**Gnome PARTition EDitor = gparted**](http://gparted.sourceforge.net/index.php)
gparted-livecd-0.3.1-1.iso. >> then burn it to CD-R.

ISO - Downloading & Burning
          **[http://psychocats.net/ubuntu/iso](http://psychocats.net/ubuntu/iso)**
          **[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)**

---

### Post by Bartender on 2006-11-24
Hi, RR, the problem is wallace has WinRar, which is (or was) set up to handle .iso's.  As soon as he downloaded any .iso, WinRar butted in and took over.
Wallace, have you tried either or both of the options you described?  I'm just guessing, but both sound viable.  Do whatever you gotta do to stop WinRar from sticking its nose into your business and maybe try downloading GParted again if you have to.  Seems to me that you oughta be able to do something to shake WinRar loose from the download you already made...

---

### Post by ReaderRat on 2006-11-24
What is Winrar? I have not run into it before.

---

### Post by Delkster on 2006-11-24
> **ReaderRat said:**
> What is Winrar? I have not run into it before.

An archive manager for Windows.

---

### Post by Bachstelze on 2006-11-24
It's a soft for managing lots of archive formats, and it also supports ISO. But it's no problem, just saving the ISO to the drive and burning it using whatever burning apps will still work.

---

### Post by Kevin on 2006-11-24
Why don't you just use an Ubuntu live-cd? They have gparted on them as far as I know, and if they don't you can easily install it from Add Applications.

Either way, if you downloaded a .iso, and winrar is opening it, just ignore the file, go into your burning program, find out where you can burn an image, and select the .iso file.

---

### Post by Bachstelze on 2006-11-24
Because the GParted on the official Live CD is more recent than the one on the Ubuntu Live CD and can do stuff the other can't. And besides, the Ubuntu Live CD with the install-thingie takes forever to load while the official one is a breeze.

---

### Post by wallacek on 2006-11-24
Replies to above: Bartender- yep, tried both fixes. I have other Ubuntu problems at the moment unfortunately requiring a clean install, but yes, dissassociating .ISO from winrar prevented winrar from hijacking my .iso d/l's. The odd thing about this is that winrar also saved my Ubuntu liveCD in .rar format, and that burned to CD ok as an iso image and installed w/o problems. 

I am having no end of trouble with Gparted (which is why i went to partitionmagic which seems to have f**ed up the entire shebang w/o hope of recovery. I won't use it again.)


In any case, the Gparted I have from the LiveCD doesn't work. All of the partition tools are greyed out, whether the drives are mounted or not. 

I must admit, I don't have a good complete understanding of mounting / unmounting drives and what that accomplishes, so my newbie status is probably what's screwing everything up. 


But hey, I'm an engineer, that's how we do things. We break stuff in the process of figuring out how it works, and then figure out how to put it back together (hopefully better than it was before).  

All my computer skills have been acquired this way- mess with it till it breaks, then try to fix it. ha- i've done a lot of re-installs, needless to say, esp. of Windows.  


thanks for y'all's help. these forums have been GREAT for declining the steep angle of the learning curve, and even though I just broke the whole thing, I'm still enjoying puttering about with it. 

regards, 
karinne  (wallacek)

---

### Post by wallacek on 2006-11-24
clarification of above:
"the Gparted from the LiveCD" referenced that doesn't work is the one that came installed on the Ubuntu liveCD. I haven't gotten one to install from the disc image of the Gparted LiveCD.  That's for later.  
thnks again
karinne

---

