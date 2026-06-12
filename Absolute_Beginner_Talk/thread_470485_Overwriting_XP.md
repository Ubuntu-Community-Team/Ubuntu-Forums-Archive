---
title: "Overwriting XP"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Nessa on 2007-06-11
I've been on this site, reading up on everything I can. I have an amd sempron based computer with an asrock motherboard that's at least 2 years old with a regular 2200 video card. It has XP sp2 installed. It has crashed twice in the past few months and had to have the OS reinstalled by the store I got it from. I don't wanna go through that again and I'm bored with windows. I don't have the cd's that came with it so I'm guessing that I have to search and download for linux drivers.

The hard drive has 2 partitions. 20GB for the windows and programs; 20GB for all the important files (pictures/music/documents). The next time it crashes I want to install ubuntu on the partition that has windows. How do I go about that? I already got the free cd's from canonical. I also have an external usb 2.0 80GB drive where I've backed everything up as well. Do I need to repartition the hard drive? Will ubuntu recognize my external drive? What (programs) exactly is included in the cd?

I would also like to know the linux counterpart for these programs if they aren't compatible with the OS. I know there Open Office that I can use for general documentation needs. It says it's free...where do I get it? 

The other software and hardware that I use are: Photoshop CS3, utorrent, Sony Ericsson Suite (for my cellphone w810i, but if it can read usb fine then I don't need this), Kodak Easyshare (for my digital camera), AVG (or any free antivirus), Instant Messengers (Yahoo, MSN, mirc, etc.), Brother Printer (scanner, card reader, copier), generic webcam and headset/speakers. Right now it's connected to a broadband connection but I'll be getting a linksys wireless broadband router soon. The computer will stay hardwired to the router though. 

I appreciate you guys taking the time to read this and thank you in advance for helping me out. Wish me luck! :)

---

### Post by Outrunner on 2007-06-11
My advice is to try the LiveCD(the one you got from Canonical). You simply have to go into your BIOS(there should be a prompt at startup, if there isn't try a few keys like delete f1, f2 f12 until you get it right). Then change the boot order so that it boots from your CD drive instead of your hard drive. Then accept the changes, insert your Ubuntu CD and you should be able to start up the Live session. There you can see if everything works

By the way, OpenOffice is included on the LiveCD, so you'll be able to test it out.

---

### Post by Nessa on 2007-06-11
Thanks! I will try that out. :)

Any ideas on how I can get it to install on the first partition and overwrite everything instead of having to create a new one?

---

### Post by Shazaam on 2007-06-11
It should ask you that while you are installing. Make sure you don't point the installer at your external drive.

