---
title: "Reformatting my new Vista Laptop for Ubuntu"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by str1fe on 2007-08-21
I recently purchased [this](http://www.circuitcity.com/ssm/Specifications-of-HP-Pavilion-17-Widescreen-Notebook-PC-DV-9410-US/sem/rpsm/oid/184835/rpem/ccd/productDetailSpecification.do#tabs) laptop from Circuit City, and just ordered the [Ubuntu Soup CD Bundle](http://www.thelinuxstore.ca/index.php?main_page=product_info&products_id=684:5f4dc62c73efc51cbc49e029b5d0d992) from The Linux Store.  I've spent quite a few hours of reading on Ubuntu and Linux in general (both on this forum and on Google), but I still have a few questions.

Once the Ubuntu CD arrives, I plan on reformatting my laptop to get rid of icky Vista, but since I've never reformatted a computer before, I'm still not entirely confident that I'll be able to do so without screwing up the hard drive somehow, or if I'll need my backup discs since I don't really need anything related to Windows.  Any links or tips would be appreciated.  Someone mentioned something about a program called GParted in another thread, so I'm wondering if it might be better to install Ubuntu while Vista's still installed, then use this to remove Vista.

Once I do reformat and am working with a blank hard drive, I want to know if I will be able to run the Live CD (to decide which derivative I like best) and then fully install one of the derivatives once I have chosen one.  Again, since I'm entirely new to Linux and have never reformatted a hard drive, I'm not entirely sure whether I'll be able to do what I want to do.

Finally, I want to know if there's anything driver-wise or otherwise I'll need to download or install for my specific laptop's hardware - the link to the specifications should be above.  After I have it installed, my only real concern is making sure everything works the way it's supposed to without sacrificing any power.

Ultimately I want Vista gone and a fully functional Ubuntu in its place, so anything I can do to easily achieve that is what I'm after. Thanks in advance for your time.

---

### Post by Hobo Joe on 2007-08-21
> **str1fe said:**
> I recently purchased [[COLOR="Blue"]this[/COLOR]](http://www.circuitcity.com/ssm/Specifications-of-HP-Pavilion-17-Widescreen-Notebook-PC-DV-9410-US/sem/rpsm/oid/184835/rpem/ccd/productDetailSpecification.do#tabs) laptop from Circuit City, and just ordered the [[COLOR="Blue"]Ubuntu Soup CD Bundle[/COLOR]](http://www.thelinuxstore.ca/index.php?main_page=product_info&products_id=684:5f4dc62c73efc51cbc49e029b5d0d992) from The Linux Store.  I've spent quite a few hours of reading on Ubuntu and Linux in general (both on this forum and on Google), but I still have a few questions.

Once the Ubuntu CD arrives, I plan on reformatting my laptop to get rid of icky Vista, but since I've never reformatted a computer before, I'm still not entirely confident that I'll be able to do so without screwing up the hard drive somehow, or if I'll need my backup discs since I don't really need anything related to Windows.  Any links or tips would be appreciated.

Once I do reformat and am working with a blank hard drive, I want to know if I will be able to run the Live CD (to decide which derivative I like best) and then fully install one of the derivatives once I have chosen one.  Again, since I'm entirely new to Linux and have never reformatted a hard drive, I'm not entirely sure whether I'll be able to do what I want to do.

Finally, I want to know if there's anything driver-wise or otherwise I'll need to download or install for my specific laptop's hardware - the link to the specifications should be above.  After I have it installed, my only real concern is making sure everything works the way it's supposed to without sacrificing any power.

Thanks in advance for your time.

When you partition your harddrive you will have the option to reformat.

Unless you have some serious hardware issue or an unsupported graphics card, you'll be able to run the liveCD fine.

All the drivers will be automatically installed, except for the the graphics driver, which you will have to install. I would tell you how, but sadly, that link doesn't tell the manufacturer, so you'll just have to wait till you get your laptop to get help on that.

---

### Post by rfruth on 2007-08-21
No need to reformat (unless you WANT to) The Ubuntu CD has a nifty utility called gparted that will resize partitions [http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/]("http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/")

---

### Post by High Camp on 2007-08-21
Howdy,

Welcome to the wonderful world of Linux. To be honest I probably know less than you about the OS, it sounds like you've done more reading than me. That being said, I have lots of experience formating hard drives. With Windows I typically format my hard drive every 3-6 months to clean it of all the crap.

The best way I have found is to do a search for "How to" "format" on google ([http://www.google.ca/search?hl=en&q=%22how+to%22+%22format%22&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=%22how+to%22+%22format%22&btnG=Google+Search&meta=))
From that you will see that you some how need to get to command promt. I have XP and Win2k cd's around just for this purpose. There are also tools that you can download and burn to cd that do the same thing. As you will see in any one of those How To Pages you will type something along the lines of "format c: /fs:fat32 in the command promt. What does this do you as?
format - Cleans the hard drive erasing ALL data.
c: - this is the drive to format, you will probably have to do the same for the d: drive and you can type diskpart to figure out what drives you have.
/fs:fat32 - tells format to do it in fat32 format since your new computer is probably in NTFS format right now.

To answer your other question, yes you can run the live cd once you have formatted your hard drive. Simply put it in and boot that machine and since you won't have an operating system on the internal hard drive it will boot from the cd.

I know that probably created more questions than it answered but it gives you some resources. When/if you need more help post or email me at s.lepine(at)highcamp(dot)ca.

Good luck,

---

### Post by Rupertronco on 2007-08-21
You can test the live cds without having to reformat your hard drive. If you're 100% certain linux is for you, I wholeheartedly encourage wiping Microsoft from as many computers as humanly possible. If you do chose to reformat you will not need to worry about partitioning the drive, unless you're planning on configuring a dual boot system. 

Dual booting will smooth the transition to linux, and will allow you to go back to windows if you feel you can't accomplish something in Linux. Initially I wished I would have taken that route (I impulse installed Slackware 9 after a multitude of problems I had become tired of with Windows) but, I'm now glad I completely eradicated my Windows OS, because it forced me to learn Linux, and I've never looked back. There are plenty of guides to setup a dual boot system if you want to consider that possibility. 

The ubuntu community is far and beyond the best Linux community in existence, if you were to ask me. Any information that's not already here you can find through asking. 

Also, if you'd like to get a faster start on things, simply download kubuntu and ubuntu iso files from ubuntu's main site, and start playing with the live cds now and possibly get to installing.

Edit: Just as a reccomendation, I'd Install Ubuntu or Kubuntu for your first system. Edubuntu might not be the best choice for an everyday, non-student user. Xubuntu is a lighter *buntu install and has fewer pre-installed software packages and runs on the Xfce desktop environment. Kubuntu and Ubuntu run on KDE and Gnome (repsectively) desktops and have the most support available.

---

### Post by Kosimo on 2007-08-21
Your Laptop have Turion64 chip and you can install Ubuntu 64bit edition. But I strongly recommend to use the 32 bit. Just for compatibility reasons.

---

### Post by MQMike on 2007-08-21
GParted how-to:   [http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

(Tips on partitoning/planning.)


In case,

Vista   ***   The definitive dual-booting guide: Linux, Vista and XP step-by-step
[http://apcmag.com/dualboot](http://apcmag.com/dualboot)

---

### Post by Duck2006 on 2007-08-21
You may have to format your drive, with gparted live cd, and then flash your BOIS to get rid of all trace of vista from the system

---

### Post by str1fe on 2007-08-21
Wow, the response has been fantastic...I wasn't expecting to get more than 2-3 replies in 24 hours.  Thanks for the help, everybody, I guess this really is what Ubuntu's all about ^_^

> **Hobo Joe said:**
> When you partition your harddrive you will have the option to reformat.

Unless you have some serious hardware issue or an unsupported graphics card, you'll be able to run the liveCD fine.

All the drivers will be automatically installed, except for the the graphics driver, which you will have to install. I would tell you how, but sadly, that link doesn't tell the manufacturer, so you'll just have to wait till you get your laptop to get help on that.
Thanks, and the video card is an NVIDIA GeForce Go 6150.  I assume that there won't be any major difficulties (I ordered the AMD64 Ubuntu CDs, as I have an AMD64 system), though I really don't know, but that's why I posted the specs, so people that know what they're talking about can help me out on that.

Also, where did you get your name from?  I know someone else who uses the internet handle HoboJoe, he got it from the nickname of a real hobo that lived behind his old middle school or something.  His name is Matt, don't remember his last name.

> **High Camp said:**
> Howdy,

Welcome to the wonderful world of Linux. To be honest I probably know less than you about the OS, it sounds like you've done more reading than me. That being said, I have lots of experience formating hard drives. With Windows I typically format my hard drive every 3-6 months to clean it of all the crap.

The best way I have found is to do a search for "How to" "format" on google ([http://www.google.ca/search?hl=en&q=%22how+to%22+%22format%22&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=%22how+to%22+%22format%22&btnG=Google+Search&meta=))
From that you will see that you some how need to get to command promt. I have XP and Win2k cd's around just for this purpose. There are also tools that you can download and burn to cd that do the same thing. As you will see in any one of those How To Pages you will type something along the lines of "format c: /fs:fat32 in the command promt. What does this do you as?
format - Cleans the hard drive erasing ALL data.
c: - this is the drive to format, you will probably have to do the same for the d: drive and you can type diskpart to figure out what drives you have.
/fs:fat32 - tells format to do it in fat32 format since your new computer is probably in NTFS format right now.

To answer your other question, yes you can run the live cd once you have formatted your hard drive. Simply put it in and boot that machine and since you won't have an operating system on the internal hard drive it will boot from the cd.

I know that probably created more questions than it answered but it gives you some resources. When/if you need more help post or email me at s.lepine(at)highcamp(dot)ca.

Good luck,
Thanks.  That post actually left me with only 1 new question, so it seems I know more about computers than you assumed :P.  It can be easily answered with Google though, but I'll come back if I'm still confused.

> **Duck2006 said:**
> You may have to format your drive, with gparted live cd, and then flash your BOIS to get rid of all trace of vista from the system
That sounds like exactly what I want to do.  If I were to do that, I assume I would format first then install Ubuntu, correct?  Then, about the BOIS, how would I access it, and how would I go about using that to get rid of Vista?

Also, is the GParted Live CD part of the Ubuntu Live CD (I've read that it is, probably on this thread, I have a very short-term memory :P) or is it something I would have to burn to a disc separately?  I have no discs capable of having ISOs being burnt into them, so hopefully the former.

---

### Post by Duck2006 on 2007-08-21
This site has the gparted live cd

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Then you partition the drive set up

20Gb for /
1Gb for the swap partition
and the rest for home

that way if you ever have to reinstall ubuntu you will still have your home partition with all your files in it.

The flashing the BOIS i will have to look it up and get back to you

---

### Post by Paul820 on 2007-08-21
> **Kosimo said:**
> Your Laptop have Turion64 chip and you can install Ubuntu 64bit edition. But I strongly recommend to use the 32 bit. Just for compatibility reasons.

And what compatibility reasons would they be? I have an Acer with a turion64 using ubuntu 64bit and there is no difference. Only trouble was flash but kilz wrote a script for that that installs it in 30 seconds. 

@op, if you choose the 64bit ubuntu and you have any problems i suggest you post in the  'x86 64-bit Users' section of the forum. Any problems you have will be sorted out there.

I don't know where people are getting the idea about 64bit being so bad but it's all FUD.

---

### Post by Duck2006 on 2007-08-21
This may help to flash your BOIS

[http://ubuntuforums.org/showthread.php?t=329189&highlight=how+to+flash+BOIS](http://ubuntuforums.org/showthread.php?t=329189&highlight=how+to+flash+BOIS)

---

### Post by str1fe on 2007-08-21
I appreciate the support guys.  I'll try the stuff everybody mentioned once my Ubuntu discs come in, then I'll post back here if I have more questions.

---

### Post by Brightbelt on 2007-08-21
I would take a look at this link:

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia) 

See if your Nvidia card is listed for compatibility etc. It may save you some time and/or at least it may give you some idea of what to expect.

Good Luck,...Frank B.

PS Not to discount the guys who have had smooth experiences, but I tried a 64-bit install of Ubuntu for about a day,.....then I gratefully switched back to 32-bit. Just my experience ;)

---