Here is a good page to look at- [http://ubuntuforums.org/showthread.php?t=33183](http://ubuntuforums.org/showthread.php?t=33183)

Ubuntu will work out of the box but if you want to run 3D apps you will have to install drivers for your video card. Dont get discouraged, there is plenty of info on this site. Same for wifi.
Brother printer drivers for when you take the plunge (write down the url)...

[http://solutions.brother.com/linux/en_us/](http://solutions.brother.com/linux/en_us/)

Antivirus? You only need that if you are forwarding any emails to Windows users:D Clamav, AVG, F-Prot and Avast have Linux programs (there may be others). There is Gaim for instant messaging. Since you are hard wiring the router to your pc (ethernet?) make sure the router has NAT set up on it.
The thing to remember is Linux is NOT Windows. But most things are similar with a DIFFERENT way to do it. If you keep this in mind you will be ok. Most of all if you have any questions feel free to come back and ask for help.

---

### Post by ugm6hr on 2007-06-11
> **Nessa said:**
> Thanks! I will try that out. :)

Any ideas on how I can get it to install on the first partition and overwrite everything instead of having to create a new one?

Boot from the Ubuntu7.04 LiveCD with your external USB HD disconnected (for safety).  Open GParted (GNOME Partition Manager in the menu) and select your internal HD (probably hda - possibly sda - but sda is often external USB).  Then delete your XP partition (it should be obvious which it is).  Apply changes, then exit GParted.

Then run the Ubuntu installer (from LiveCD) - select the "Guided - largest continuous free space" option - and it should create a "/" and "swap" (don't worry if you don't know what this means - the Guided option removes the need to understand) partition automatically for you in the space you just created by deleting XP partition.

PS: This may not be correct for previous Ubuntu versions.

PPS: If your second "files" partition is NTFS - you will need ntfs-3g installed to write to it after installing - dead easy to do after you've successfully installed.

---

### Post by Nessa on 2007-06-11
Yes, it's NTFS. The external usb drive is like that as well...

---

### Post by sailor2001 on 2007-06-11
If you intend to trash windows, you can install ubuntu from the live disk with an option to use the entire hard drive... There are thousands of programs for linux so you're pretty well covered for any program you want.  When I install ubuntu on a box,  the first thing I do is go into synaptics (system/administration/ and tick all the repositories (settings).....reload and then go to add/remove and tick what ever makes your heart happy. Finally I'll go to Automatix2 (web site) and download anything I'm missing..a favorite thing of mine is in synaptics to tick KDE so I have the best of 2 worlds... Beryl is also in synaptics, but best if you have high RAM and a good graffic card for that.

---

### Post by sailor2001 on 2007-06-11
[http://www.linuxalt.com/](http://www.linuxalt.com/)    a good listing for linux programs. best to bookmark this... many, many of the programs are already in synaptics as a pkg. download

---

### Post by ugm6hr on 2007-06-11
> **Nessa said:**
> Yes, it's NTFS. The external usb drive is like that as well...

Don't worry - it's pretty easy to install full read/write NTFS support (in Feisty) after installing:
In Synaptic - install ntfs-3g and ntfs-config, reboot, then Applications -> System -> NTFS Configuration Tool. Follow the instructions and voila.

Ubuntu will read both drives without that as default.  If you're planning on dropping Windows, it would make sense to try and change the formats of both drives in the long run (maybe back one drive onto the other, then reformat etc).

---

### Post by Nessa on 2007-06-11
Dropping windows...yes, that's exactly what I want to do. 

So I back up everything on the external usb drive and then use the live cd and choose the option to use the whole hard drive? Do I plug in the usb drive during install? Do I leave my other devices plugged in?

Is it ok to put the drivers on the usb drive instead of burning them onto a cd?

Thanks again! :D

---

### Post by ugm6hr on 2007-06-11
> **Nessa said:**
> Dropping windows...yes, that's exactly what I want to do. 

So I back up everything on the external usb drive and then use the live cd and choose the option to use the whole hard drive? Do I plug in the usb drive during install? Do I leave my other devices plugged in?

Is it ok to put the drivers on the usb drive instead of burning them onto a cd?

Thanks again! :D

It will be less hassle to unplug all usb devices until after the install.

As for drivers.... what drivers?  If your hardware is older than Feisty (which at 2 years is true), then you shouldn't need any drivers (they are all on the Ubuntu disc).

---

### Post by Nessa on 2007-06-11
Oh cool! I didn't know that. Thanks!

I double-checked the video card because I wasn't sure what it was. It's an Nvidia GeForce FX5200. Not sure if that would matter.

If running the live cd works fine, does that mean I shouldn't have (or get only minimal) problems installing?

What format should be used for the hard drive?

---

### Post by ugm6hr on 2007-06-11
Basically - if the LiveCD works, it will be dead easy to install - it will just work.  

If it doesn't then it will probably still work - but there is no way to know until trying to install (with the AlternateCD).

I would actually recommend you not format the drive at all.  It sounds like you're now planning on using the whole HD for Ubuntu, so it will be easiest just to use the "Guided" install to use the whole drive - it will reformat the drive and create the necessary partitions for you (one ext3 and one linux swap).  As for whether a single large partition is best - it's personal preference (the same as when you chose 2 partitions with Windows).

---

### Post by notwen on 2007-06-11
Try & run the LiveCD for your everday use(surfing the web, general word processing, etc) and see if you run into any bumps along the way.  This time is also useful to help you learn where everything is in Ubuntu, like Control Panel, Session, Add/Remove Programs(or Synaptic, both are similar), Printers, Desktop Settings, things of that nature.  Once you're comfortable enough using th LiveCD, you should give the install a whirl.  Ubuntu comes w/ a small learning curve, but as long as you're patient and don't mind learning new things about your new and much more secure and stable OS, you shouldn't have any issues. Good Luck.  

FYI, the forums are your friends, put it to use.  =]

---

### Post by Nessa on 2007-06-15
So internet explorer crashed yet again. I have some time on my hands so I popped the cd in and booted into the 3rd option. Forgot exactly what it said...

Oh my god, I love it!!!

Right now I'm on firefox and logged into yahoo using Gaim. Does it have an option to log into invisible mode?

I opened up Rythmbox but all my music files are mp3. Can't play them right? What else should I try?

(Woohoo online!)

---

### Post by Nessa on 2007-06-16
Is everything on the Live CD going to be available in the actual install?

---

### Post by ugm6hr on 2007-06-16
> **Nessa said:**
> Is everything on the Live CD going to be available in the actual install?

Essentially - Yes.

I don't use rhythmbox - it doesn't seem to work on my system properly - but I thoought it does play mp3's.  There are lots of other options though.

---

### Post by arron on 2007-06-16
For linux drivers, most will run off the base install.  The only time you will have a little more complication is really new hardware or laptops.  As you explained your hardware, you shouldn't need any drivers.  For the install, if everything is backed up on your usb hard drive, I wouldn't connect it just in case.

Ubuntu has torrent programs, open office and a full array of other programs and support.  For photo shop I would recommend Gimp.  It is very powerful, most advanced users say you can do about anything that you can in photoshop, but professionals say it does have some limits.  I use gimp myself and love it.

Play with the CD some, that is when you boot right off the CD.  If you like it, during the install you can chose the partition and stuff.  Im now almost a year with no windows boot and happy!

---

### Post by Nessa on 2007-06-16
Right now, the internal drive has 2 partitions. 20GB for the files and 20GB for XP. Ubuntu needs 3 to install right?

---

### Post by logos34 on 2007-06-16
> Ubuntu needs 3 to install right?

no, just two -- / (root) and /swap

---

### Post by arron on 2007-06-16
nessa: you got a pm.

---

### Post by markharding557 on 2007-06-17
> **Nessa said:**
> So internet explorer crashed yet again. I have some time on my hands so I popped the cd in and booted into the 3rd option. Forgot exactly what it said...

Oh my god, I love it!!!

Right now I'm on firefox and logged into yahoo using Gaim. Does it have an option to log into invisible mode?

I opened up Rythmbox but all my music files are mp3. Can't play them right? What else should I try?

(Woohoo online!)
when you have installed ubuntu on your hd install automatix from[http://www.getautomatix.com/]("http://www.getautomatix.com/")
this program can install codecs for mp3,video,java,flash and a lot of other stuff

---

### Post by Nessa on 2007-06-17
I didn't get any new messages arron.

Thanks for the link mark. :D

The swap partition is twice my ram right? If I give it more than that, will that help any or it doesn't matter? The root is the main partition for the OS right?

So... 20GB for the files will be kept. Let's say 18GB for the root and 2GB for the swap... Will that be fine?

---

### Post by arron on 2007-06-17
nessa : you got a pm now.....  logos34 sorry i sent it to the wrong person.

---

